---
title: "[SOLVED] IDE driverecognized as SCSI - won't boot"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Thriell on 2008-11-23
First off: I've been fiddling with computers since the days when people were happy to pay Radio Shack $500 for a z-80 machine that had 4K of RAM and nobody had ever HEARD of Microsoft or Windows. I'm not afraid of a command prompt and can follow instructions.

With the exception of a shell account I once had (and rarely used) on a RedHat Linux server, Linux is pretty much new territory for me.

I booted Ubuntu 8.04 from the LiveCD and ran the install from within the desktop (Gnome??). Everything went smoothly, but the new OS won't boot. I have been messing with this for a week and the only thing I've figured out is that my 80gig IDE drive SHOULD be called /dev/hda but instead it is seen as /dev/sda.

The result is that GPartEd can edit the partition table if I boot from the LiveCD, but when I try to boot from that drive, the system is trying to access an SCSI drive and fails miserably.

I've searched this forum and google enough to figure out that there was a recent "update" that caused this problem for a lot of people, but nobody seems to have a fix.

One thread suggested changing the BIOS setting from IDE to RAID, but my motherboard ([gigabyte ga-6vtx]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ProductID=1388")) is a little on the old side and doesn't HAVE such a setting.

Any other ways to get this beast to boot, short of just saying "forget the whole thing"?

---

### Post by psusi on 2008-11-23
No, it should be called exactly what it is.  Since you don't really mention what is going wrong ( "won't boot" is not an error description ), we can't help.  What exactly happened when you rebooted after installing?

---

### Post by Thriell on 2008-11-23
> **psusi said:**
> No, it should be called exactly what it is.  Since you don't really mention what is going wrong ( "won't boot" is not an error description ), we can't help.  What exactly happened when you rebooted after installing?

The first several times, I watched that neon orange bar bounce back and forth for about 10 minutes and then I was greeted with a command prompt that said "initramfs".

After looking around here, I figured out how to edit the boot options and remove "quiet" so I could watch several dozen screens worth of text fly by until it came to a screeching halt at a line that complained about not being able to read a partition table. I'm afraid I don't have the exact error message, but the partition table IS  good ... Windows XP is alive and well on the only active partition. I'm trying to set up ubuntu as a dual boot in the unallocated space (15 gigs)

---

### Post by psusi on 2008-11-24
Getting that exact message would help.  What kind of setup do you have?  Is it just a plain vanilla single disk system that had windows installed in a single partition before, and you had Ubuntu carve off some space to install to?  What does sudo fdisk -lu say?

---

### Post by Thriell on 2008-11-24
> **psusi said:**
> Getting that exact message would help.  What kind of setup do you have?  Is it just a plain vanilla single disk system that had windows installed in a single partition before, and you had Ubuntu carve off some space to install to?  What does sudo fdisk -lu say?

I wish I could just give you a brand name and a model number to describe the system, but this is a system that I put together 4 years ago out of parts that I either already had or bought on ebay. The motherboard is a Gigabyte GA-6VTX, and to that I've added a single IDE hard drive, 800MB RAM, a CD-RW, a DVD±RW, an ATI Rage Video Card, and a network card whose brand name escapes me at the moment.

I started with Windows taking up the whole 80GB drive. I resized the Windows partition to 65GB and then ran the Ubuntu install. When it gave me the partitioning options, I chose "Manual". In the 15GB of free space, I made a 512MB swap partition, a 100MB ext3 partition with the mount point "/boot" and the rest of the available space as an ext3 partition mounted to "/". The install program then merrily wrote the necessary files to the disk ( I booted windoze and was able to verify that the Ubuntu files did, in fact, get written to those partitions).

I just booted from an 8.10 CD and when I clicked "Computer" from the "Places" menu, it actually showed the partitions on my hard disk instead of an SCSI drive which I don't own.

I'm even able to browse the contents of those partitions and load "/grub/menu.lst" from the 100MB partition into a text editor.

I think I'll just start over with 8.10. It seems that 8.04 is broken, at least as far as my machine is concerned.

Thanks for putting up with me. ;)

---

