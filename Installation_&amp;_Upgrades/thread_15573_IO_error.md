---
title: "I/O error?"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by PaNtHeR on 2005-02-15
Hello to the forum.

I'm pretty new to linux and, already  :-) , I need some help. 
While instaling Ubuntu everything goes fine until writing filesystem to hard disk. I get:

Creating ext3 filesystem for / in partition #1 of SCSI (0,1,0)(sdb) 

and stops at 100%.  When I press alt+f4 I get screen full of:

Feb 15 17:16:09 (none) syslog warn klogd: lost page write due to I/O error on sdb
Feb 15 17:16:09 (none) syslog err klogd: Buffer I/O error on device sdb, logical block 16

Now I understand there must be something wrong with my Harddisk, which is btw. attached on SATA channel. I have another drive with Wind(bl)ows and alot of data so I can't try with that one.  Weird thing is that this 'faulty' harddisk works OK in windows, and I can format it and copy data, everithing works fine. 
I even used this disk as primary before buying that another one only month ago - so I think the disk is not faulty. 

And one more thing but I don't think it's important: this problematic disk is actually PATA drive with IDE-to-SATA adapter on. I haven't tried to connect it to IDE because I have only one IDE channel onboard and two CDROM drives connected to it, and simply don't think that might be problem.

Does anyone have a clue what's going on because I'm freakin' out already.

And one more thing - is there any sure way to check if my drive is OK, 'cause in Windows everything looks fine?

Thanks.

---

