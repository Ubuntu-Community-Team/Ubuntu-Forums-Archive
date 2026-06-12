---
title: "Ubuntu /bin/sh tty error no piix modual"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by MunchySnacks on 2007-12-12
I am trying to get Ubuntu up and running but have had some problems. Sometimes I can  get the live cd to start sometimes not. It seems ejecting the drive and putting it back in helps while it booting. I got a version of Knoppix to try and get that to work it works fine except sometimes on trying to find the boot image on boot I have to eject the disk and reinsert it before it errors out. I am guessing these are all related but the biggest problem is I got Knoppix to install and boot but "got the /bin/sh can't access tty: job control turned off" error. I tried the modprobe piix command by the boot options and break=top. It returns piix modual not found. This is all off the Ubuntu live cd and Knoppix Cd that I tried this both said the same thing. I don't know if i need to install piix or what but any help would be appreciated.

My hardware is (as best as I can remember this tired)
Athlon 64 fx-55
2x 7800 GTX Nvidia 
150 Gb SATA drive Western Digital
500 GB SATA drive Seagate Baracudda
2 GB Ram
Plextor DVDRW

---

### Post by Thanoulis on 2007-12-12
Seems like your PlextorCD has the problem...did you try with another?

---

### Post by MunchySnacks on 2007-12-12
I think you might be right I can get it to boot with a secondary drive that is set to slave right now. Would disconnecting and setting my secondary to master help?

*Edit*
I disconnected the primary Plaxtor set my secondary drive up as primary and got the same msg on boot for linux of the bin/sh error. Did seem to boot better thought on knoppix just not on Ubuntu.

---

### Post by MunchySnacks on 2007-12-13
I have Ubuntu installed to HD now. I had to remove my Plaxtor DVDRW set my secondary cdrw drive to master. Then I had to format the partitions in reiser and after I had those reformatted in reiser (ext3 and ext2 would not format kept getting errors) I could get it to install thanks for the help though helped part of the problems I was having.

---

