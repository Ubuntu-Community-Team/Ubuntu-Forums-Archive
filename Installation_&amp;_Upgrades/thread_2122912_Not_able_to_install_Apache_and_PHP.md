---
title: "Not able to install Apache and PHP"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by bipinvish on 2013-03-06
Hello Members,I am Bipin Vishwakarma not that sound in programming, but I am not able to install Apache2 and PHP in my Ubuntu 12.04.I run the command "sudo apt-get install apache2"  and got and error somthing like "E: Sub-process /usr/bin/dpkg returned an error code (1)"and after that I am getting something like that


----------------------------------------------------------------------------------------
bipin@bipin-VPCYB25AG:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,765 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libqtwebkit4:i386 (--configure):
 package libqtwebkit4:i386 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libqtwebkit4:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
bipin@bipin-VPCYB25AG:~$ 

-------------------------------------------------------------------------------------------
plz friends helpthanx in advance.

---

### Post by pierceTN on 2013-03-06
Hey there Bipinvish,

I have had different install problems with apache on a cent OS server that required recompiling php with the apache package.   


with ubuntu, first try:


> sudo apt-get purge apache2


then try:


> sudo apt-get install apache2


and see if that helps.


also, you will need to add a repository first, here is a link on how to do that. [http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/)


hope that helps,


-Pierce

---

### Post by cortman on 2013-03-06
Try

```
sudo dpkg --configure -a
```

and if that doesn't fix it, run

```
sudo rm -r /var/cache/apt/archives/*
sudo apt-get update
sudo apt-get install apache2
```

---

### Post by bipinvish on 2013-03-06
> **pierceTN said:**
> Hey there Bipinvish,

I have had different install problems with apache on a cent OS server that required recompiling php with the apache package.   


with ubuntu, first try:




then try:




and see if that helps.


also, you will need to add a repository first, here is a link on how to do that. [http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/adding-extra-repositories-on-ubuntu/)


hope that helps,


-Pierce


Again I am getting something like that
What is that "error code (1)"


root@bipin-VPCYB25AG:~# sudo apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5,765 kB of archives.
After this operation, 29.7 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 177409 files and directories currently installed.)
Removing apache2 ...
dpkg: error processing libqtwebkit4:i386 (--configure):
 package libqtwebkit4:i386 is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 libqtwebkit4:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bipin-VPCYB25AG:~#

---

### Post by pierceTN on 2013-03-06
Did you try adding the repository?

-
Pierce

---

### Post by bipinvish on 2013-03-07
I visited the link you give for adding repository. And as guided I go to the Source.list file, but I am not able to locate the mentioned DEB lines.
should I have to add those lines manually ?
And I have the 64-bit version of Ubuntu 12.04

---

