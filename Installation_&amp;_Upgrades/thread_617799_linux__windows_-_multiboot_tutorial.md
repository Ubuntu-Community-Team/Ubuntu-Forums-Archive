---
title: "linux / windows - multiboot tutorial"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by bluepowder7 on 2007-11-19
ok, so it's high-time to set up the desktop PC for multi-boot, by adding Ubuntu.  the pc currently has win2k and winxp on their own partitions, and i've pre-partitioned the drive ahead of time so there's space reserved up front and out back.  my hard drive is a 160 gig SATA drive, and here's my partition layout thus far:

240meg /// 45gig Win2k /// 55gig WinXP /// 60gig or whatever was left over

these are my current 4 primary partitions.  now, they two Win partitions are each NTFS, and the 240meg up front is set aside in case i need to have my linux /boot partition there.  not sure if that's correct or not, but it's there.

since i want to install Ubuntu and reserve some space for other OSes (like another flavour of linux and later on a BSD), that last 60gig is gonna get cut 4 or 5 ways (a few OSes and a final swap partition).  i can do that using GParted easily enough, and i can set up the file system types on each of the partitions too (240meg up front and that giant 60gig chunk).

question 1 - does that 240meg /boot partition need to be FAT16, or can it be ext2?
question 2 - should i install Ubuntu 7.10 from a live CD (which i already have), or should i download some other version?
question 3 - is there anything i should back up onto a floppy or USB memory stick before proceeding, like the Win loader (wherever it happens to be)?

and, of course, question 4 is where would i find a good tutorial for my case?

i'm not worried about my "user files" like the MyDocuments folder since that's already backed up on a memory stick, and both Win installs are fairly new so i haven't had time to really load up THAT much software.

last time i tried "dual boot", i didn't go by any tutorial and just let the second OS installer do its thing and that ended up hosing my PC.  would be nice to avoid that this time around!!!



EDIT - ah, bugger - can a mod or admin change the title from "tutorial" to "questions", please?

---

### Post by Pumalite on 2007-11-19
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://partedmagic.com/](http://partedmagic.com/)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by louieb on 2007-11-19
Cool a guy that backs up his data - what an idea!
Now 1st about putting /boot on a separate partition not a bad thing.  but unless you have an old BIOS its not really necessary. (and if you do make one only let 1 distro max mount it on /boot) If you plan to use GRUB for your boot loader/manager then ext2 or ext3 is the way to go.

When you are booting multiple Linux distros look at something call chainloading also look at using the configflle option. Both are described on the GRUB page of the Dual Boot link in my signature.  

The Dual Boot site is a very good source of information, examples, and most other things dual boot. Plan to spend some time  there.  

Good Luck.

---

### Post by bluepowder7 on 2007-11-19
ya, i did end up at HermanZone, and that's making me contemplate two options:

* option 1 = use that 240meg partition up front as a shared /boot partition for all my OSes (will need some management work on my part later on when i get around to installing the second linux OS), and presumably have the GRUB loader there as well

or

* option 2 = use that 240meg partition up front as just a GRUB partition, and keep the /boot of each linux OS within its own partition (which won't start until around 110gigs from the front of the hard drive)

option 1 would take some manual work to keep conflicts and file over-writes to a minimum, but would inherently avoid any sort of BIOS address limit (and really, i won't need to do any manual work until i get around to installing the SECOND linux OS, which buys me some time)

option 2 is easy to do overall i think, but i'm not ENTIRELY sure if that's safe, since only the first two or three linux OSes would have their /boot within the mystical 120gig or 137gig region, and the last few OSes are gonna fall completely past that 120gig / 137gig region (( since the two Win partitions account for around 100gigs, give or take ))

my BIOS is relateively new, probably no more than a year or two old, so i'm presuming that i can ignore that whole 120gig / 137gig issue (and that GRUB error 18 that HermanZone mentions)


... still slightly confused ...


ok, quick question - how can i check whether my BIOS is susceptible to that 137gig limit?  is there some setting i can check in BIOS, or should i just try to install the first linux OS into the very furthest partition and see if stuff still works?

---

### Post by louieb on 2007-11-20
Option2 +1. Thats how I do it on my P2-400mHz playbox computer. Distributions come and go on it regularly. But its only has a 30 gig drive for Linux and XP is on the 2nd 8 gig  drive. Since its an older slower PC I play with light weight distros on it. To give you an example heres how its set up.
[LIST=1]
[*]GRUB boot loader only 23 MB
[*]Linux distro 5GB
[*]Linux distro 3GB
[*]Extended
[*]Linux distro 2GB
[*]Swap
[*]stuff I want to keep/share between distros (wallpaper, music,  configuration files, ...) 18GB[/LIST]The GRUB menu in partition 1 contains configfile and chainloader entries for the 3 Linux partitions.  
When I install a new distro on one of the partitions I have the installer put GRUB in the boot sector of that partition. Then on reboot select that partition and see what happens. 
 

 
As far a testing for the GRUB 18 error, the only way I know to do it is install a distro in the neither region of the drive and see what happens.

---

### Post by bluepowder7 on 2007-11-20
well, looks like no matter which option i choose, there's ways of moving files around and editing the fstab to keep things working.  got ubu installed on an earlier partition for now, with /boot and grub in that 240meg chunk up front.  gonna have to re-read that HermanZone thing a few times to fully understand what needs to be done when the next OS comes up.

hmm, i don't particularly like how GRUB looks / works right now.  it looks like it presents me with the linux kernels and the windows loader, but my win2k and winxp aren't part of that first GRUB screen - i have to go to the separate loader to pick between 2k and xp.  is there any way of getting ALL the OSes onto one screen?  i'm thinking there's bound to be a time when i walk into the windows loader screen only to realize that i'm supposed to be booting into linux, and there doesn't appear to be a way to backtrack to the first GRUB screen.

---

