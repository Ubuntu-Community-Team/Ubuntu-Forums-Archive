---
title: "System program problem detected"
date: 2018-04-12
forum: Installation &amp; Upgrades
---

### Post by cam17 on 2018-04-12
All of my Ubuntu desktop have this error usually after installation. I know how to remove the file from /var/crash directory to stop the error but I would like to know what the cause is as this error seems to appear after a new installation or command line reinstallation.

---

### Post by cruzer001 on 2018-04-12
It's a fairly common occurrence and usually will not reoccur.  

/var/log/apport.log will give the details.

---

### Post by cam17 on 2018-04-13
From what I see the problem goes back to 2015. This problem still occurs when using 16.04.4 ? Is there a general reason for this error message?

---

### Post by cruzer001 on 2018-04-13
> This problem still occurs when using 16.04.4 ?

Its not a problem, its a crash report and its still going on in 18.04.

> Is there a general reason for this error message?

Its Apport doing whats its suppose to do, but crash reporting is suppose to be turned off in 16.04.

> Apport collects potentially sensitive data, such as core dumps, stack traces, and log files. They can contain passwords, credit card numbers, serial numbers, and other private material. 

[https://wiki.ubuntu.com/Apport#Why_is_apport_disabled_by_default.3F](https://wiki.ubuntu.com/Apport#Why_is_apport_disabled_by_default.3F)

---

