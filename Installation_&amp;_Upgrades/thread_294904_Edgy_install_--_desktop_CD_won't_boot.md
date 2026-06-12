---
title: "Edgy install -- desktop CD won't boot"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by Kensey on 2006-11-07
This morning I burned a desktop CD for edgy, and tried to boot it on a Dell Optiplex GX110 (old PC I have at home, runs XP fine).  The CD booted to a menu, but when I tried to boot with the default option, I got a weird behavior: a line of little rainbow-colored dots appeared across the middle of the display, like the beginning of a dissolve effect, then everything stopped dead.  I rebooted and tried again with the same result.

I haven't tried it on another PC yet, because I'm using 6.06 LTS on my laptop and don't want to monkey with that, my other desktop PC is the house fileserver, my wife doesn't want me monkeying up *her* laptop :twisted: , and we're fresh out of other PCs.

I'm taking it to work today to try it on my desktop there, but if it fails there too, is this probably a bad CD burn, or does edgy's installer have particularly demanding graphics requirements in some way?  And if it succeeds there, how can I get it into a useful mode at home where I can do an install?

---

### Post by taurus on 2006-11-07
Try using the alternate CD then.  By the way, it's not going to screw up your laptop or your desktop just from booting the desktop CD.  Since it's a LiveCD, it will run the whole OS from the CD...  And don't forget to burn it at a slow speed like 4x.  Fast burning CD sometimes can cause booting problem with Ubuntu.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by Kensey on 2006-11-07
What's the difference between the regular and alternate CDs?  Is there a way to tell in advance which I should use for a given install?

---

### Post by Dragineez on 2007-01-22
> **Kensey said:**
> What's the difference between the regular and alternate CDs?  Is there a way to tell in advance which I should use for a given install?You don't say how much RAM is in that machine, but the alternate is good for machines with less than 192MB or RAM - or doing server installs - has text mode installer.

I'm dealing with the same problem. Live CD and install won't work on this machine. Everyone will tell you it's a bad burn. It's probably not. The machine is failing to mount the CD. I haven't worked around this yet, but I've heard multiple suggestions that it's the built in video, which share/steals system RAM, that may be the culprit. If possible, try:

boot: live pci=noacpi ide=nodma noapic nolapic aic78xxx=no_probe

That got me ***close*** but I'll have to try again tonight. I want to play with BIOS settings for the video as well as trying the install in VESA safe mode.

---

### Post by justaguynpc on 2007-01-23
I have never had any success with install via livecd, and I have 2G of ram.  As it goes, never had any problem installing from the alternate cd though.

Just my $.02 worth......................

Cheers

---

