---
title: "After 4 weeks still canot get  Compaq 615 to run"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by DavidLR on 2010-08-04
HI,
I've read as much as I can and have tried all sorts of "fixes" but I cannot get my Compaq 615 to run Ubuntu 10.4. I can get it to load sometimes by pressing F6 furiously, but left to itself, all I get is a blank screen - even the cursor stops flashing!
 
Does Ubuntu actually run on Compaq 615?
 
I've tried these versions:
 
Desktop
Netbook
Desktop 64 bit
 
I've formatted the hard drive twice (takes 8 hours each time!).
 
I've tried these extensions when loading the programme from CD (inserted before quiet splash)
 
xforcevesa
nomodeset
nomodeset xforcevesa
 
It was suggested that I post the output of  "lspci | grep VGA", but I have no idea what this is, or where to enter it, or when to enter it.
 
I'm an absolute beginner on Linux and I'm ready to return to Windows (despite the fact that I'm a strong supporter of open source). At least Windows runs, however much we may malign it.
 
Where to now?
 
Any assistance to get me up and running will be most appreciated.
 
David

---

### Post by desnaike on 2010-08-04
Sorry your having problems but it happens, I read a post that had linux mint 8 running on it and also check out these links hope you get sorted out.[COLOR=Red]It is explained here[/COLOR] : [http://bbs.archlinux.org/viewtopic.php?id=82052](http://bbs.archlinux.org/viewtopic.php?id=82052)

The explanation about the Compaq 615 is on the latest entry.

It is also mentioned here : [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/454268]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/454268")

---

### Post by lechien73 on 2010-08-04
Could you try booting with the desktop 64-bit edition, and inserting the "noapic" and "nolapic" boot flags, please? You can put these after "quiet splash".

Sorry it's causing you so many problems, it appears that many other distros have the same issue on that machine.

---

