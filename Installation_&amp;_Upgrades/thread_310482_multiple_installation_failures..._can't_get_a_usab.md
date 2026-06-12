---
title: "multiple installation failures... can't get a usable ubuntu install going"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by superchode on 2006-12-01
my system:

AMD 4400+, 1gig RAM, nvidia 6600GT. windows partition on sda, installing ubuntu on sdb.

i've had many goes at this, so bear with me as i run them down:

breezy badger (amd64): 
install progresses, but fails late in the process with the screen scrolling matrix-esque garbage in an infinite loop.  i can actually reboot and get into the ubuntu install after this, but certain things are broken - and updating the distribution doesn't work properly and furthur breaks the install.

6.06.1 (dapper) and 6.06.10 (edgy) amd64 and 6.06.1 (dapper) i386:
install never even starts properly. begins install, seems to attempt to display a GUI... perhaps it's a GUI install on this version... but it's so garbled that i can't see what's going on and can't continue.  i thought this problem was due to the boot/install option the cd gives and that it was booting a bad ubuntu install that existed on sdb instead of installing clean.  i used a liveCD to go in and remove the bad install (fdisk) - and got the exact same result when loading up the above CDs again.

6.06.1 (dapper) amd64 alternate install CD:
installs (OEM mode) just peachy... no errors, completes - but on reboot the display is garbled and unusable.  it appears as if things are working underneath, but i don't know what it's telling my videocard to display - something is seriously wrong there.

when i can finish an install, grub gets installed properly and works well - letting me choose my windows or ubuntu partition.

the strange thing is that the liveCD works just fine (breezy is the only one i had handy and therefore used). can boot up and use it no problem... so it seems like ubuntu should be able to handle my hardware... yet the problems persist.

please help me to sort this out. i would very much like to learn and love ubuntu... but it's not, as of yet, contributing its fair share into the relationship.

---

### Post by Ashrael on 2006-12-01
check all your partitions for bad blocks etc. Also do not use 6.10, it's not quite stable yet... Also, grub should be installed on your first (windows) drive, and told that ubuntu resides on hdb...
Especialy the diskcheck is important......

---

### Post by superchode on 2006-12-01
disk is in fine shape, grub is working properly... loaded into the mbr of hda and boot up ubuntu on hdb no problem.

i think the problem may be related to this thread:

[http://www.ubuntuforums.org/showthread.phpt=287526&highlight=nvidia+garbled](http://www.ubuntuforums.org/showthread.phpt=287526&highlight=nvidia+garbled)

is this a common/known ubuntu problem?

---

