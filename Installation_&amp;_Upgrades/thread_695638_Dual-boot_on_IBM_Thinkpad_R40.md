---
title: "Dual-boot on IBM Thinkpad R40?"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by JEBB on 2008-02-13
Thinkpad R40, XP
I made a clone of my 40GB HD to an 80GB drive with Acronis True Image.  After exchanging the drives, the new one  worked fine.  

I want to put Ubuntu on that drive to create a dual boot system.  Is that possible using the Ubuntu CD or should I go back a step and partition the new drive and clone the original drive to one of those partitions or do I need to buy a program to change the partitions?  

Also, how do I boot from the Ubuntu CD?  

If I succeed in creating a dual boot system, how will I get the computer to boot in one or the other operating systems?  

Thanks.

---

### Post by jan quark on 2008-02-13
1
you have one OS on one partition and the other partition is blank right?
then when you install ubuntu and choose the option during the installation process " install on largest continuous free space" ubuntu will install on this blank partition
the grub loader will detect the OS which is already installed and you will have a boot option during the booting process, where you can choose between ubuntu and the other operating system

2

you can boot from the Ubuntu live CD
set in your bios the booting order for CD rom at the first place

3

you do not need an extra application to format and partition the drive
during the installation ubuntu will do it on its won using the application 
gparted

4

here are some useful links how to set up a dual boot system
and how to install ubuntu in general

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by JEBB on 2008-02-13
Thanks for your response.  

1.  Clarification- at this point in time there is only ONE partition on the hard drive.  Does that make any difference?

If the disk defragmenter shows relative position of files on the hard drive, they are one one end.  Any consequence to that?

2.  How can I see the BIOS file to change anything?  How do I start it?  Once there, how will I get out of it saving the changes and not putting in any others?

3.  Will Ubuntu start gparted itself?  Will that application actually create separate partitions?

4.  After I read the information on the links, I may have other questions.

---

