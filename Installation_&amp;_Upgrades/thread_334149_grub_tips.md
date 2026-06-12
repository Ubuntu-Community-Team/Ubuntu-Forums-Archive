---
title: "grub tips"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by goodfella on 2007-01-08
This post describes my experience installing windows xp on its own drive after having installed ubuntu.

**PROBLEM** ](*,) 
I just recently had to install windows xp professional 32 bit on a seperate hard drive because some of my hardware and software refused to work on my windows xp pro x64.  Namely Topo 4.0 and my pci serial port card.  Topo 4.0 under xp x64 gave me an "unknown application error" and my pci serial port card only has a 32 bit driver and therefore will not work with xp x64.

I allready had ubuntu 6.06 installed and was booting fine with grub into either ubuntu or xp x64.  I read a post that to install ubuntu on a seperate drive you just need to set the drive you wish to install linux on to the first bootable hard drive drive in the bios [instructions]("http://www.ubuntuforums.org/showthread.php?t=179902") .  I figured that the same would work for windows.  Unfortunately it didn't.

I set my windows drive to the first bootable hard drive.  The second bootable hard drive was my ubuntu drive.  I then ran the windows install and when it finished I set the first bootable drive to my ubuntu drive.  Much to my suprise, instead of grub loading, windows xp started to load.  Windows, instead of changing the mbr of the drive it was installed on, changed the mbr of my ubuntu drive.  I have no idea as to why this was the case, but I was in a panic.

**SOLUTION** :D 
So I pulled out my live cd from which I installed ubuntu and started up ubuntu from it i.e. the first option.  All I had to do to fix the problem was type the following command in the terminal:
```
 sudo grub-install --root-directory=/dev/hdb2
```

/dev/hdb2 is the drive and partition where ubuntu is installed.  This little command got me back to where I was with ubuntu and now I am able to boot into windows xp x64 and windows xp 32 bit.  I wish I only needed windows xp x64 but it's not a perfect world.

---

### Post by groggyboy on 2007-01-08
I like it when people post their own solutions for problems!

There's a wiki page [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") with more ways of fixing errant GRUBs (usually because of Windows :evil: ) if you're curious.

cheers!

---

### Post by goodfella on 2007-01-08
thanks for the link.

---

