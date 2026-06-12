---
title: "Can't boot or see Windows 7 partition after installing Ubuntu"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by WLbUdOa1 on 2013-11-02
I installed Ubuntu earlier today and I can't see Windows 7  partition in Gparted and don't get an option to boot Windows 7 at  restart.
  When I was installing Ubuntu, I chose "Something else" option and  partitioned about 100 GBs of "Unallocated space". It did not show  Windows 7 in those partitions at that time or right now.
  After googling and trying different things I still was not be able to fix anything.
  I tried running Boot Repair after booting from Live USB, but that did not help.

  This is the Boot Repair log file: [http://paste.ubuntu.com/6349990/](http://paste.ubuntu.com/6349990/)

  Based on what I can understand is Windows is not there anymore, however it did not show up even when I was installing Ubuntu. 

Can anyone please suggest what to do to recover Windows 7 or at least the files? Please help! Thanks in advance :)

---

### Post by fantab on 2013-11-02
I am afraid you have 'replaced windows with Ubuntu'. I wonder what process you followed to install ubuntu.

Stop using Ubuntu immediately if you want to rescue data from the lost partition(s).
If you are willing to spend a few $ then I suggest you try '[Macrium Reflect]("http://www.macrium.com/personal.aspx")' or any other Partition/Data recovery tool for Windows. Most of them will not be Free. 

Note: 100% data recovery may not be possible. After all you overwrote the disk with Ubuntu, so the space Ubuntu is installed to is more or less lost permenantly.

If you want to try a free solution then give [TESTDISK]("http://www.cgsecurity.org/wiki/TestDisk") a shot.

A lesson for future: Always BACKUP ALL YOUR IMPORTANT DATA.

---

### Post by WLbUdOa1 on 2013-11-03
I ran TestDisk, but it did not show any Windows partitions...so I guess all my files are lost.
I looked at Macrium Reflect, but it appears that you need to have Windows running.

---

### Post by WLbUdOa1 on 2013-11-03
Do you know if it possible to create a Windows restoration USB with Ubuntu? Is there a chance it might solve the problem at least temporarily so I can move my files? Thanks!

---

### Post by fantab on 2013-11-03
Test disk should help try again, and read the testdisk documentation. Also use photorec, it comes with testdisk. [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

If you access to another Widnows PC then remove your HDD and pulg it in another Windows PC and try any Windows DATA recovery tools.

Edit: I have mistakenly pointed you to Macrium Reflect. I actually wanted to point you to [THIS]("http://www.partitionwizard.com/free-partition-manager.html"). You need to connect your HDD to working Windows machine.

---

