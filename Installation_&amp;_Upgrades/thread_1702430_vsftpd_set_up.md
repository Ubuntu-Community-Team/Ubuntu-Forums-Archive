---
title: "vsftpd set up"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-07
I am attempting to set up a FTP server.  I am going with vsftpd. I followed the steps in the documentation for Ubuntu 10.10

[http://help.ubuntu.com/10.10/serverguide/C/ftp-server.html](http://help.ubuntu.com/10.10/serverguide/C/ftp-server.html)

I installed vsftpd  and made one change to the vsftpd.conf file.  I uncommented the chroot_local_user=yes so that my users only have access to their home directories.

I then restarted vsftpd.

Now going over the another machine I attempted to access the server using filezilla.  I configured the network connection using the wizard and tested it so I know filezilla is configured correctly. 

I am attempting to access the site by login into the website  so I am using the following parameters

HOST:  [www.website.com]("http://www.website.com")
USERNAME:  USER    (this is the user name of the ubuntu system who's home page has the website)
Password:  *****
port: 20

When I attempt to connect I get the following error in filezilla. 

Status:    Resolving address of [www.website.com]("http://www.website.com")
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

