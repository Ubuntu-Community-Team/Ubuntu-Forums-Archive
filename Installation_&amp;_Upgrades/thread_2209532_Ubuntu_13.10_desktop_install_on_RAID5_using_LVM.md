---
title: "Ubuntu 13.10 desktop install on RAID5 using LVM"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by Gallomimia on 2014-03-06
Greetings; as was suggested to me for my available hardware, I wish to install ubuntu 13.10 desktop edition on a RAID5 of 3 disks. The disks have various data on them, one is blank, all is backed up and I'm ready to destroy the data. I've tried building the raid on a running OS. (I have a working install of 13.10 on a separate smaller drive.)

I've also tried booting from a 13.10 live install, but cannot seem to find options to build or install upon a RAID. (Which is unfortunate. I should hope this gets added to the general installer)

I've tried using the following files to boot and install in the alternate/network install mode. (Alternate seems to be missing from the 13.10 release)

archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/boot.img.gz
archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/mini.iso
archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/boot.img.gz
archive.ubuntu.com/ubuntu/dists/saucy/main/installer-i386/current/images/netboot/mini.iso

None of them boots! I can boot using the flashdrive in question with the liveCD image without difficulty, so I've ruled out problems on that end. I've come to the conclusion that I'm either using the wrong files or the files in question don't work, and I'm looking for help to find the answer. Getting very frustrated and headed to bed now.

As an aside, once I complete this process I plan to use dm-cache to add a pair of SSD's as fast-cache to the array. I'll be looking for suggestions on whether to RAID0 them first or not, and also for suggestions on where to put the swap file for this system, if any (It has 16GB of ram)

Once I do finally finish this process, I'll also be looking for help cataloging all the help files I used and documenting my experience, because there seems to be a serious lack in up to date guides on this type of installation.

---

### Post by Kirboosy on 2014-03-06
You might be able to run a [FakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto") on your box depending on your motherboard. 

If you still wish to proceed the software method you will need to download the [Alternate Installer]("http://www.ubuntu.com/download/alternative-downloads") which should enable to you setup [Software RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

Hope that helps!
~Caboose

PS RAID can be a monster to setup. I'm still fighting with my server on getting a RAID 10 with 4 x 2Tb drives setup properly.
PSS Othertimes it can be really easy and smooth. Lets hope for the latter.

---

### Post by Gallomimia on 2014-03-07
No, it doesn't help. The links to images you provided are the same ones that I haven't been able to get to boot. I will try them again tho. As for "fakeraid" I've heard nothing but bad about this option. For the sake of argument the motherboard is a Gigabyte 990FXA-UD3 and I haven't had much luck with drivers so far. While several of the fanspeed and temperature sensors seem to work, none of them are named or make any sense as to what they measure. (Aside from fan# which is marked on the board) So I'm not hopeful. Any real insight on that matter would be welcomed. I've also seen some talk about the various filesystems available for raid, and I'm still confused about what would be good, mostly because much of the discussion is 5-8 years old.

---

### Post by Gallomimia on 2014-03-08
I've finally gotten the network install to work by switching off UEFI. The computer reboots immediately upon selecting any of the options, either returning to the same screen or starting from the hard disk.

---

### Post by Kirboosy on 2014-03-10
I had issues with the installer automatically configuring GRUB correctly on my RAID. What I ended up doing was after install was rebooting again into the LIVECD and installing/using [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). That seemed to do the trick for me and my RAID would work properly with GRUB after that. Hopefully its as simple for you.

~Caboose

BTW You will need a graphical desktop version of Ubuntu LIVECD for Boot Repair to work.

---

