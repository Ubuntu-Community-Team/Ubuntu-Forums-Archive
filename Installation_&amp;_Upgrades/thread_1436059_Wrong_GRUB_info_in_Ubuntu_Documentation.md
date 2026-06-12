---
title: "Wrong GRUB info in Ubuntu Documentation"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by colourfullegume on 2010-03-22
I am a new Ubuntu user and have recently installed Ubuntu 9.10.  (I am familiar with Unix itself, and would classify myself as a basic user with some intermediate knowledge.)

As I would like to continue using Windows for the time-being via a dual boot, I looked up the starter documentation at this link: [https://help.ubuntu.com/9.10/switching/dualboot.html](https://help.ubuntu.com/9.10/switching/dualboot.html)

All went very well up to a point.  I have two hard drives and have installed Ubuntu on the secondary drive, hence no need to repartition the drive that holds Windows.  The dual booting worked fine, except that it defaults (after timeout) to boot up Ubuntu, and I wanted to default to Windows.

So I read this page: [https://help.ubuntu.com/9.10/switching/dualboot-custom.html#dualboot-custom-bootorder](https://help.ubuntu.com/9.10/switching/dualboot-custom.html#dualboot-custom-bootorder)

Unfortunately, after much time wasting, I realised that the documentation is wrong.  It is referring to GRUB instead of GRUB2 and the correct documentation is here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2).

I have sorted out my problem by editing /etc/default/grub and then running update-grub.

However, I would appreciate it if someone who is familiar with and has permission to edit the documentation could do so in order to save distress to other new users.

---

### Post by phillw on 2010-03-22
Hi and welcome to the forums,

I've had a quick look and it *should* have been updated, I have added to a bug report that it be updated. 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/437446?comments=all](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/437446?comments=all)

Thanks for reporting it.

Regards,

Phill.

---

### Post by colourfullegume on 2010-03-22
Thanks Phill.

---

