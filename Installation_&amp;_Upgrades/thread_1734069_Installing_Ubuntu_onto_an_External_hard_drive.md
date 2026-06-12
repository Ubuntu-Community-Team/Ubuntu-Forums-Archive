---
title: "Installing Ubuntu onto an External hard drive"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by TacticalApe on 2011-04-19
So a few days ago I tried to do this and something went wrong, and caused so much trouble that I decided I didn't want to do it at all. Then I changed my mind today, and decided I'll try again even after all that happened. (I don't want this to happen again:[http://ubuntuforums.org/showthread.php?t=1731750) ]("http://ubuntuforums.org/showthread.php?t=1731750")
So can anyone link me to a tutorial or post one? because I don't really know what to do.

---

### Post by Dutch70 on 2011-04-20
From your other thread, it looks like you know how to install it. My advice is to unplug your windows hdd during the install. After you get it installed and verify that it's booting ok. Hook up your other drive, boot into Ubuntu and run...
```
sudo update-grub
```

You may have to hit the escape or F12 key or whatever it is on your computer & select your ehd to boot Ubuntu with your other hdd plugged in.

---

### Post by TacticalApe on 2011-04-20
I can't unlplug my windows hdd, because windows is installed on the computer and the only thing I'd unplug would be the EHD that I'm installing ubuntu to.

---

### Post by oldfred on 2011-04-20
You then have to use manual install, and either partition in advance or as part of the install. With manual install you get the choice on where to install grub2's boot loader which you have to install to the external. Then set external as first to boot in BIOS.

Lots of detail, not as complex as it may seem as Herman explains just about everything.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Dutch70 on 2011-04-20
> **TacticalApe said:**
> I can't unlplug my windows hdd, because windows is installed on the computer and the only thing I'd unplug would be the EHD that I'm installing ubuntu to.

Windows being installed on the hard drive does not prevent you from unplugging it. In fact, unplugging it protects windows. Hence, the reason I advised you to temporarily unplug/disconnect it.

What I meant is disconnect your internal hdd, install Ubuntu to your ehd, then reconnect your internal hdd. I have windows on one hdd, and nearly 10 OS's on another. I unplug my windows hard drive every time I install an OS. You don't have to, but it leaves much less room for error.

---

