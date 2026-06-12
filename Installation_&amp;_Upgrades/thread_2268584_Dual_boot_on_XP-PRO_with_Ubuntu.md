---
title: "Dual boot on XP-PRO with Ubuntu"
date: 2015-03-09
forum: Installation &amp; Upgrades
---

### Post by eightbits2010 on 2015-03-09
Yesterday I installed Linux Mint xfce on my XP-PRO laptop. I am so used to using Ubuntu (12.04) on my meerkat PC I would
rather have Ubuntu installed.
Question: Can the Linux Mint be removed without destroying the XP-PRO and then install Ubuntu as a dual boot ?
I have some programs that will run only under Windows, so I have to keep that for now. I am hoping that can be done and some guidance on accomplishing that.

---

### Post by yancek on 2015-03-09
> Can the Linux Mint be removed without destroying the XP-PRO and then install Ubuntu as a dual boot ?

You don't need to remove Mint.  During the installation, you need to use the Something Else option so that you can select the partition on which you have Mint installed to install Ubuntu and make sure you select to Format that partition during the installation.  You should see the xp partition(s) as they will show as ntfs filesystem types.  Just don't install to those partitions.  The link below has a very detailed tutorial on installing Ubuntu and specifically a section on Dual/Multi booting which would be helpful to read.

 
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

If you could post the output of:  sudo fdisk -l someone might be able to be more specific about partitions.

---

### Post by Bucky Ball on 2015-03-10
If you just want the Ubuntu desktop environment, why not install Unity, log out, choose it from the sessions menu, login?

---

