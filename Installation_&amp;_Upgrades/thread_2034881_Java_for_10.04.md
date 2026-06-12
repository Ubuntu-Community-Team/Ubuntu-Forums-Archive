---
title: "Java for 10.04"
date: 2012-07-29
forum: Installation &amp; Upgrades
---

### Post by flit07 on 2012-07-29
Hi,

I was trying to install java JRE by following this site
[https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](https://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

and a few others. Mozilla still has no java plugins.

Checked ~/.mozilla/plugins/libnpjp2.so, the link is pointing to where i've extracted the JRE.

Any clues?

Thanks.

---

### Post by Laiquendi on 2012-07-29
System long ago reached his EOL, maybe it's just incompatible?

---

### Post by flit07 on 2012-07-29
:(

---

### Post by tester100 on 2012-07-30
Hi

simple steps......

open terminal and write these cmds step by step

apt-get install python-software-properties

add-apt-repository ppa:webupd8team/java

apt-get update

apt-get install oracle-java7-installer

---

### Post by QIII on 2012-07-30
Start each of those commands with "sudo".

---

### Post by tester100 on 2012-07-30
> **QIII said:**
> Start each of those commands with "sudo".


just if you´re not logged in as root.........

if u login with root account , then no need for sudo...

---

### Post by Lyfang on 2012-07-30
> **tester100 said:**
> just if you´re not logged in as root.........

if u login with root account , then no need for sudo...
```
sudo su
```

---

### Post by yuvraj23 on 2012-07-30
Download open jdk 7 from software centre.. you will get the plugin :)

---

### Post by flit07 on 2012-07-30
got it! Thanks all and tester100.:P
Yea, I did ran with sudo previously.

---

### Post by QIII on 2012-07-30
> **tester100 said:**
> just if you´re not logged in as root.........

if u login with root account , then no need for sudo...

If you are actually logging in with an active root account, you are unwise.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

