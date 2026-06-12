---
title: "Error 15: File Not Found! Upgrading from 9.04 to 9.10."
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by Strato9 on 2015-05-11
Hi,

I am having an issue after upgrading from 9.04 to 9.10.  I originally started at 8.10 and was doing the incremental upgrades.  I received the 'Error 15: File not Found!' error when restarting after upgrading to 9.10.

I tried to use Boot Repair Disk, but it did not fix the problem.  I am posting a link to the output below.

paste.ubuntu.com/11084832/

Thanks you in advance for any help!

J

---

### Post by yancek on 2015-05-11
If you go to the Ubuntu site below to the section "End of Life" you will see that your newly installed Ubuntu 9.10 has not had any support for over four years.  If I remember correctly, Ubuntu switched from Grub Legacy in 9.04 to Grub2 in 9.10 which has totally different boot files.   You might check the site for current Ubuntu releases.  Depending upon the age of your hardware, you may be better off with a lighter version of Ubuntu or some other lighter Linux.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by yancek on 2015-05-11
If you go to the Ubuntu site below to the section "End of Life" you will see that your newly installed Ubuntu 9.10 has not had any support for over four years.  If I remember correctly, Ubuntu switched from Grub Legacy in 9.04 to Grub2 in 9.10 which has totally different boot files.   You might check the site for current Ubuntu releases.  Depending upon the age of your hardware, you may be better off with a lighter version of Ubuntu or some other lighter Linux.

 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Strato9 on 2015-05-12
I am trying to move up to a current supported version.  The server was pre-installed with 8.10.  I tried to go through the tutorial below, but it did not fix the error.  

[http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu](http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu)

I'm able to copy the data off the server if I have to as a last resort.  Is there any saving this upgrade?

---

### Post by dino99 on 2015-05-12
Dont try to upgrade, the actual supported flavours are way too different nowadays. Do a fresh installation.
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

