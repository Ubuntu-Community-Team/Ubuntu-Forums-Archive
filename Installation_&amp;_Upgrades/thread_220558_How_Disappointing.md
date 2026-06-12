---
title: "How Disappointing"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by magog45 on 2006-07-21
I must say that I like Ubuntu 5.10 both the regular and X versions but 6.06 seems to be a loser. Trying to do a fresh install on an Asus P2BD with dual P3 800s and 512mb memory a 120gb samsung harddrive, soundblaster pci live 5.1, ATI radeon 7500 with 64mb, liteon CDRW and a realtek 8139 netcard has been frustrating. If the livecds even get past the linux kernel startup to a point where I have the system up and running(and its hit and miss) when I try to do the harddrive install it either freezes at various points 23%, 38%, 67% and as high as 97% or the installer crashes. I've reburnt the iso's checking the MDsum at each end. I'm not a newcomer to Linux, looking up on my shelf I see Redhat 5.2, 6.0 and fedora, also various releases of SUSE, Mandrake and Corel not to mention FreeBSD. The one thing they all had in common was the install was not as automated as Ubuntu and many of the newer distributions seem to be. Not a system problem I thing as Damn Small Linux now occupies the drive and is quickly getting fatter and it recognizes my 2 processors no problem which Ubuntu fails to do.

---

### Post by reacocard on 2006-07-21
try using the 'alternate' install cd. it may work better. and you need to install an smp enabled kernel to use dual processors. linux-image-2.6.15-26-686-smp is the package you'll need to install for that.

---

### Post by magog45 on 2006-07-21
I've tried every version of 6.06 desktop and alternate, it simply doesn't want to install and none of the install options really give you step by step control of the process. If I can't get the system installed it's pretty hard to update the kernel to the smp version. Thats why I mentioned Damn Small, its now installed on the dual processor system as well as an ancient Fujitsu Tablet PC and it had no trouble with either. If it is the kernel that is affecting the install then it is unlikely I will be installing 6.06 until they update the install CD, but I think it is more lkely that it is a problem with the installer as the freeze-ups are inconsistent, if it always happened at exactly the same place it would be easier to debug.

---

### Post by Kapre on 2006-07-21
Happened to me onetime (on 5.10) and was trying it till the wee hours of the morning. Since it is a CD from Shipit, I thought it will be free of defects (which it is) and the after three times of frustrated installation (would hang at 55% and 98%) I tried the "wiping" method. I wiped the CD and clean my drive with a dollar store cleaner and viola! Installation completed.

I hope the obstacle that happened to you won't prevent you from trying Ubuntu.

K

---

### Post by magog45 on 2006-07-22
I'm using Ubuntu as I type this, but it is 5.10 on and older P3 single processor box so there is much it is too slow to do. I had hoped to replace it with a faster dual processor box for DVD burning and such but I don't understand why the smp kernel wouldn't be standard in this world of dual core processors. Like I said in my first post there's Damn Small booting from a usb stick recognizing both processors and an ancient soundcard while Ubuntu freezes and/or crashes. If someone has a solution that doesn't involve an upgrade to the kernel after install(it won't install) I'm interested but less so as I configure DSL to my needs,

---

### Post by magog45 on 2006-07-27
The same system has now had FreeBsd installed as well as DSL, the most recent attempt with Ubuntu got to 92%-detecting hardware and then froze up. I am also getting occasional kernel panics on warm reboot but only with Ubuntu. The hardware is not unusual, I think a little more time by the community on the install procedure and a little less on updating to the next piece of cutting edge software would go a long way to putting Ubuntu on more desktops. Anytime you can kill a windoze PC that is a good thing right?

---

