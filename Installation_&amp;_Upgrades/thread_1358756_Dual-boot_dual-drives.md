---
title: "Dual-boot dual-drives?"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by iSephy on 2009-12-18
I have two 200gb IDE Hard Drives and I want to install Windows XP on my Slave and Ubuntu 9.10 (Karmic Koala) on the Master. I tried once to do this, but when I turned on the computer, it went to the black screen and hung with only a flashing "_" on the screen. 

Please help. :confused:

~Seph

---

### Post by darkod on 2009-12-18
IDE drives can be difficult getting the wanted boot order. Are you able to select in BIOS which drive is first choice and which second? Or the Master is always first?
Because when installing windows it needs to be Master (at that moment), so maybe after the XP install you will need to switch the drives for the XP drive to be Slave, and then install Ubuntu on the Master.
Maybe that was the problem last time, but I can't be sure.

---

### Post by iSephy on 2009-12-18
I can choose which drive boots first, but I should go into more detail. I have two DVD(+-)RW Lightscribe drives on another cable. I don't know if that matters, but I thought it might be of some interest.

---

### Post by darkod on 2009-12-18
It shouldn't. It should just ignore the optical drives.

Also, did you try running the Try Ubuntu option first? The black screen with flashing cursor is sometimes due to wrong driver. The Try Ubuntu option is a good test whether your system will work with default drivers/settings.
If there is some problem that Try Ubuntu reveals, you can be almost sure that the installed system will react the same.

PS. Even if it is video driver issue, it doesn't mean it can't work. There is option to select the recovery mode entry in grub menu (if you get to the grub menu at boot) and under recovery mode to update the driver. I had to do that on my desktop and it works great.

---

### Post by iSephy on 2009-12-18
I have tried that, but when I removed the hard drive with Ubuntu out, it worked perfectly, no hang up or anything. I think it might be because of GRUB, or whatever. :P I'm relatively new to Ubuntu, so I don't really know what GRUB is besides the fact that it's a boot loader, so if you could help me with *that, *too, that would be great! :D

---

### Post by darkod on 2009-12-18
Well, as the name says, basically it's used to load the OS. Ubuntu, Windows, etc. Does the error happen after you select Ubuntu from the menu? Do you get the menu? If you select windows does it boot OK?

---

### Post by iSephy on 2009-12-18
What happens is, I get my normal blue screen that says "HP a1209n Intel Processor, etc." Then, my computer goes to a black screen with a "_" at the top-left and just blinks. It never goes to anything else. I even left it running all night to see if it would work eventually. It didn't. So no.

---

### Post by darkod on 2009-12-18
OK. Boot with ubuntu cd, Try Ubuntu option, open terminal (in Applications-Accessories) and execute:
sudo fdisk -l (small L)

Copy the result here and don't reboot, I'll give you few commands to reinstall grub2 for a start. I'm waiting. :)

---

### Post by darkod on 2009-12-18
OK, I gotta go. You can read how to reinstall grub2 here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just use the instructions for 9.10 which uses grub2 and which you also use if this was a clean 9.10 install (not upgrade from 9.04).

---

### Post by iSephy on 2009-12-18
It asked me for a password and username when I tried to input sudo fdisk -l

---

### Post by iSephy on 2009-12-18
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20492048

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdf: 2017 MB, 2017525248 bytes
4 heads, 32 sectors/track, 30784 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30785     1970223+   e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$

---

### Post by oldfred on 2009-12-19
It is only showing one 200GB drive and your 2GB USB key. If your system only has ide (pata) drives, you may not be able to switch order in BIOS like you can with the newer Sata drives. It depends on motherboard. 

Older ide drives have jumpers on the drive to select master and slave. Each must be set correctly to work. Newer ide drives with the 80 wire cable are cable select and have three different colors on the cable connectors. The middle is the slave and the end is master.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)

---

### Post by iSephy on 2009-12-19
I had only one drive plugged in because I forgot to plug the other in... xD I have it fixed now, though, thanks!

---

