---
title: "MYSQL installation"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by mnuthan on 2010-01-18
Hi,
I am new to Ubuntu, and installed Ubuntu9.10 3 days back. I am trying to install MYSQL, getting following error.  Any idea on how to resolve this problem 

> 
nuthan@nuthan-laptop:~$ sudo apt-get install mysql-server mysql-client
[sudo] password for nuthan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-client-5.1 mysql-server-5.1
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-client mysql-client-5.1 mysql-server mysql-server-5.1
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,313kB/15.5MB of archives.
After this operation, 36.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main mysql-server-5.1 5.1.37-1ubuntu5 [7,186kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main mysql-client 5.1.37-1ubuntu5 [63.7kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main mysql-server 5.1.37-1ubuntu5 [63.9kB]
Fetched 7,313kB in 2min 32s (47.8kB/s)                                         
Preconfiguring packages ...
(Reading database ... 148724 files and directories currently installed.)
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.37-1ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.1_5.1.37-1ubuntu5_i386.deb (--unpack):
 trying to overwrite '/usr/bin/mysql_client_test', which is also in package mysql-bench 0:5.0.89-0.glibc23
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package mysql-server-5.1.
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.37-1ubuntu5_i386.deb) ...
egrep: /etc/mysql/: No such file or directory
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.1.37-1ubuntu5_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.37-1ubuntu5_all.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.1_5.1.37-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nuthan@nuthan-laptop:~$ 



---

### Post by wojox on 2010-01-18
Try:

```
sudo apt-get -f install
```

---

### Post by phillw on 2010-01-18
Hi and welcome to the forums,

I'm surmising you're wanting a LAMP installation on your system ?

If so, using tasksel & Synaptics is real piece of cake.

Having spent time helping with broken installs in the past, you might want to pop over to --> [http://www.vpolink.com/threads/493-LAMP-Important](http://www.vpolink.com/threads/493-LAMP-Important)

It is that easy, honest !!!

Please, don't use the long method - it's a pain & has been replaced as of 9.10

Regards,

Phill.

---

### Post by mnuthan on 2010-01-18
Hi Thanks for your reply.
I am getting following error while using tasksel

> 
nuthan@nuthan-laptop:~$ sudo tasksel
tasksel: aptitude failed (100)
nuthan@nuthan-laptop:~$ 



---

### Post by phillw on 2010-01-18
Hi, do you have another apt programme running ?

E.g.  Synaptic Package Manager, Update Manager, Ubuntu Sortware Center ?

You can only have one apt based programme running at one.

Phill.

---

### Post by phillw on 2010-01-18
Also, picked up from another thread - try this to reset the apt system - I've used it before and can vouch for it.

```
 sudo dpkg --configure -a
```

It makes dpkg, which apt is a part of the suite of, reset itself if it has gotten a bit confused -- I have days like that !!

Regards,

Phill.

---

### Post by mnuthan on 2010-01-20
I am running only one program. infact I have tried same by restarting the server. Still getting same error,

and  
 sudo dpkg --configure -aresutl:

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mysql-client
 mysql-server-5.1
 mysql-server


do i need clean these errors before reinstalling ..? if yes how to clean them..?

---

