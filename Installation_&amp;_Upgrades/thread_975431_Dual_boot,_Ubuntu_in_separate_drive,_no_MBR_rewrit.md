---
title: "Dual boot, Ubuntu in separate drive, no MBR rewrite"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by JoeSabido on 2008-11-08
Before I start, I wanna say that I tried to do a forum search but I got the following error

Fatal error: Allowed memory size of 16777216 bytes exhausted (tried to allocate 24 bytes) in /srv/www.ubuntuforums.org/public_html/search.php on line 1815

My setup:

Motherboard - ASUS M3A78-EM
CPU - Athlon 64 X2 5200+
RAM - 4GB PC6400
RAID-0 (fakeRAID on SATA1 & SATA2 ports on MB / WinXP Pro / NTFS)
Generic IEEE-1394 card on PCI slot
Backup drive on SATA3 (NTFS / Files only)
LG DVD-Recorder on IDE0 / Master
SAMSUNG DVD-Reader on IDE0 / Slave
5.1 Creative speakers (will I loose support for 5.1 audio with Ubuntu?)

My goal:

I have an extra 160gb SATA hard drive lying around, in which I want to install Ubuntu, but I don't want to overwrite my MBR because I can't risk my XP install at this point, and if I don't like Ubuntu I wanna be able to just unplug/format the drive. And if I do like it, then migrate stuff from my RAID to my backup drive and reinstall Ubuntu on the array.

So what I plan to do is unplug all my drives (just for my peace of mind), plug the Ubuntu drive (on SATA5) and install Ubuntu, allowing it to write the MBR of its own drive. Then plug my XP raid back in and I should be automatically go into Windows, since in my BIOS I have the array as the primary boot option.

Now, in my XP System Properties / Advanced tab / Start & Recovery there's an option that *I think* would allow me to list Ubuntu as an available operative system while booting WinXP. I remember I saw this done a while ago (with WinXP & Suse)

Currently, such config has this:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

What would I need to add to this to make Ubuntu boot from the other hard drive?

Please if I'm mistaken at something or if you need more info to help me out, please tell me. I'm not an expert with this Linux thing :( but on the other hand, I'm tired of being a slave of Mock-a-soft.

---

### Post by bulldog on 2008-11-08
Maybe you can find something of use with this link,

[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

---

### Post by cdtech on 2008-11-08
This is the way I did mine:

From a terminal in Ubuntu: (pay attention to the drive, mine is sdb)
mkdir ~/win
## if your using SATA drives
sudo dd if=/dev/sdb of=~/win/ubuntu.bin bs=512 count=1
## if your using ATA drives
sudo dd if=/dev/hdb of=~/win/ubuntu.bin bs=512 count=1
(This will copy the Ubuntu boot sector and save it as a bin file)

Copy the ubuntu.bin file into WinXP C:\
Microsoft has an explination of how to edit the boot.ini file here:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

Just add the Ubuntu location into the boot.ini file:
C:\ubuntu.bin=Ubuntu 8.10

If you want to add to Vista, there is a totally different procedure for this....

Hope this helps ya.......

---

### Post by JoeSabido on 2008-11-09
Thanks! That helps! :D

If anyone has other ideas / methods I'll be glad to read them!

---

