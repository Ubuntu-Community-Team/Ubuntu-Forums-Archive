---
title: "Ftp set up does not work"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-08
I am attempting to set up a FTP server.  I am going with vsftpd. I followed the steps in the documentation for Ubuntu 10.10

[http://help.ubuntu.com/10.10/serverg...tp-server.html]("http://help.ubuntu.com/10.10/serverguide/C/ftp-server.html")

I installed vsftpd  and made one change to the vsftpd.conf file.  I  uncommented the chroot_local_user=yes so that my users only have access  to their home directories.

I then restarted vsftpd.

Now going over the another machine I attempted to access the server  using filezilla.  I configured the network connection using the wizard  and tested it so I know filezilla is configured correctly. 

I am attempting to access the site by login into the website  so I am using the following parameters

HOST:  [www.website.com]("http://www.website.com/")
USERNAME:  USER    (this is the user name of the ubuntu system who's home page has the website)
Password:  *****
port: 20

When I attempt to connect I get the following error in filezilla. 

Status:    Resolving address of [www.website.com]("http://www.website.com/")
Status:    Connecting to 100.202.18.14:20...
Status:    Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:    Could not connect to server
 


Does anyone know how I can test to see if vsftpd is installed correctly and running?

Any idea as to why I am getting this error?

Do I need to install another software package to get vsftpd work?

Do I need to turn any modules on?

Did I miss something during my setup?

Thanks,

Spindler

---

### Post by spindler on 2011-03-08
I have some new information....Although my problem has not changed.

I was able to test my router and found that the ftp requests are not being blocked.

I also used an online tool to test the ftp connection.

[http://www.g6ftpserver.com/en/ftptest](http://www.g6ftpserver.com/en/ftptest)

The results were the following:

** About to connect() to 100.24.180.110 port  21*
** Trying 100.24.180.110...  connected*
** Connected to  100.24.180.110 (100.24.180.110) port 21*
** FTP response reading failed*
** Closing connection #0*

I also tested using ssl explicit and ssl implicit to see any difference and I was able to see the following:

** About to connect() to 100.24.180.110 port  21*
** Trying **100.24.180.11**0...  connected*
** Connected to **100.24.180.110** (**100.24.180.110**) port 21*
** successfully set certificate verify  locations:*
** CAfile:  d:\www-bin\curl\curl-ca-bundle.crt*
[FONT=courier]CApath: none[/FONT]
** SSLv3, TLS handshake, Client hello  (1):*
[FONT=courier]Unknown  SSL protocol error in connection to 100.24.180.110:21 [/FONT]
** Closing connection #0*


These two statement tell me that I am able to contact the server...but not connect to it.

NOW,   I should mention that I am using a system user and password to test and access ftp.   I plan to use a virtual user eventually....once I get the ftp connection working.

Any ideas why the ftp request does not connect?

---

