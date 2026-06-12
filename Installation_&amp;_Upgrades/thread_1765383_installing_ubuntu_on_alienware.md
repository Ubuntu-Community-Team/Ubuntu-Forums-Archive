---
title: "installing ubuntu on alienware"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by chris1497 on 2011-05-23
I'm trying to install ubuntu or any linux on my alienware and I am having difficulties.

Its an intel core 2.

I've made an ubuntu 11.04 live cd for 64 bit.  When I boot into the cd it starts up and I get a desktop, mouse and the upper task bar with just three icons: power, network, and something else.  I can't click any of these icons or do anything else useful.

I've also tried running live disks of Suse and Fedora.  Neither one works either.  I got an error on one of them saying unkown file system.

I'm running windows 7 currently installed on the C drive. then I have another partition for my files.  At one point I've upgraded the RAM on it, but I bought it directly from dell and have had no problems in the 2 years running windows.

---

### Post by linuxinstalledfromhdd on 2011-05-23
Try using 10.10 32-bit and see if that makes any difference.  Try creating a Live USB Bootable Drive to install it.

---

### Post by chris1497 on 2011-05-23
I believe I tried 10.10 once before on the alienware and it wouldn't even get as far as the desktop.

I'm assuming you suggest 10.10 because it is more stable? or is there another reason?

---

### Post by linuxinstalledfromhdd on 2011-05-23
Did you try it with 32-bit verses 64-bit?  It can make a difference sometimes.

---

### Post by chris1497 on 2011-05-23
i tried the 32 and 64 bit versions of ubuntu 11.04. neither worked.  I'm currently downloading the 32 bit version of 10.10 to make a live cd out of.

---

### Post by chris1497 on 2011-05-28
ok. tried that. I get a desktop and a movable mouse. no top or bottom task bar.

I have now tried live cds of the following and none have worked.

ubuntu 11.04 32 bit
ubuntu 11.04 64 bit
ubuntu 10.10 32 bit
ubuntu 10.10 64 bit
fedora 14
suse 11.3
suse 10.something
and an earlier version of fedora

The only readable error I have gotten is from suse. Said something about an unreadable file system.  All of the others have just hung at some point during the live cd boot.

I currently have windows 7 installed.  There are two partitions. The OS is on one and the other one is used for data. Is there anyway this could be a problem?

Is there any reason the hardware wouldn't be supported?  Its a stock alienware that I bought 3 years ago.  The only change I have made is updating the ram, which I bought directly from dell to make sure it was compatible.  To reiterate, the alienware is an intel core 2 duo, 4 gigs of ram, 160gb HD, dual sli nvidia graphics cards. not sure about the mother board, could figure it out if its necessary

---

### Post by chris1497 on 2011-05-29
solved.

installed within windows.  then booted into the recovery mode. installed the driver for nvidia card before it would boot into graphics mode properly.  spent several more hours tyring to get the resolution set back to the native 1900x1200.  messing around with the xserver and config files and manually downloading drivers off the nvidia site. rebooted to complete an install of something else and my resolution was fixed. not even sure what did it.

only reason I went through all this is because I have linux on another computer so I've already experienced it.  If I were thinking of switching over from windows for the first time I would've given up several days ago... Thats kinda a problem if ubuntu is trying to challenge windows.

---

