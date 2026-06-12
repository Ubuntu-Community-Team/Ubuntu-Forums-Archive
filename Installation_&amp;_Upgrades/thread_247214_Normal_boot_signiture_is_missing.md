---
title: "Normal boot signiture is missing"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by erik@frontiernet.net on 2006-08-30
I'm trying to set up dual booting with linux and xp. I installed vcom's partition commander on my xp machine and created two partitions. I then installed Ubuntu's linux from a download. The install worked but unfortuneately wiped out my xp. I reinstalled xp from my restore disk and a backup. I reinstalled vcom's partition commander and when I rebooted the machine I can reboot xp but when I try the linux boot I get an error message suggesting that I have a defective boot record. The normal boot signiture is missing. When I  boot up with the Ubuntu disk I can see that linux is loaded, that the partitions are still there and a portion of the hard drive has xp type file definition and there is a portion set up appropriately for linux. When I explored installing Ubuntu again I froze at the screen asking me to change patitions. There must be an easier way to fix the boot process. I don't think fixmbr will work. Any help would be appreciated.

---

### Post by FIONEX on 2006-08-30
Ok, first things first, you need to repair the MBR.  Create a startup disk in windows, then boot using this disk.  From the A drive, type the following "fdisk /mbr".  That'll repair your master boot record.  Now if you can get linux to boot using the linux disks, then reinstall the boot loader from there.

---

### Post by erik@frontiernet.net on 2006-08-30
I used a dos boot cd and when I ran fdisk/mbr I was returned to the prompt. I don't know if anything changed.
So, Iran "fdisk.exe" I get a series of questions about a large disk (mine is 60 gig) patitioned with 20 plus for nts xp and 30 plus for linux. I don't see any option that speaks to actually fixing the master boot record. I guess that is what comes of dealing with graphic interfaces so long I had to use google to find out how to change disks at the dos prompt. Am I even warm? Can I follow the steps for installing the grub from the install cd posted elsewhere?

---

