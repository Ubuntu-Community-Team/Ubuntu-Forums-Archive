---
title: "installer not able to detect ssd drive [false raid?]"
date: 2016-07-06
forum: Installation &amp; Upgrades
---

### Post by kkedzierska on 2016-07-06
Hi, 

while attempting installation of 16.04 ubuntu I discovered that linux (I tested ubuntu 16.04, 16.10 and the latest arch distribution to check latest kernel) is** unable to see my ssd drive**. lsblk gives only information on flash drive on which I recorder iso.

**Lenovo Yoga 900** 80UE
BIOS version 2UCN06WW
SSD: SAMSUNG MZVLV512HCJH
my computer has something like **Intel® Rapid Storage Technology** and on some forum I read that it has false RAID. 

what I know is that to go through this issue in previous models one could change drive settings to AHCI (not sure about that as I don't actually understand this ahci, raid, ide things). Unfortunately in the latest yoga 900 model and current BIOS version there are no advanced options. 

Does anyone has some solution and advice how to discover this disk for linux, especially ubuntu?

---

### Post by oldfred on 2016-07-07
It should be under drive settings somewhere or even a separate page, but do not know Lenovo Yoga.
Do you have latest UEFI/BIOS version?

       With the Linux 4.4 kernel the Lenovo Yoga 3 laptop owners out there will finally have support for using their ESC key.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-ESC-Key-Patch](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.4-ESC-Key-Patch)
Many Lenovo function key issues
[https://groups.google.com/forum/#!topic/fa.linux.kernel/f7lTE1YafwQ](https://groups.google.com/forum/#!topic/fa.linux.kernel/f7lTE1YafwQ)
Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/) 
    
Have not seen many recent systems with Intel SRT. That was used to allow Windows to seem like it booted quicker. It really is just a caching typically on a small SSD used just for booting. Some with larger SSD 24 or 32GB turn off SRT and installed all of / (root) into SSD making all of Ubuntu fast, not just boot. Either /home or data partition(s) were then on hard drive.

Intel SRT seems to be identical across brands.
older installs, but I do not thing SRT has changed. And newer version of Ubuntu usually see RAID (old versions would not even see the drives), but grub may not install correctly.
       Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382) 
            Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by sebasgt09 on 2016-07-27
> **kkedzierska said:**
> Hi, 

while attempting installation of 16.04 ubuntu I discovered that linux (I tested ubuntu 16.04, 16.10 and the latest arch distribution to check latest kernel) is** unable to see my ssd drive**. lsblk gives only information on flash drive on which I recorder iso.

**Lenovo Yoga 900** 80UE
BIOS version 2UCN06WW
SSD: SAMSUNG MZVLV512HCJH
my computer has something like **Intel® Rapid Storage Technology** and on some forum I read that it has false RAID. 

what I know is that to go through this issue in previous models one could change drive settings to AHCI (not sure about that as I don't actually understand this ahci, raid, ide things). Unfortunately in the latest yoga 900 model and current BIOS version there are no advanced options. 

Does anyone has some solution and advice how to discover this disk for linux, especially ubuntu?

I have the same problem, do you already solve it?

---

