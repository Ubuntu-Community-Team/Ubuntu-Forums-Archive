---
title: "Very Slow Live CD"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by LoREZ on 2010-06-27
I'm looking at installing Lucid on my main machine, which currently runs a dual-boot of Karmic and Win7 flawlessly. I've already done it inside VirtualBox several times with no trouble on this same machine.  When I startup on the live cd, this is what happens:

[LIST]
[*]4:30 minutes before progress bar stops
[*]@ 5:55 background comes up
[*]@ 7:09 install dialog pops up
[*]@ 7:22 install dialog is usable
[*]52 seconds later I get a mouse pointer
[*]2:30 minutes after that the Gnome panels show up
[/LIST]

The whole thing takes around 11 minutes, roughly, and it is slow to launch programs and draw menu icons after that, but the mouse is still snappy.  Kubuntu Lucid live cd doesn't boot at all for me.  However, Linux Mint 9 live cd, based on Lucid (so I hear), boots to a usable GUI in like two or three minutes.  Any clue what might be happening here?  With this sort of behavior in the live cd, I hesitate to install 10.04.

These are my system specs:

[LIST]
[*]Core i7 860
[*]8 GB of RAM
[*]500 GB Western Digital Caviar Black HDD
[*]Gigabyte P55-UDP4 Mobo
[*]NVIDIA GeForce GTX-260
[*]A few TBs of external USB and eSATA drives
[/LIST]

---

### Post by wilee-nilee on 2010-06-27
Hit esc or shift at booting cd and choose test cd, and also run a md5sum on the ISO, and cd. Burn another at slowest speed possible usually 4x if needed. You could use a thumb they seem to load faster.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by LoREZ on 2010-06-27
First, thanks for your reply!

The checksum on the file is good.  I reburned as you instructed and checked the integrity, which was good, but the disk still took 11 minutes to boot.  I used a flash drive, and that worked flawlessly and with increased speed over even the properly working live cds.  That's good, but it leaves me with a mystery that troubles me, because it could come back to haunt me:  Why would Ubuntu 10.04, and only Ubuntu 10.04, behave that way on my system?  Any ideas on BIOS settings that might effect drive performance in the context of Ubuntu distros?  It's just weird.

---

### Post by wilee-nilee on 2010-06-27
> **LoREZ said:**
> First, thanks for your reply!

The checksum on the file is good.  I reburned as you instructed and checked the integrity, which was good, but the disk still took 11 minutes to boot.  I used a flash drive, and that worked flawlessly and with increased speed over even the properly working live cds.  That's good, but it leaves me with a mystery that troubles me, because it could come back to haunt me:  Why would Ubuntu 10.04, and only Ubuntu 10.04, behave that way on my system?  Any ideas on BIOS settings that might effect drive performance in the context of Ubuntu distros?  It's just weird.

If you have the externals plugged in when booting the live cd I suspect those are the culprits. The thumb should ran faster as it does as it is like a ram stick to some extent. Unplug everything and try the cd again if you have the terrabyte external plugged in. Not sure why this is Lucid specific and only you know whats in the bios.

---

