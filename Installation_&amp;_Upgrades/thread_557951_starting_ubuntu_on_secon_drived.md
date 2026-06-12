---
title: "starting ubuntu on secon drived"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by pieniaszek on 2007-09-23
Dell 4155. I want to dual boot XP and Ubuntu, with XP completely on the primary hard drive and Ubuntu completely on the slave.

Initially,  installed ubuntu 7.04 on the single hard drive, eliminating the XP i had installed.  I personalized that ubuntu installation.
I then purchased a new hard drive, moved the hard drive with ubuntu to the slave position and installed XP on the primary.

I downloaded a new iso 7.04 to install on the slave, but wonder how I could  open the second hard drive which has 7.04 on it, without a clean re-install?

I have stopped at that point in the new re-install states;
partition #1 of SCSi1 (0,1,0) (sdb) as ext3
partition #5 of SCSi1 (0,1,0) (sdb) as swap

Why does swap go on #5?
How do I understand how ubuntu partitoning work?

Does the install see that I had Ubuntu, or something on that disk?

---

### Post by logos34 on 2007-09-23
your swap, sdb5, is a logical partition (they start numbering with '5')...the guided installation often puts the swap inside an extended partition.  

The installer will overwrite the existing root on sdb1. 

Not sure why you are reinstalling.  If you just want to be able to dual boot ubuntu and windows on the other disk, all you have to do is add XP entry to menu.lst and fstab.

More on dual booting:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you want to use Grub to boot windows on the other drive, you need to edit men.lst for 'virtual swapping' of drives:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)

---

### Post by pieniaszek on 2007-09-23
Not sure why you are reinstalling. If you just want to be able to dual boot ubuntu and windows on the other disk, all you have to do is add XP entry to menu.lst and fstab.

You lost me with "add XP entry to menu.lst and fstab".

I'm had Ubuntu operating when I only had one hard drive. I don't want to end up with the MBR problems I had before, with two older PCs in my 
cellar "stuck" in Mandrake 10. ( and I never really learned the Unix part of Linux.)

---

### Post by logos34 on 2007-09-23
Clarify the situation for me, if you could:  

Can you boot into windows?  And can you still boot ubuntu (by switching the Bios hard disk boot order)?

---

### Post by pieniaszek on 2007-09-23
I set my boot sequence to start with the CD, then the hard drive.
If I want to start Ubuntu ( and I haven't let it finish yet), I insert my iso CD, otherwise i boot up XP.

Setup doesn't (or I don't know how to) boot from the second hard drive.  If it's possible, that would be the best way, at least from my thinking.
That second drive with Ubuntu was running and I was at least saving some Linux favorites in Firefox.

---

### Post by logos34 on 2007-09-23
no, what you're referring to is the Bios device boot order.  What you want is the *hard drive* boot order--there should be a submenu for each class of storage device (removable/floppy, optical/cdrom, hard disk drive).  Set the slave drive with ubuntu first.

---

### Post by pieniaszek on 2007-09-24
Thank you for making me realize that I have a something strange since I reinstalled XP.  What was a C Drive is now G, the Hard-Disk Drive Sequence starts with System BIOS boot devices, then a USB device (not installed)  ((I just ran a printer from the USB port)).
AND, my boot sequence is 1. IDE CD ROM ( my Ubuntu iso CD only would run from the DVD device), 2. Hard Disk Drive C ( I don't know what that is now), 3 Diskette drive

I'm missing some drivers. By the way, I found an application at [www.driveragent.com](www.driveragent.com) which checks drivers and identifies ones needing updating.  In my case, update means initial install since an XP reinstall doesn't include drivers.

---

### Post by pieniaszek on 2007-09-29
Dell 4155. XP on primary with 160GB. Ubuntu on slave with 60 GB.

Ubuntu was the primary on a 60GB hard drive. I installed a new 160GB drive as the primary and moved the drive with Ubuntu to the slave position.

I used the Dell Reinstall XP disc with SP1 to install XP on the primary, then installed SP2.  I noticed that somehow XP was installed on the "G" instead of "C", but felt that I would use the XP capability to re-letter.

XP worked and I re-installed updated drivers using Driver Agent.
I then installed Partition Magic 8.0 with the intent of using the Boot Magic feature to be able to select XP or Ubuntu.
First problem was that Partition Magic would not let me create a small FAT32 partition which is necessary to install Boot Magic.  I guessed that the G vs C may be a contributor and used the feature in Partition Magic for re-lettering drives.

Now I am in the impossible state of not being able to open XP. At the Welcome page, with the start icon showing, I select it and after a brief 
display of "setting", the I see "logging off".  Neither my CD, DVD nor Floppy drives can be accessed.  I can get to the BIOS start page and see both all drives.  I must have caused the drive re-lettering to screw everything up.

Can I switch primary and slave, boot with Ubuntu then see XP?

I would appreciate any help to get out of this dilemma.

---

### Post by logos34 on 2007-09-29
> **pieniaszek said:**
> Can I switch primary and slave, boot with Ubuntu then see XP?

You don't have to physically swap them--just go into the bios and arrange the hard disk boot order so that the 60 GB boots first.  

You can then add a windows entry in fstab so that [XP mounts]("http://www.psychocats.net/ubuntu/mountwindows") and you can access it...You can also add an entry in menu.lst so you can chainload XP bootloader from Grub, but it won't work if you can't already boot directly into windows. 

Not sure what the problem is with windows and PM, or how the drive lettering ended up the way it did (unless one of the optical drives got labeled C: ).  PM [user's guide]("ftp://ftp.symantec.com/public/english_us_canada/products/norton_partitionmagic/npmagic_8/manuals/norton_partitionmagic_8.pdf") recommends running chkdsk on windows partition and turning off antivirus beforehand.  In your case you'd have to run chkdsk from the recovery console on the XP install cd.  

You might consider reinstalling windows, taking care to format the entire drive as one NTFS partition C: , or else leaving a small sliver of unallocated space at the head of the disk for PM.

---

### Post by pieniaszek on 2007-09-30
Thanks for your help.
I had to resolve my inability to install XP on a new disk first. 
Turns out that a corrupted driver made that new disk useless and I couldn't boot from a CD because the optical read device was bad.  So,
I ended up buying another new disk and a new CD device. Installed both, removed the slave with Ubuntu and made the old(new) disk the slave.
Once I installed XP, I installed Acronis Disk Director 10.
I used  the MS tool to clean the slave.

Now I have a Ubuntu iso CD and I intend to install it on the slave.

I will try the Acronis "Boot from a CD/DVD" feature.

---

### Post by pieniaszek on 2007-10-04
I now have Ubuntu installed on my second hard drive. I previously installed Acronis Disk Director for the purpose of using its Boot Manager.
After I installed Ubuntu and rebooted, it appears that my MBR was changed because the first screen that appears provides list of Ubuntu selections, then Windows XP.

I do I "put" the Acronis Boot Manager back in control?  Do I run Fdisk/MBR?

I want to re-partition my second drive and found a web site describing Gparted, but then I could not find details on how the tool works.

Is the GParted tool the best to use for partitioning?

---

### Post by logos34 on 2007-10-04
> **pieniaszek said:**
> do I "put" the Acronis Boot Manager back in control?  Do I run Fdisk/MBR?

no, fdisk /mbr will restore the *windows* bootloader.

> Is the GParted tool the best to use for partitioning?

Gparted is very good.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

