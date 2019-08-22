# Create Self signed certificate

## 1 - Google doc

See [https://cloud.google.com/load-balancing/docs/ssl-certificates#gettingakeyandcertificate](https://cloud.google.com/load-balancing/docs/ssl-certificates#gettingakeyandcertificate)


## 2 - Commands

```bash
# create working directory
mkdir ssl_cert
cd ssl_cert


# creates private key
# file example.key
$ openssl genrsa -out example.key 2048
Generating RSA private key, 2048 bit long modulus (2 primes)
..........+++++
...................................................................+++++
e is 65537 (0x010001)

# creates certificate signing request
# see https://en.wikipedia.org/wiki/Certificate_signing_request
# file example.csr
$ openssl req -new -key example.key -out example.csr
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:FR
State or Province Name (full name) [Some-State]:France
Locality Name (eg, city) []:Paris
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Home
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:oscar6echo.net
Email Address []:olivier.borderies@gmail.com

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:

# creates self signed certificate
# file example.crt
openssl x509 -req -days 365 -in example.csr -signkey example.key -out example.crt
Signature ok
subject=C = FR, ST = France, L = Paris, O = Home, CN = oscar6echo.net, emailAddress = olivier.borderies@gmail.com
Getting Private key
```

To obtain a valid certificate from a certificate authority, e.g. Comodo, RapidSSL, Thawte, Sectigo, DigiCert, Symantec, etc.



