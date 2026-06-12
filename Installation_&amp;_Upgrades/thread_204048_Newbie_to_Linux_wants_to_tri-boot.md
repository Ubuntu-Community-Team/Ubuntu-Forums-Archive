---
title: "Newbie to Linux wants to tri-boot"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by a1musicman on 2006-06-26
Hello all,

I am new to Ubuntu, and really like what I see. I am new to Linux, but not new to computing, having built several computers and know a bit about partioning, etc. I would like to take my dual boot computer (WIN 98 SE & WINXP Pro) and add an Ubuntu boot as well. I run a lot of things through my machine, as I do a lot with audio and video.

Here is my machine:

3.0 GHz Pentium 4 Processor, 1.5 GB PC 3200 RAM, 650 W power supply, DVD Burner, CD Burner, 3 hard drives - 250 GB Maxtor, 100 GB Maxtor and 160 GB Maxtor. The 250 and 100 are IDE and the 160 is SATA, the 250 is my main boot drive, partioned as follows: 10 GB for WIN 98, 50 GB for WINXP Pro (NTFS), 20 GB NTFS (this is where I would like my Ubuntu to go), 100 Gb NTFS for storage and 65 or so GB FAT32 for storage. Converting the last FAT32 partition to another file system is not a problem yet (just need to move the data to another drive).

I have the latest Live CD (6.06) and actually am booted in the Ubuntu now.

My question is, where do I go from here?

Thanks for the help!
Steve

---

### Post by zxee on 2006-06-26
You should be able to select that 20GB partition for ubuntu & install to it.
Grub (GRand Unified Boot-loader) should set up your window's partitions for booting.
However it's always a good idea to back up. There is also an option to not install grub to the MBR. In that case you could use another bootloader from windows to boot into ubuntu e.g [http://wiki.linuxquestions.org/wiki/Smart_Boot_Manager](http://wiki.linuxquestions.org/wiki/Smart_Boot_Manager). 
Hope that helps.

---

### Post by MikeMLP on 2006-06-26
There have been significant problems using the liveCD.  I also wish to dual boot, with XP, but havn't yet done so, because I am still trying to "measure twice and cut once," that is, do all my homework to prevent headaches and data loss.  As far as I can tell, there are two places where the live CD can muck things up:

1.  When resizing an NTFS partition using the Ubuntu LiveCD version of Gparted (.1)  I would recommend using the Gparted LiveCD which will give you the latest version (.2.5-2) of Gparted (or other partitioning software if you already have it).

2.  The installation of Grub to the MBR can cause difficulty when trying to load up an install of Windows using NTFS (see [https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661]("https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661")

I have been looking at alternative choices that allow me to leave my MBR as alone as possible, and, if you decide to install using the Ubuntu 6.06 Alternate CD, you can write the bootloader, Grub or Lilo, to the linux partition instead of the MBR, and load using a GAG boot CD, or by tweaking the windows bootloader (NTLDR) by hand (doesn't look that difficult to me) to chainload into Linux.

You could just give the LiveCD a shot, but I've seen a lot of people here upset with windows partitions that aren't bootable.  It seems that it may be possible to repair some of them, but others may have more difficulty.  I would also back up the MBR before starting as well (it is what I plan to do), unless you don't mind reinstalling windows if a problem arises.

As I am a Newbie, I have learned most all of this from this site:[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by a1musicman on 2006-06-27
Thanks for the info! I think I am going to do some more homework as well, as I do not want to screw anything up - I can be patient. Best of luck to you!

---

