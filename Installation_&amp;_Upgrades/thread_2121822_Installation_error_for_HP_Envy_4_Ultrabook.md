---
title: "Installation error for HP Envy 4 Ultrabook"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by pete35 on 2013-03-03
I have a HP Envy 4 ulrabook with windows 8 and SSD. 

I'm trying to follow the steps given in this thread [http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450).

I have disabled secure boot & Intel rapid smart technology from the BIOS. When I try to install using a Live USB, for the screen to select the "Installation type" I get a error saying **"Sorry, Ubuntu 12.10 has experienced an internal error"**. On selecting the show details option it shows the executable path as "**/usr/lib/ubiquity/bin/ubiquity**". In this "Installation type" selection screen I do not get any option to select device or partitions. All options are disabled. 

Thanks.

[ATTACH=CONFIG]239691[/ATTACH]

---

### Post by oldfred on 2013-03-03
Did you remove RAID meta data from drive? Intel is standard with all computers, so difference should be small.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

Also:

 There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)

---

### Post by pete35 on 2013-03-05
Thanks. It worked. I removed the RAID meta data and installed it. Had to do a boot repair since it was booting directly to Windows 8.

But Wifi routers are not being detected. It connects when I use a Ethernet cable, but not wifi. Any suggestions for this? 

Thanks.

---

### Post by oldfred on 2013-03-05
I do not know wifi driver issues. 

From Ethernet connection does it offer to load new drivers from system settings?

Otherwise search forum for your model wi-fi, there are already many threads. Or start a new thread with model in title.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post a reply here and attach (via the paperclip) the abs-network.txt file which will be in your home folder.

---

