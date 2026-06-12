---
title: "adapt installation cd with extra driver"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by tomcarly on 2010-03-22
Hi,

i'd like to add an extra driver to my installation cd so that it hopefully detects my hard disks. What's the procedure for doing this?

Thanks,

Tom

---

### Post by gordintoronto on 2010-03-22
That's not the way to do it.

What is unusual about your hard disks? What installation CD do you have, and what happens when you boot from it?

---

### Post by tomcarly on 2010-03-23
The problem is not the hard disks but the raid controller. It is not supported by Ubuntu 8.04, 9.10 and 10.04 beta. It is supported by CentOS and it needs the mpt2sas driver. 
During the installation it does not detect the hard disks due to this. It is also reported here by someone else: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361)
On this page, someone says he made it work by changing the initrd.gz file but without further explanation.

---

### Post by jfabrizio on 2010-03-29
I have the same problem...

---

