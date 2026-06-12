---
title: "Partitioning after using Wubi"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by thymurdock on 2010-11-07
I recently installed Ubuntu 10.10 to my laptop via the Wubi installer inside of Windows 7, as I think my boot commands weren't allowing me to boot from the CD, and I was too lazy to fix it. Anyway, I'm not sure how it went about partitioning my hard drive for this. It's confusing me, and I'm not too sure if I need to allow Ubuntu more room, because I plan on letting it become my main operating system, or if I don't. I'll give you some details.
Under in my system monitor program and under file systems it has two systems listed. One, which is my hard drive is labeled as /dev/sda2 under the directory host and the type is fuseblk. The second is labeled as /dev/loop0 and the director is just a / and the type is an ext4 with a size of only 23gb. I'm supposing that files which I download are going to be saved to this area, so what I'm asking is how do I allocate Ubuntu to have more of my hard drive space?

---

### Post by cipherboy_loc on 2010-11-07
Is this from the Wubi install, or did you use the LiveCD to install? If it is from Wubi, I would recommend removing it and re-installing from the LiveCD: Grub2 updates screw the system up. It is best to dual-boot because of this. Wubi is not meant for regular use; it is meant to be a tester to entice user to install Ubuntu from the LiveCD.


Cipherboy

---

### Post by thymurdock on 2010-11-07
Well I burnt the ISO from the download on the website and put the cd in and I installed it from inside windows 7. I'm not sure if there's a difference.

---

### Post by cipherboy_loc on 2010-11-07
There is a difference: Wubi-Ubuntu is installed inside Windows (7 in your case), and using the LiveCD (and booting from it) it is installed on a separate partition.

I cannot find much on google at the moment but the disk access is slower in Wubi than it is in an install of Ubuntu. See here: [http://en.wikipedia.org](http://en.wikipedia.org) /wiki/Wubi_%28Ubuntu_installer%29



From Wikipedia:
**Compared with a regular installation, a Wubi installation faces some  limitations. Hibernation is not supported and the filesystem is more  vulnerable to [hard reboots]("http://en.wikipedia.org/wiki/Booting#Hard_reboot")[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#cite_note-WubiFAQ-0").  Also, if the Windows drive is unmounted uncleanly (most commonly  because of a Windows crash), Ubuntu will not be able to mount the  Windows drive and boot until Windows has successfully booted and shut  down. If the Windows system cannot be booted after the crash, the user  also cannot boot Ubuntu. Performance related to hard-disk access is also slightly slower, more  so if the disk image file is fragmented, on a Wubi install compared to a  normal one.[[1]]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29#cite_note-WubiFAQ-0")**

---

### Post by thymurdock on 2010-11-07
Ok, so it's suggested that I uninstall what I've got already?

---

### Post by cipherboy_loc on 2010-11-07
Yes, I would back up your Ubuntu home folder to a removable drive and install Ubuntu such that you dual boot Ubuntu 10.10 and Windows 7. Shrink the Windows 7 partition (and put it at the front) and create a Ubuntu / partition and a swap partition (which should be about 2-5 GB). If you have a large drive I would recommend:

Windows 7 (> 60 GB)
Shared disk space (About 30 GB)
Ubuntu (> 15 GB)
Swap (5GB)

Ubuntu size is not an issue because I have taken it and slimmed it down to 1.69 gb to run off a flash drive. [flame intensity="100"]Windows 7 is the biggest size waster on the planet, hence it needs a lot of room.[/flame]  ;-)



Cipherboy

---

### Post by garvinrick4 on 2010-11-07
Uninstall your WUBI install in folder in C: drive right next to users. If you do not uninstall will leave a wubildr in Windows grub which is what boots WUBI install and causes a mess
to boot. Fixable but why have the mess.
Open wubi folder and uninstall in side folder.

---

### Post by thymurdock on 2010-11-07
Thanks a lot, I was quite confused as to why it wouldn't let me choose how much room I needed haha.

---

### Post by garvinrick4 on 2010-11-07
If you want help with partitioning put in live Cd (ubuntu install cd and choose Try Ubuntu 
start internet open terminal and post these results. copy and paste one at a time in terminal.
```
sudo fdisk -l
```lower case L
```
sudo parted -l
```lower case L

---

