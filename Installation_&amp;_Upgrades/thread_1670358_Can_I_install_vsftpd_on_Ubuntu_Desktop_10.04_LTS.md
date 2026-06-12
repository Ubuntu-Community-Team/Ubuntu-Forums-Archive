---
title: "Can I install vsftpd on Ubuntu Desktop 10.04 LTS?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by xavierlinw on 2011-01-18
I just installed Ubuntu Desktop 10.04 LTD on my computer, and I wanted to install vsftpd on it, but I got an error message.

I am wondering if I can install any server software onto Ubuntu Desktop  Edition, like apache2, vsftpd, postfix, and openssh-server. Do I must  use the Server Edition to do so?

I am sorry. I am just a new guy to Ubuntu.


Code:

root@Acer1410Server:/etc# apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vsftpd
root@Acer1410Server:/etc# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2
root@Acer1410Server:/etc# apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
root@Acer1410Server:/etc#

---

