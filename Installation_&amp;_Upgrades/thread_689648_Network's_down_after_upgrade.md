---
title: "Network's down after upgrade"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by last1 on 2008-02-06
So last night I did a little apt-get upgrade on my asus EEE pc running xubuntu. Now when I start up and look at the little network icon, it just says no network devices found, and doesn't give me that annoying prompt for my keyring password to get onto my wifi network. ifconfig only shows the loopback device as being present. What gives?

---

### Post by scaine on 2008-02-07
You're probably better off over at the eeeuser.com forums for this stuff, but I think the problem is that the latest updates are kernel updates, which breaks any custom stuff you might have installed to, say, get your wifi working natively under MadWIFI drivers.

I'm running Ubuntu standard on my Eee, but I've installed the custom kernel, so I'm just ignoring these updates for the moment until someone more technically adept does it first and posts their experiences!  This guy ([http://forum.eeeuser.com/viewtopic.php?id=13640](http://forum.eeeuser.com/viewtopic.php?id=13640)) mentions that all you have to do is re-install/compile your WIFI drivers.  That's fine for him, maybe, but it's an entirely new kernel I'm running to get my WIFI running, so that won't work for me.

Good luck with it though.  If you get a fix, please post it along!

---

### Post by last1 on 2008-02-07
Well, I just re-installed with the latest version of eeeXubuntu, so problem solved, I guess. After looking at it a little more I don't know if it even was a kernel thing, though the kernel certainly was upgraded. Not only was wifi not working, but also the wired network. I could plug in an ethernet cable and nothing would happen. Even went ahead and downgraded to the old kernel by putting the deb on a usb drive and transferring it over, but that didn't fix it either.

I wish I had been making regular backups with partimage or tried making myself a custom livecd with all the tweaks, cause i don't know about you but for me at least installing and tweaking it to be usable was a right pain in the @ss last time.

---

