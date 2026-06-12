---
title: "Dual-Boot Installation Problem"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Ørion on 2010-04-30
Hello, thanks for reading my thread.  I'm reasonably computer literate and have installed ubuntu (both dual-booting and by itself) on a couple of computers, but am no means an expert on linux and am running into some problems with the latest release of Ubuntu (10.04).  Basically, my problem is with partitioning my hard drive.  Previously, when using Ubuntu's installer, I was able to do a guided partition that let me use a nice and noob-friendly GUI to shrink my windows partition and make room for Ubuntu, however when I use the installer for 10.04, the only options I see are manual partitioning and use the entire disk for Ubuntu.  I tried using Gparted (both on the Ubuntu live CD and on its own live CD), however it says that I can only shrink the partition by 1MB (I have a 500 GB hard drive and have only used about 100 gigs of it).  I have also used the Windows 7 disk management utility, which will only let me shrink the partition by 2GB.  I have tried 4 different defragmenting programs (windows, auslogics, puran, and jdefrag) and have tried cleaning up files with the windows disk clean up, CCleaner, ATF Cleaner, and TFC with no improvement.  I did some research and found that the problem may be with the MFT being at the end of my partition, resulting in windows not letting me reduce my partition by more than the 2GB.  I do not, however, know why partitioning on linux is giving me problems and do not really want to try the manual partitioning without some expert help, particularly as I read that the latest release has caused some people to lose data on their windows partition.  Thank you very much for the help, I really appreciate it :)

---

### Post by phillw on 2010-04-30
Hi,

I'm not familiar with Win7 and the page file, but came across this discussion on the subject [http://www.astahost.com/info.php/Defrag-Mft-Pagefile-Boot_t14449.html](http://www.astahost.com/info.php/Defrag-Mft-Pagefile-Boot_t14449.html)  I hope it is of help. I know in the past we could turn the pagefile off when wishing to defrag but I don't know if that is possible with win7.

Regards,

Phill.

---

### Post by Ørion on 2010-04-30
Hi Phil, thanks for the post.  I turned off the page file and defragmented again, however windows still will not let me shrink beyond 2GB :(

---

### Post by lisati on 2010-04-30
My exposure to Win7 so far has been fairly minimal (replacing some trialware on a family member's new laptop with some free and OSS equivalents)

Is turning off "system restore" an option?

---

### Post by phillw on 2010-04-30
Hi, you do realise that this is a Ubuntu support forum ;-) I've done some more digging and have found what I hope is a solution. Obviously as I no longer have Vista and have never tried Win7 I can only say that on reading the instructions they seem reasoned and do alert you to things that can cause failure to boot. It also contains information of a 30 day free trial of a programme that can handle your problem.

[http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html](http://thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html)

I'd appreciate you posting back with how you get on with the instructions. If they are good (and they look it), I'll bookmark that site for future reference. 

Regards,

Phill.

---

### Post by oldfred on 2010-04-30
There has been a lot of discussion about gparted and whether is causes problems. I think Herman explains it and it has to do with rounding of cylinders and a checkbox that most do not know why to use.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

I think this is the same for 7:
Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.

---

### Post by Ørion on 2010-04-30
Thanks for the replies everyone.  I followed that guide, turned of system restore, hibernation, and page files, defragmented with PerfectDisk, and was still unable to make any changes, both with the windows partitioner and with the GParted live CD.  In GParted, it unchecked the cylinder option but still am unable to do much.  Basically in GParted, the maximum size for the reduction is only 1MB more than the minimum size (I can post a screenshot if it would help).  And I know it is an Ubuntu forum ;), but as the issue is with installing Ubuntu and both the Ubuntu installation partitioner and GParted seem unable to do anything, I was hoping someone here could help.  And of course, there's always the fact that linux experts generally know more about windows than linux experts :lolflag:.

---

### Post by reiki on 2010-04-30
You may have "unmoveable" files in a section of your hard disk. Windows creates them and makes life interesting. The only way I've found to surely get around this is to wipe windows, reinstall it, and the very first time it gets to desktop, STOP. Shrink the windows partition immediately before it writes any more to the partition. I know this is especially true of Windows 7 as I started with a 750GB drive with win7 64-bit in a brand new machine. First boot, got to desktop and immediately used the windows disk utility to shrink the windows partition to 100GB. Another person with the EXACT same machine used windows for a couple days, installed some software, etc, tried to shrink it and ran into exactly what you're seeing. Could not shrink the windows partition to anything less than about 500GB. Windows had written some "unmoveable" files to that space. Wipe, restore, reboot, and shrink on first boot fixed it for him.

Not sure how willing you are to wipe windows and redo it, but that was my experience so far. :)

---

### Post by Ørion on 2010-04-30
I was afraid of that :(  I have lots of stuff and don't really want to go through the trouble of reinstalling windows.

---

### Post by phillw on 2010-04-30
> **Ørion said:**
> I was afraid of that :(  I have lots of stuff and don't really want to go through the trouble of reinstalling windows.

Hard disks are cheap, have you considered getting one? Other than that, I'm out of ideas :-(

Regards,

Phill.

---

### Post by Ørion on 2010-04-30
Yeah I might end up doing that.  I'll save up a bit and buy a cheap 50GB or so hard drive I guess.  Well thanks for all your help everyone, I really appreciate your time :)

---

### Post by phillw on 2010-04-30
shame you not in UK, 80GB  drive for 17GBP

Phill.

---

