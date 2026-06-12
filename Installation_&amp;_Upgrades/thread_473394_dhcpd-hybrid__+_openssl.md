---
title: "dhcpd-hybrid  + openssl"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by anxean on 2007-06-14
openssl + fiesty

[http://www.openssl.org/docs/HOWTO/](http://www.openssl.org/docs/HOWTO/)

asdf@asdf-desktop:~$ openssl s_serverError opening server certificate private key file server.pem
5911:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('server.pem','r')
5911:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load server certificate private key file

For some reason openssl server wont read the keyfile

Ill show you what i did so far.


**RSA KEY**
asdf@asdf-desktop:~$   openssl genrsa -des3 -out privkey.pem 2048
Generating RSA private key, 2048 bit long modulus
..................................................+++
.................................+++
e is 65537 (0x10001)
Enter pass phrase for privkey.pem:
Verifying - Enter pass phrase for privkey.pem:


**DSA KEY**
 openssl dsaparam -out dsaparam.pem 2048
Generating DSA parameters, 2048 bit long prime
This could take some time
.........+..............+....+..+.+........+...............+...+..+..............+..........................+.+.+.................+.......+.......+.....+..+....+++++++++++++++++++++++++++++++++++++++++++++++++++*
.+.+........+.............+..+...+.+..............+.+..+............+....+...................+.........................+.+.+.....+.................................+.............+++++++++++++++++++++++++++++++++++++++++++++++++++*
asdf@asdf-desktop:~$ 

asdf@asdf-desktop:~$   openssl gendsa -des3 -out privkey.pem dsaparam.pem
Generating DSA key, 2048 bits
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
asdf@asdf-desktop:~$ 

**Then** i make the request

asdf@asdf-desktop:~$   openssl req -new -key privkey.pem -out cert.csr
Enter pass phrase for privkey.pem:
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:asdf
string is too long, it needs to be less than  2 bytes long
Country Name (2 letter code) [AU]:as 
State or Province Name (full name) [Some-State]:as
Locality Name (eg, city) []:as
Organization Name (eg, company) [Internet Widgits Pty Ltd]:as
Organizational Unit Name (eg, section) []:as
Common Name (eg, YOUR name) []:as
Email Address []:as

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:wahtachallenge
An optional company name []:
asdf@asdf-desktop:~$ 

**Now** everything should work fine, according to [http://www.openssl.org/docs/HOWTO/](http://www.openssl.org/docs/HOWTO/) bu instead i receive his message:

asdf@asdf-desktop:~$ openssl s_serverError opening server certificate private key file server.pem
5911:error:02001002:system library:fopen:No such file or directory:bss_file.c:352:fopen('server.pem','r')
5911:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:354:
unable to load server certificate private key file

**Oh man** nothing more irritating then that,  Anyone have any ideas??

-anxean

---

