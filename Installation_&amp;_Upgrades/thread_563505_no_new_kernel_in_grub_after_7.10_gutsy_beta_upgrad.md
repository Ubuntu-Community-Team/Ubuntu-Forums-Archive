---
title: "no new kernel in grub after 7.10 gutsy beta upgrade"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by raydar on 2007-09-30
I tried an upgrade from Ubuntu 7.04 to 7.10 beta and all was well until the restart:  Grub does not list the new version, and when I try to boot the kernel I had been selecting before the upgrade, I can get no further than

Starting TiMidity++ ALSA midi emulation    [OK]

before a video setup box (showing 2 monitors, test/select video card & monitor type, but only working for the main monitor)  comes up and, after I tinker with the settings or not, restarts X then comes right back.  

I see the list of steps being gone through during the boot, the box appears, I click cancel or ok, I see the boot steps list several times briefly while resolutions are being tested (the screen blinks out repeatedly, in any case), and when the gui comes back, I'm back at the video setup box with default settings.  I've thus had to restart w/the button on the case; no key combos work and I can't get past the box.

I had seen, in the upgrade terminal window, something go by about grub or potentially needing to re-run a boot configuration utility.  I tried update-grub, but nothing new showed up in the operating systems list at boot.  I'm figuring it was supposed to; was my grub list already "full," via some limit, when I did the upgrade?  Any idea how I can boot the upgraded (beta) version that installed successfully before the requested reboot?

---

