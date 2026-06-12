---
title: "Since I upgraded to 12.04 from 11.10"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by DoctorVell on 2012-05-05
Since I did an upgrade from release 11.10 to 12.04 I get the following message after doing an update from the system updates.  I never encountered it all until then, before it worked perfectly and no problems.

Errors were encountered while processing: 
 ushare 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up ushare (1.1a-0ubuntu7) ... 
/var/lib/dpkg/info/ushare.config: 22: /etc/ushare.conf: GoFlex: not found 
dpkg: error processing ushare (--configure): 
 subprocess installed post-installation script returned error exit status 127 

What does it mean and how can I fix it?  :confused:

---

### Post by DoctorVell on 2012-05-05
NOTE: This also happens when I install a new program too.

---

### Post by dino99 on 2012-05-05
the comment says all : /etc/ushare.conf: GoFlex: not found 

i suppose you have used Goflex (from seagate) in the past, so it complaint about it because it cant find it.
if this storage is really gone then edit the conf file to comment out this goflex entry

sudo gedit /etc/ushare.conf

or modify your sharing settings.

---

### Post by grahammechanical on 2012-05-05
How did you install Ushare?

[http://manpages.ubuntu.com/manpages/natty/man1/ushare.1.html]("http://manpages.ubuntu.com/manpages/natty/man1/ushare.1.html")

It could be that the repository for Ushare is not yet set up for Precise but still for Oneiric.

Every time your software sources list is read you will get this error.

Regards.

---

### Post by DoctorVell on 2012-05-05
I am going to try that and hopefully it works.

---

### Post by DoctorVell on 2012-05-06
> **doctorvell said:**
> i am going to try that and hopefully it works.


works now thank-you all!

---

