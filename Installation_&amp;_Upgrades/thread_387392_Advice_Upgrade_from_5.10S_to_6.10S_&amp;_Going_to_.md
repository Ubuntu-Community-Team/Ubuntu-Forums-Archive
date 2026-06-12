---
title: "Advice: Upgrade from 5.10S to 6.10S &amp; Going to RAID?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-18
I have been running Ubuntu 5.10 since shortly after its release in late 2005. I moved to Ubuntu after working with Slackware and Gentoo but I am no means a Linux expert.

I have been running on the following hardware:

ASUS CUSL2 Motherboard
Intel Pentium III 866Mhz
2 x 256MB SDRAM
1 x 400GB PATA Hard Drive.

Before making the upgrade to 6.10 Server, I am going to take out the 400GB drive, add a 3ware 8006-2LP RAID 0/1 card, and two Seagate 7200.10 500GB SATA harddrives. I am going to put them in RAID 1. 

I have read some online documentation about the 3ware card and its BIOS setup seems relatively straight forward. 

I'll then put the Ubuntu 6.10 Server installation CD into the CD-ROM drive and let it boot. I assume it will automatically "see" the RAID setup as one 500GB drive? Or will it see both? If both, I assume I simply partition one of them and the RAID card will mirror accordingly?

I imagine I will simply use the default partition scheme? Any advice there would be fine.

I will probably go ahead and install the LAMP version of Ubuntu 6.10 Server. That includes Apache2 among other things. Otherwise, I will also install OpenSSH Server and SAMBA. 

Now, one thing I did not install last time that people told me I should was some sort of e-mail client so that the system could send me messages, including important errors. What do you all think? Is this necessary? Is there a way to configure software for the 3ware card such that it sends me an e-mail if one of the drives in the RAID array fails? Is there software that can generate status report in HTML and put that in the Apache2 folder for viewing online?

Finally, I have close to 80GB stored on the 400GB drive in /usr/myname#. What is the easiest way to transfer those files onto the new RAID array? Simply connect it using a PATA cable to the IDE0 port on the motherboard and mount it? Otherwise, I could simply move the 80GB to another computer and move it back onto the Linux machine once SAMBA is up and running.

Any advice on these issues would be appreciated. I would especially like to hear from anyone who has a RAID 1 setup using the same 3ware card.

Thanks!

---

### Post by tomazb on 2007-03-18
You are very wise man. Been fighting with fake (nvidia on board) raid for my friend for several days and it aint over yet.

Yes, proper hardware raid will appear as single disk unit(s) to your OS. So in this case you will see one 500GB "disk" connected to 3ware card. 

You can download 3DM2 which is a web console to monitor and control your 3ware from remote. With 9500 and bigger models it will also do periodic housekeeping stuff like checking physical stuff and such. And also send you an email if something bad happens to your disks. Be prepared to do some slight work to install it since install scripts from 3ware only support RedHat and Suse, but it is worth it.

Fastest way to copy data is via internal PATA cable in your case - you will get probably between 20 and 40MB/s - perhaps more. Depends on several factors.

---

### Post by Holzmann on 2007-03-18
> **tomazb said:**
> You are very wise man. Been fighting with fake (nvidia on board) raid for my friend for several days and it aint over yet.

Yes, proper hardware raid will appear as single disk unit(s) to your OS. So in this case you will see one 500GB "disk" connected to 3ware card. 

You can download 3DM2 which is a web console to monitor and control your 3ware from remote. With 9500 and bigger models it will also do periodic housekeeping stuff like checking physical stuff and such. And also send you an email if something bad happens to your disks. **Be prepared to do some slight work to install it since install scripts from 3ware only support RedHat and Suse, but it is worth it.**

Fastest way to copy data is via internal PATA cable in your case - you will get probably between 20 and 40MB/s - perhaps more. Depends on several factors.

Thanks for the reply!

I have never set up e-mail anything on a Linux machine, so I hope there is good documenation for this. The "installing of scripts" as you put it also sounds foreign to me.

Right now that same 400GB drive that has my data also has Ubuntu 5.10 installed on it. Will I run into boot problems if that drive is connected at the same time as the two 500GB drives on the 3ware card? Otherwise, if it boots into 6.10 as it should, I simply need to mount that 400GB drive, go to the right directory and move the files over.

---

### Post by tomazb on 2007-03-19
If you set boot order to SCSI first, then 3ware will be the boot device. Usually additional cards in the system are seen in bios as SCSI devices.

You can read about Debian package for 3ware which allegedly also works at [http://zeroasterisk.com/blog/index.php/2007/03/06/3dm2-3ware-raid-management-tool-on-ubuntu/](http://zeroasterisk.com/blog/index.php/2007/03/06/3dm2-3ware-raid-management-tool-on-ubuntu/)

---

