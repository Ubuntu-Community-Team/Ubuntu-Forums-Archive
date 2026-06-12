---
title: "php5-mysql unmet dependencies"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by sderrick on 2009-11-26
trying to install php5-mysql in 9.10 I get the following error

scott@scotts-laptop:~$ sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-mysql: Depends: php5-common (= 5.2.10.dfsg.1-2ubuntu6.1) but 5.2.10.dfsg.1-2ubuntu6.3 is to be installed
E: Broken packages

---

### Post by Zebu on 2009-11-29
Hi,

have you tried:

```
sudo aptitude install php5-mysql
```Just answer Y to all questions, it should work.


Regards,
ZB

---

### Post by phillw on 2009-11-29
or... you could be *really* lazy and follow this one ;)  [http://www.unixmen.com/linux-tutorials/570-install-lamp-with-1-command-in-ubuntu-910](http://www.unixmen.com/linux-tutorials/570-install-lamp-with-1-command-in-ubuntu-910)

lol,

Regards,

Phill.

---

### Post by sderrick on 2009-11-29
> **Zebu said:**
> Hi,

have you tried:

```
sudo aptitude install php5-mysql
```Just answer Y to all questions, it should work.
ZB

thanks that did the trick,  it downgraded the offending module so al is happy.

Scott

---

