---
title: "Installation Blank Screen"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by mikeglaz on 2007-02-01
I am trying to install Ubunutu on my second partition.  I select Start Installation after the CD boots.  Then the Ubuntu logo appears with the progress bar.  Afterwards the screen goes blank and the CD stops spinning and nothing happens.

I tried hitting F6 and typing **break-bottom**.  Then I see all this text scrolling and it hangs on this line:

**VFS: Cannot open root device "<NULL>" or unknown-block(8,1) Please append a correct "root=" boot option kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)**

I have the K8V SE Deluxe motherboard with Promise FastTrak 378 Disk Controller which requires loading a SATA driver for it during Windows XP installation (by pressing F6 after the WinCD boots).  I was thinking that maybe I might have to do the same for Ubuntu ... although I did install openSUSE without any problems.
I also have the ATI Radeon 9800 video card if that helps.

Any ideas??

---

### Post by KillerBob-it on 2007-02-02
do you have a TV card?
I have the same problem with my TV card, I must unplug it from the PCI slot to boot into Ubuntu/Kubuntu (both 6.06 and 6.10).
No problem with openSUSE

---

### Post by mikeglaz on 2007-02-02
Nope.  No TV card ...

---

### Post by pixxels on 2007-02-05
I'm having the exact same problem right now.  I started by trying to boot from the edgy DVD.  I'm now downloading the desktop CD and the alternative CD to see if one of those will help.  Looking around the forums it sounds like 6.06 doesn't have this problem.

I'm going to try the suggestions in [this]("http://www.ubuntuforums.org/showthread.php?t=302136&highlight=k8v+se+install") thread also.  


-scott

---

