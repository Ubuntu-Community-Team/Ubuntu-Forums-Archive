---
title: "cannot install feisty running out of ideas"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by stevexprebellion on 2007-06-08
Hi,
I am trying to escape microsoft and I am a definate nembie although very experienced with windooze. I tried to install both the live cd and the alternate version with no success. Here are the things I have tried so far. By the way I am runnig an old dell laptop with only a 266mhz cpu and 256mb ram 20gb hd though.

1. run live cd - system hangs after detecting cdrom stage of installer. blue screen with white bar and no activity even after several hours.
2. run alternate cd - system returns errors about cdrom in loading stage of installer various block errors then stalls.
3. installed on anther system (with laptop hard disk) hoping that transfering hard disk back to laptop will run auotdect for new hardware like ms xp does. Installations worked on the other system but once back on laptop I get x server error. Ran x server cnfiguration tool and it found my laptop graphics chip ok saved then reboted same problem. 

Please help (with idiot instructions if possible;)

---

### Post by uburiver on 2007-06-08
I have been having the same problems with a used Dell Latitude C640 that I just picked up.  I found a post on a different forum that addressed the issue, but a few of the users were reporting fixes after turning off the floppy drive (not my situation), or swapping in a CD-ROM drive (I don't have one to swap).  Users were reporting that they suspected that there is a problem installing using combo drives.  I tried changing the BIOS to boot off of a USB stick that I had loaded with the .iso, but I could not set the USB drive as bootable.  I am hoping to hear some good tips in response to your request as well.  Here is the other post that I mentioned:  [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)  The most relevant discussion is near 2007-04-22

---

### Post by stevexprebellion on 2007-06-09
thanks for sharing that. I checked the references and i see i am not alone. I tried plugging a floppy drive into my laptop in case that was all I needed to do and it made no difference. Like you I cannot change my CDROM drive aas it is a laptop. There are no options in my bios to boot from USB. Maybe I could try booting from floppy and installing from a seperate hard disk partition, perhaps someone could advise me how to do it in idiot english ;)

---

### Post by uburiver on 2007-06-10
Last night a found of download site with the latest distribution, 7.10.  I downloaded the edubuntu distro, but it should work the same as the ubuntu one.  I created the LiveCD same as before, using disk utility on a Mac, only this time it installed just fine on the Dell Latitude C640.  Perhaps there was a bug in the current distro that was fixed??  Whatever the reason, it works.  I found the download at softpedia: [http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Gutsy-Gibbon-27851.shtml)

Note:  it seemed to have in initially CD stall, but then it kicked in and ran the OS from the CD.  You can then choose to install.

good luck.

---

### Post by DoubleR on 2007-07-01
I installed 7.10 tribe1 Ubuntu on my dell laptop c640 last night and was successful.. I had to install twice.  I think the first install had some trouble because of the way I partitioned.  I am dual booting and the original 20gig drive is getting crowded.  Second attempt went very well.

---

