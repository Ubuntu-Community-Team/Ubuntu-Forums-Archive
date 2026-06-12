---
title: "Ubuntu 8.04 + Hardware RAID0"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by jpag3074 on 2008-09-24
Good Evening to all!
I am new to Ubuntu (I have done some Fedora installs ect.) and overall a newbie to Linux. I am setting up Ubuntu on my home brew PC and have 2 x 10k raptors in it on a RAID 0 (on Promise T3Controller)
The Ubuntu CD recognized my drives hooked to the controller, but it does not recoginize the RAID0 Array I have setup. I am assuming this is because I need to load some type of driver prior to it seeing my array.
I have googled this and browsed multiple sites with not much avail. I was hoping someone could point in the right direction on getting this working, as I would love to have Ubuntu as my main OS.
I appreciate the assistance.
Josh

---

### Post by cariboo on 2008-09-24
to set up raid you should follow this howto:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I used it to set up my server about a year ago and it is still going strong.

Jim

---

### Post by jpag3074 on 2008-09-27
Ok
I used your link and was not able to get DMRAID to function properly
BUT - I checked for BIOS updates to my K9A2 board and found that there was 1.5 (I was running 1.4)
AFTER a BIOS update, I used DMRAID and was able to get successfully get Ubuntu and Linux Mint to see my RAID 0
Thank you very much
Josh

---

### Post by jpag3074 on 2008-09-27
Ok - Update
I am able to see my RAID when I go through Linux Mint setup 
I created 4 partitions (working with 500 gb)
1gb /boot ext2
4096mb /swap
50gb for / ext3
the rest /home ext3

Now when I go to start the format, it spits out error
"The ext3 file system creation in partition #3 of Serial ATA RAID pdc_bcjjdcbdjd (stripe) failed"

BUT if I change the ext3 to ext2 for the other partitions, the format goes through normally - I do not want to run ext2 for my main partitions, and I am at a standstill at this point, just researching, ANY input is appreciated.

I have successfully loaded Fedora 9 without any issue whatsoever (no loading of DMRAID or anything) just as a FYI, but I really want to work with Ubuntu or Mint

Thanks,
Josh

BTW Hardware Specs
MSI K9A2 Platinum BIOS ver 1.5
Phenom 9850
2 x 250GB Seagate SataII hooked to SB600 controller
ATI Raedon 3870
SATA Lite-On 18x DVD
500W Thermaltake Purepower 500

---

