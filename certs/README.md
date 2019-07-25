# Generating Self Signed Certs for Testing

Steps stolen from [linux.com](https://www.linux.com/learn/creating-self-signed-ssl-certificates-apache-linux):

##### Check for SSL

```bash
sudo a2enmod ssl
```

##### Generate the CSR

```bash
sudo openssl req -new > new.ssl.csr

Generating a 1024 bit RSA private key
................++++++
........................++++++
writing new private key to 'privkey.pem'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:Enter Code Here
State or Province Name (full name) [Some-State]:Enter State Here
Locality Name (eg, city) []:Enter City Here
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Enter Company Name
Organizational Unit Name (eg, section) []:Org Unit (if you have one)
Common Name (eg, YOUR name) []:First and Last Name
Email Address []:Work Email

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:Leave Blank
An optional company name []:Optional
```


##### Generate the Certificate

```bash
sudo openssl rsa -in privkey.pem -out new.ssl.key
sudo openssl x509 -in new.ssl.csr -out new.ssl.cert -req -signkey new.ssl.key -days NNN
sudo cp new.cert.cert ./certs/sslCert.pem
sudo cp new.cert.key ./certs/sslKey.pem
```