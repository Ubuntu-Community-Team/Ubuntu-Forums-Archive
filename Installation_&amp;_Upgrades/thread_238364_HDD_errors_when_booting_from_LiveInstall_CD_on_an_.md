---
title: "HDD errors when booting from Live/Install CD on an Ubuntu only PC?"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by sbmd on 2006-08-17
I get the following errors when tring to boot from the Livecd. 

ata1: translated ata stat/err 0x51/40 to scsi sk/asc/ascq 0x3/11/04
buffer I/O error on device dm-1, logical block

I have 2 sata hdd and 2 ide dvd roms. I am using this [Gigabyte]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1631") board. I installed Ubuntu in this matter and now when I boot to the livecd that I used to installed a few months later I get these errors. 

It seems that similar problems have been received from some people but noone really knows what to do. 

I have read that you can hold ctl+c during the evms and it lets it pass, but is there something wrong with my system?

---

### Post by dearingj on 2006-08-27
> **sbmd said:**
> I get the following errors when tring to boot from the Livecd. 

ata1: translated ata stat/err 0x51/40 to scsi sk/asc/ascq 0x3/11/04
buffer I/O error on device dm-1, logical block

I have 2 sata hdd and 2 ide dvd roms. I am using this [Gigabyte]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1631") board. I installed Ubuntu in this matter and now when I boot to the livecd that I used to installed a few months later I get these errors. 

It seems that similar problems have been received from some people but noone really knows what to do. 

I have read that you can hold ctl+c during the evms and it lets it pass, but is there something wrong with my system?

I'm starting to see the same error. I ran reiserfsck and it said it found unrecoverable errors, but Windows' Scandisk doesn't find anything wrong with my hard drive, with either my Windows or Linux partitions (reformatted so Scandisk could read it).:-k

---

### Post by sbmd on 2006-08-27
I also notice that when i boot to the cd and hold the ctl+c to get past the event manager the live cd freeazes or hangs at the partioning screen. It just hangs on the loading the partitions part, the progress bar continueally goes and nothing ever comes up, I have let it go over night once. What has happened? as this is the same cd i installed ubuntu with? thanxk ofr your help in advance, but i would like to get this working on my PC. ](*,)

---

