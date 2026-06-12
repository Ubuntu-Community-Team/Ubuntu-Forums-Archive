---
title: "Can't load ubuntu after succeful installation"
date: 2016-01-16
forum: Installation &amp; Upgrades
---

### Post by pawel15 on 2016-01-16
I tried to launch my old laptop (Samsung R610). After bilion diffrent options I've tried with Boot-repair tool and here am I. Here is url which one this tool show me: **paste.ubuntu.com/14539648/**.

I'll be glad for any help :)

---

### Post by mörgæs on 2016-01-17
A good beginning is stating what you want and what you have tried until now (just the most important of your 1.000.000.000 attempts, please). For example, are you aiming for a dual boot or Ubuntu only? Which Ubuntu releases have you tried? 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by kansasnoob on 2016-01-17
So a quick google search tells me that's a fairly old laptop, maybe shipped with Vista???? If so maybe circa 2009 or 2010????

If so I'm curious about the installation type being EFI:


```
=================== parted -l:

Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
1      1049kB  538MB  537MB  fat32              boot
2      538MB   794MB  256MB  ext2
3      794MB   500GB  499GB                     lvm

```

I do actually have an older desktop (circa 2009) that provides the option of booting in either EFI or BIOS mode but I know it works much, much better in BIOS mode.

---

### Post by pawel15 on 2016-01-17
Yeah. Laptop is from the end of 2008 (I think) and oryginaly there was vista, but I have to change hdd for another so I decided to use Ubuntu. 


What I tried? Every combination with options in bios. UEFI. Use various system version, both 32-bit and 64-bit.


Here is result from last try, Ubuntu 14.04.3 LTS and something like this shows up:
[IMG]http://s2.ifotos.pl/img/imagejpeg_snwqnna.jpg[/IMG]

---

