---
title: "Can't boot due to wireless"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by microUgly on 2012-07-28
I've been trying to install 12.04 on an older Compaq laptop.

Originally, the demo and installer loaded fine, I was able to load to this screen quite a few times.  But the wireless wasn't working so I didn't have internet access.  No worries, I plugged a network cable, at wich point the GUI froze.  From that point on, I could no longer load the demo/installer.  It just froze on the animated dots.  Even after unplugging the network cable and disabling wireless in the firmware.  I have no idea how it loaded a few times and then would load ever again.

So I downloaded the alternate installer which installed fine.  But now Ubuntu is installed, it still won't boot--it just gets stuck on loading screen with the dots.

I've tried loading from recovery mode and it stops after displaying:
> b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefireware](http://wireless.kernel.org/en/users/Drivers/b43#devicefireware) and download...I believe this was the same issue preventing the installer from loading--I disabled quiet to see what was going on and it got a little further than this before stopping. 

I've found the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for updating the firmware, but I don't know how to get Ubuntu to boot so I can perform these steps.

It's driving me crazy because I don't care if it doesn't load the wireless hardware.  I actually have wireless disabled in the BIOS so I'm surprised it's even aware of the hardware.  Is there a way to tell it to start up without attempt to load wireless?

Any help would be much appreciated.  I've been trying to try Linux for over a decade.  But I always give up because these problems always occur and suck up so much time that eventually I have to be rational and switch back to something that does work--and then try again in 12 months :)

---

### Post by microUgly on 2012-07-29
Woohoo, I got it!  I'm just not fluent enough with Linux to have discovered it earlier.

I'm not sure how I would have solve this in terms of getting the standard installer to load, but using the alternate installer I was at least able to get Ubuntu installed to then have an installation to fix.

So for others in my situation, you need to boot into recovery mode then "Drop to root shell prompt".

From there, you must remount the filesystem as read/write:
```
mount -o rw,remount /
```

Then follow the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

Note that there is no patch files to install with 12.04 (mentioned in the later part of step 1).

---

