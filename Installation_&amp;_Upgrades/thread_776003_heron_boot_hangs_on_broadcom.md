---
title: "heron boot hangs on broadcom"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Vetto on 2008-04-30
I just upgraded kubuntu 7.10 to 8.04 official and after the reboot the system hangs at the splash screen (I have no grub problems).

When booting in recovery mode, I see that it is hanging up on the internal broadcom card.  I have seen some threads where network-manager is not upgrading well?  My network is/was configured manually via kde-network-manager so that the cards would startup upon boot because I have nfs mounts.

Has this been seen before and how was it fixed?  new broadcom drivers?  reinstall network-manger?  scrap it all and do a fresh install vice the gone-awry upgrade?

related thread?? [http://ubuntuforums.org/showthread.php?t=772967](http://ubuntuforums.org/showthread.php?t=772967)

---

### Post by Vetto on 2008-04-30
Fixed it myself...sorta

There is a problem (documented in various bog trackers for ubuntu and bugzilla) with the broadcom 4301 chip and the .24 kernel that ships with Heron marked as high.  (Not mentioned in the installation notes I might add...:mad: )

The fix was to boot into single user mode with the older kernel still listed in my grub menu, then edit /etc/modprobe.d/blacklist adding the following two lines:
```
blacklist b43legacy
blacklist bcm43xx
```

Now that will initially disable the card on boot, but supposedly you can use it after with by modprobing it.  (wierd)

I have a pc card wifi adapter, so I dont use the BCM card anyway, so I will leave it that way for now.

Fresh upgrade from CD would still fail with this problem, bad bad maintainers for releasing with this "high" category show-stopper out there and not mentioning it in the installation notes (or somewhere).  Unfortunatly, the average user will not be able to fix this easily adding to the fodder of the "not ready for the masses" sheeple.

---

