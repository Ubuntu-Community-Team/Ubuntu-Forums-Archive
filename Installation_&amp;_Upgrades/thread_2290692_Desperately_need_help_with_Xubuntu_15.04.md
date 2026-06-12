---
title: "Desperately need help with Xubuntu 15.04"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by cannon_dt on 2015-08-14
Hi,
My existing hdd reported close to 11000 bad sectors and fearing that it would soon die, I got another Toshiba 1 TB HDD and tried to get xubuntu 15.04 into it. My existing hdd had linux mint and it works fine.

After booting via a live USB, I created the following using gparted in my new HDD
- an extended partition for 600 GB
- within this extended partition I created a 20 GB "/" partition for the xubuntu install
- within this extended partition I created a 4 GB swap
- within this extended partition I created a 200 GB home partition for xubuntu

I went ahead and installed the OS and all went well. Upon restart I went into my original Mint installation and performed a sudo update-grub and after restarting I was able to see "ubuntu 15.04" on my grub menu. When I hit it and pressed enter I end up with a black screen. Even the processor light flickers for 2 seconds and then dies, its like nothing is happening and all I can do is a cold boot and get back to Mint.

1. Even recovery mode does not work
2. I tried a nomodeset using CTRL+E on the grub menu but that resulted in the same unresponsive black screen
3. I booted my live USB again and installed additional drivers (the proprietary fglrx driver for my Raden 6600 card) and then reinstalled the xubuntu OS but this again did not work. 

All I get is a black screen and even CTRL+ALT+Fn keys dont get me to a terminal, its like it is dead. 

Is my partitioning wrong? I assumed that I dont need a primary partition and an extended partition would do. Am I wrong? 

I desperately need help as I need to back up the contents of my dying HDD and get this new xubuntu working. I dont know if the xfce is causing these graphical issues but seeing the unresponsiveness of my desktop I dont know what is going on, so I am turning to the experts for help. 

Please do help.

Peace,
Ananth

---

### Post by dino99 on 2015-08-14
ubuntu & the likes can be installed into an extended partition (which is a kind of container; no problem on that side)
so when you have installed xubuntu, you have selected 'something else' option to use the previous partitions set inside the extended one, i suppose.
but are they ext4 or else ? have you also installed grub ? and where ? (you should have set it into /dev/sda or the same as 'mint')
it is strange you cant use the 'recovery mode'. As 15.04 use systemd to boot, maybe try to boot with upstart (you get it into the 'advanced boot menu of grub)
the black screen is a graphic driver issue, try to purge the installed one, then reinstall it (either the opensource, or the closed one)

---

### Post by cannon_dt on 2015-08-14
> **dino99 said:**
> ubuntu & the likes can be installed into an extended partition (which is a kind of container; no problem on that side)
so when you have installed xubuntu, you have selected 'something else' option to use the previous partitions set inside the extended one, i suppose.
but are they ext4 or else ? have you also installed grub ? and where ? (you should have set it into /dev/sda or the same as 'mint')
it is strange you cant use the 'recovery mode'. As 15.04 use systemd to boot, maybe try to boot with upstart (you get it into the 'advanced boot menu of grub)
the black screen is a graphic driver issue, try to purge the installed one, then reinstall it (either the opensource, or the closed one)

Yes, I did do "something else" to use the created partitions done via gparted

While installing xubuntu, I did use the "change" option and marked them as Ext 4 Journaling system and did a format, so that covers that right? If you mean install bootloader (the drop down that comes in the screen after selecting "something else") I installed it in the newly created "/" partition for xubuntu (I did this so that the Mint bootloader still controls the booting process which is why I did a sudo update-grub in Mint to get the Xubuntu option in the grub menu. Is this wrong?

Upstart also did not work. In fact I went into the EDIT mode of GRUB menu and removed "quiet splash" and replaced with text but again just the black screen. Not even text mode.

Given that it is a graphic driver issue, in the live session I accessed addition drivers and chose fglrx proprietary driver and then performed the install - is this not enough. I do have the amd catalyst bin driver but given that I cannot even get to a terminal I am unable to install it in xubuntu.

The strangest thing is the process flickers exactly for a second before the whole machine goes dead, no response of any sort. I am full stumped :(

---

### Post by yancek on 2015-08-14
I almost always install Grub to the / partition as you say you did, then go back to the primary system I use with Grub and update, again as you did so that should work.  You could boot Mint and go to the site below and get the boot repair software and run it and take a look at the output or post it here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cannon_dt on 2015-08-14
> **yancek said:**
> I almost always install Grub to the / partition as you say you did, then go back to the primary system I use with Grub and update, again as you did so that should work.  You could boot Mint and go to the site below and get the boot repair software and run it and take a look at the output or post it here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Actually I had messed up the boot loader and ended up with grub rescue and has to do a boot repair and it is at [http://paste.ubuntu.com/12079221/](http://paste.ubuntu.com/12079221/)

But for the problem I am having I dont see the relevance of this. update-grub worked fine and I can see ubuntu in my grub menu, it is only while booting xubuntu that I am having a black screen.

UPDATE EDIT:
I noticed a strange thing in my BIOS. Only me dying hard disk is listed under SATA 2. SATA 1 is undetected and SATA3 is my CD drive, so if gparted can see my new hdd and partition it and I installed an OS in it why is the BIOS acting oblivious to it.... I am going mad :(

---

### Post by cannon_dt on 2015-08-14
Posting my fdisk output
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0009c773

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   195311615    97654784   83  Linux
/dev/sda2       195313662  1722839039   763762689    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       195313664   203216895     3951616   82  Linux swap / Solaris
/dev/sda6       203218944   593842175   195311616   83  Linux
/dev/sda7       593844224  1013274623   209715200   83  Linux
/dev/sda8      1013276672  1034248191    10485760   83  Linux
/dev/sda9      1034250240  1453680639   209715200   83  Linux
/dev/sda10     1453682688  1722839039   134578176   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00046eeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4094   629153791   314574849    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5            4096    41947455    20971680   83  Linux
/dev/sdb6        41949184    50337791     4194304   82  Linux swap / Solaris
/dev/sdb7        50339840   629153791   289406976   83  Linux

```

So if fdisk can see my sdb then why is the BIOS not seeing it? Could this have something to do with my problem?

---

### Post by cannon_dt on 2015-08-15
Thanks to all for their comments.
The issue was related to the fact that my BIOS could not see the HDD. It was bad cables at the end of it all - after I switched cables (& sata ports on my MB) both HDDs were detected and then xubuntu was loading fine with no black screen.

Peace

---

