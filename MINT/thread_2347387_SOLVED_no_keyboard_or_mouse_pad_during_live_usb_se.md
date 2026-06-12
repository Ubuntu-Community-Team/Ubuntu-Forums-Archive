---
title: "SOLVED no keyboard or mouse pad during live usb session"
date: 2016-12-24
forum: MINT
---

### Post by stimpeh on 2016-12-24
Solved: I am an idiot...Changed to USB FDD as boot device (instead of USB HDD), working fine now...



Hi all,

I thought my problem was related to the distribution I wanted to test, Linux Mint Xfce, so I'll post the original post(s) from linux mint forum, basically my problem is that in any live session (tried multiple distributions) my keyboard and mouse pad don't work in the live session....hope you guys can help me...

by [Stimpeh]("https://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=103050") » Sat Dec 03, 2016 12:45 pm
Hello,

I'd like to migrate from Cinnamon 17 to Xfce 17.3 on my laptop but when launching live USB neither keyboard nor mousepad work in the live session.
I've succesfully installed from same live USB on same computer in Virtualbox, so the installation USB is OK.

I've sometimes experienced no keyboard or mousepad functionality on boot, with Cinnamon...simple reboot would do the trick.

Computer is a Acer Aspire 7250 with AMD Radeon 6310 Graphics (Catalyst and stuff always giving trouble...graphics is not top, but that's another story).

how to proceed?

Thank you


[RIGHT][Top]("https://forums.linuxmint.com/viewtopic.php?f=46&t=234819#top")[/RIGHT]



[Stimpeh]("https://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=103050")Level 1
[IMG]https://forums.linuxmint.com/images/ranks/1.gif[/IMG]Posts: [10]("https://forums.linuxmint.com/search.php?author_id=103050&sr=posts")Joined: Thu Dec 27, 2012 6:08 pmLocation: FranceContact: [Contact Stimpeh]("https://forums.linuxmint.com/viewtopic.php?f=46&t=234819#")
[h=3][Re: no keyboard or mousepad Xfce 17.3 live USB]("https://forums.linuxmint.com/viewtopic.php?f=46&t=234819#p1256352")[/h]
[LIST]
[*][]("https://forums.linuxmint.com/posting.php?mode=edit&f=46&p=1256352")
[*][]("https://forums.linuxmint.com/posting.php?mode=delete&f=46&p=1256352")
[*][]("https://forums.linuxmint.com/report.php?f=46&p=1256352")
[*][]("https://forums.linuxmint.com/posting.php?mode=quote&f=46&p=1256352")
[/LIST]
[Post]("https://forums.linuxmint.com/viewtopic.php?p=1256352#p1256352")by [Stimpeh]("https://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=103050") » Fri Dec 23, 2016 4:26 pm
*bump*

some more information with the hope of an answer.... [IMG]https://forums.linuxmint.com/images/smilies/icon_redface.gif[/IMG] 

inxi -Fxz output:

CODE: [SELECT ALL]("https://forums.linuxmint.com/viewtopic.php?f=46&t=234819#")
System:    Host: pieter-Aspire-7250 Kernel: 3.13.0-24-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Linux Mint 17 Qiana
Machine:   System: Acer product: Aspire 7250 version: V1.10
           Mobo: Acer model: HMA71_BZ Bios: Insyde version: V1.10 date: 11/02/2011
CPU:       Dual core AMD E-300 APU with Radeon HD Graphics (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 sse4a ssse3 svm) bmips: 5189.28 
           Clock Speeds: 1: 780.00 MHz 2: 1114.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Wrestler [Radeon HD 6310] bus-ID: 00:01.0 
           X.Org: 1.15.1 driver: fglrx Resolution: 1600x900@60.1hz 
           GLX Renderer: AMD Radeon HD 6310 Graphics GLX Version: 4.5.13399 - CPC 15.20.1013 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD/ATI] Wrestler HDMI Audio driver: snd_hda_intel bus-ID: 00:01.1
           Card-2: Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA) driver: snd_hda_intel bus-ID: 00:14.2
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-24-generic
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k bus-ID: 07:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Qualcomm Atheros AR8152 v2.0 Fast Ethernet driver: atl1c ver: 1.0.1.1-NAPI port: 2000 bus-ID: 08:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (47.1% used) 1: id: /dev/sda model: WDC_WD3200BPVT size: 320.1GB 
Partition: ID: / size: 290G used: 141G (52%) fs: ext4 ID: swap-1 size: 4.00GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 54.0C mobo: N/A gpu: 54.00C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 174 Uptime: 3 min Memory: 918.0/3679.6MB Runlevel: 2 Gcc sys: 4.8.4 Client: Shell inxi: 1.8.4 
 


I tried running compatibility mode, took ages to load (about 15 minutes) then gave me a weird distorted screen so had to reboot....
integrity check passed
memcheck i didn't go through all the way because it takes ages...


obviously I retried a live session but to no avail; i can just connect eternal mouse to be able to quit, however; one needs to press 'enter' to shut down after taking out USB, and since keyboard is not responding..... [IMG]https://forums.linuxmint.com/images/smilies/icon_lol.gif[/IMG] [IMG]https://forums.linuxmint.com/images/smilies/icon_rolleyes.gif[/IMG] 

edit: live session of 17.1 Xfce not working either....gonna try Xubuntu now...
edit2: xubuntu not working either, thought it might be something with kernel so tried an old mint cinnamon 14, not working either!!!! so yeah, I have a problem with keyboard and mouse(pad, usb mouse working fine) when in live session....will post to ubuntuforums as well in the hope of a solution....
someone posted something about enabling legacy in BIOS but I can't seem to find that option in my BIOS....


anyway...getting tired of slow cinnamon: plz help.

yours truly,

Pieter


[RIGHT][/RIGHT]

---

### Post by howefield on 2016-12-24
Thread moved to the "*MINT*" forum.

---

