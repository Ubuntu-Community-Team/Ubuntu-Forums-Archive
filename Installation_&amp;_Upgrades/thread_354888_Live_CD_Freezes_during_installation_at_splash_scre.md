---
title: "Live CD Freezes during installation at splash screen"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Billtg on 2007-02-06
I'm currently running XP pro but want to give Ubuntu a try, so I got the live CD (6.10) and started it up. It seemed to be running fine, but then just before the progress bar gets to the end, it suddenly freezes and I get some weird green pixels across the screen. When I try using safe graphics mode, I get taken to an error screen telling me that no screens are found.

Current Hardware:
**Processor** - AMD Athlon 64 3700+
**Video Card** - ATI Radeon X800 XL
**Motherboard** - MSI K8N Neo4 Platinum

Looking around the board I found a common solution was this:

Press F6 at the menu
Delete "quiet - splash" from the command line
Add "break = bottom"
At Command line type "chroot /root nano etc/X11/xorg.conf"

I did the first three and was brought to a command prompt with "initramfs>" then typed in the command, but it came back with an error saying:
chroot: Cannot execute nano: no such file or directory exists

I have tried with both the 64-bit CD and the i386 CD with no success. If you have any suggestions which may help they would be much appreciated. Solutions which don't involve burning another CD would be preferable, but don't let this hold you back if you are brought to this conclusion.
Thank you.

---

### Post by strygning on 2007-02-06
I got the exact same problem.

Tried burning another disk at 8x with no luck.

Im on DFI NF4 Ultra-D, Opteron 146 and ATI X800GT.

---

### Post by Arical on 2007-02-06
Mine is also doing the same thing. When I removed splash quiet, it showed me what was going on. After it said loading scsi is when it all went bad. Error after error of 

ID: failed opcode was: unknown I/O
end_request: I/O error, dev hdd, sector xxxx
buffer I/O error on device hdd, logical block xxxxx

Any ideas? I did an MD5sum on the media before I burned it and that turned out alright. However I can't even complete the media integrity test on here without it freezing.

Edit: I also know its not the CD on mine, as I can load it onto my laptop just fine, it just won't load on my desktop. 

My desktop is a P4 3.0 prescott
1gb DDR3200 ram

---

### Post by eapache on 2007-02-06
Billtg and strygning: try making sure that you type the command in correctly. That error sounds like what it would give you if you forgot the space between nano and etc/X11... but if you both got it, that's kind of weird. sounds like bad cd, but I really have no idea.

Arical: you have a bad hard-drive of some sort. Try checking your Scsi configuration and connections. If you don't actually have scsi drives, then it's detecting it wrong, and you'll have to configure the drivers manually (I have no idea how, but there's bound to be a site out there somewhere). If you have another os on the drive(s), make sure it's working. If you have no data on the disk, try reformatting it (use gtparted: [here]("http://gparted.sourceforge.net/")).

---

### Post by Billtg on 2007-02-06
> **eapache said:**
> Billtg and strygning: try making sure that you type the command in correctly. That error sounds like what it would give you if you forgot the space between nano and etc/X11... but if you both got it, that's kind of weird. sounds like bad cd, but I really have no idea.

Thanks for the advice but I'm quite sure I've typed it in correctly as I've tried many variations of spaces and different words removed. As for the bad CD idea, I suppose it's possible but it seems odd that it would happen on both CDs as well as on other users' CDs. The advice is much appreciated though.

---

### Post by robindc on 2007-02-06
Sounds very similar to the issue I am having with 6.10 Desktop and Virtual Pc how do you 
modify the graphics setting if you cant complete an installtion ?

---

### Post by theopye on 2007-02-07
I had the same problem- this did the trick for me:

When booted into the Live CD Desktop; under the menu, navigate to "System > Administration > Services"

Find a service called "CPU Frequency Manager (powernowd)" and uncheck the service, this will stop it from running.

I hope it works and good luck! :)

(All of my errors were pretty inconsistent, except for stuff crashing... one thing I ran into was something like you posted.)

---

### Post by aberry5555 on 2007-02-07
if nano isn't installed maybe you could install it using apt-get, or use another text-based ASCII editor, though off the top of my head I can't think of one :S

try running "apt-get install nano", though I don't know if, at this stage of startup, you will have network processes to do it. If this doesn't work, boot up as "normal" until you get the error message, then press ctrl+alt+F1 to bring up a terminal and then try and get nano, then follow the steps before hand to get it working.

---

### Post by Nicepen on 2007-07-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I found this article related to the problem we are having.  Might be to late for some of you but I'm sure someone will come along and use this.  

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

