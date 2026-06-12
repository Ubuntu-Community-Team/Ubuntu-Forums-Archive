---
title: "dual boot ubuntu and windows vista"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2008-04-23
****I would like to install UBUNTU 7.10 (I have the i386 version) on my laptop with WIndows Vista installed. Do I have any problem because of the hard-drive format what is in windoes vista NTFS and the version of UBUNTU 7.10 I have is a 32byte version? /B]

---

### Post by undecidable on 2008-04-23
Windows doesn't need to use the whole disk, and the Ubuntu install CD can reduce the amount of space Windows uses, and put Ubuntu in the newly freed space.  

during installation Ubuntu will ask you if you want to "resize your hard disk" and use the newly freed space to install Ubuntu - say yes.  

Please read:  [http://www.ubuntu.com/node/691](http://www.ubuntu.com/node/691)

A detailed walkthrough of the procedure is at:
  [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by chrisdugdale on 2008-04-23
Wait a day! The Ubuntu Hardy Heron 8.4 LTS will be available for download tomorrow. It  has a new thing called Wubi so you can install it like a Windows program and not change your hard disk partitions. The beta seems real good and it sounds like Wubi works well. Much less painful and you take less risks too.

---

### Post by drumanart on 2008-04-23
Thanks for the advice, I'll wait up  to tomorrow and I'll use Ubuntu Hardy Heron 8.4 LTS.

---

### Post by Lantesh on 2008-04-23
> **chrisdugdale said:**
> It  has a new thing called Wubi so you can install it like a Windows program and not change your hard disk partitions.

Wubi seems to me to be a band aid solution for those who are not smart enough or too scared to actually partition a hard drive.  The main advantages of Linux over Windows are security, speed, and stability, all of which are compromised by running Linux virtually within Windows.  If you want to go virtual consider running Windows with Linux via Virtualbox or wmware.  Personally I utilize a true dual boot setup, although I can't remember the last time I actually even bothered to boot into Windows.

---

### Post by Pumalite on 2008-04-23
If you decide to do a real dual booting, keep in mind that you have to allocate space for Ubuntu with the Vista partitioner first. You cannot partition with the Ubuntu CD.

---

### Post by Lantesh on 2008-04-23
> **Pumalite said:**
> You cannot partition with the Ubuntu CD.

Umm yes you absolutely can.  I created all my partitions with the Ubuntu live CD.

---

