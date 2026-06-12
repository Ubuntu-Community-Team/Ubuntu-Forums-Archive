---
title: "mod-security error"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by baseej313 on 2008-09-01
Hi everyone.
i am new in ubuntu.
I am trying to install mod-security with apache2 but getting the error again and again during installation.
The error is : "E: Couldn't find package mod-security".
I am using the command for mod-security installatin is
$sudo apt-get install mod-security
Second question is how can we manually instally any package i.e mod-security.
Your help will be much appreciated.

Regards
Baseej

---

### Post by Partyboi2 on 2008-09-01
Looks like that package is no longer in the ubuntu repo's. You could try and download the package from [[COLOR=Blue]here[/COLOR]]("http://etc.inittab.org/%7Eagi/debian/libapache-mod-security2/"). To install it after you have downloaded it double click on the downloaded package. Or from a terminal change directory to where the download package is eg if it is on your Desktop
```
 cd ~/Desktop
```and
```
sudo dpkg -i <package>
```*Change <package> to name of package

---

### Post by baseej313 on 2008-09-01
Hi there,
Thanks for quick reply.
I did according to your instructions but getting the following error now.

dpkg-split: error reading modsecurity-apache_2.5.5: Is a directory
dpkg: error processing modsecurity-apache_2.5.5 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 modsecurity-apache_2.5.5

Regards

---

### Post by baseej313 on 2008-09-02
Hi everyone.
i am new in ubuntu.
I am trying to install mod-security with apache2 but getting the error during installation.
The error is : "E: Couldn't find package mod-security".
I am using the command for mod-security installatin is
$sudo apt-get install mod-security
After downloding the packag i also tried like that
sudo dpkg -i mod-security
this wayt it gives this error
dpkg-split: error reading modsecurity-apache_2.5.5: Is a directory
dpkg: error processing modsecurity-apache_2.5.5 (--install):
subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
modsecurity-apache_2.5.5
Your help will be much appreciated.
Regards

---

### Post by overdrank on 2008-09-02
Hi and please do not create multiple threads on the same issue. You can bump your post if you are not getting any response. Once a day is a good idea.
Merged threads and bump to the top. :)

---

