---
title: "After upgrading to Lucid, my laptop no longer boots"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by brian.hillz0r on 2010-05-11
I just upgraded from Karmic to Lucid and my system will no longer boot. The upgrade completed without any error messages, but upon reboot, it hangs at the loading screen. I cannot start the system in recovery mode either. Same issue happens. To get to the command line, I've appended:

init=/bin/bash

to the kernel line in grub. I then remount so I have r/w access.

It appears to be an issue with udev. While the loading screen is "loading," udevd_work scrolls a bunch of stuff that's too fast for me to read (nor can I copy and paste it).

/var/log/udev isn't showing any recent errors, only messages from before the upgrade.

I've run out of ideas, does anyone have any suggestions on where to continue?

Thanks!

---

### Post by dino99 on 2010-05-11
probably an issue with the graphic chipset. If you can edit the sources.list, check that you only use genuine lucid repo, no ppa or third party activated, then : clean, autoclean, autoremove, update and:

sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

you may give some hardware info to googled around

---

### Post by brian.hillz0r on 2010-05-11
I have no third party or Karmic sources in /etc/apt/sources.list. I ran the commands you gave me, but they didn't appear to help.

Hardware specs: 

Intel Core 2 Duo 2ghz
Intel Integrated Graphics GM965
4GB RAM
250GB HD

I'd give the specifics, but I'm unable to copy and paste the output of lspci.

One strange thing, once the splash screen appears, all HD activity seems to cease per the HD LED. I can just let it sit there overnight and it never gets past that screen.

I had no issues with Karmic so this is kind of worrisome.

---

### Post by Catharsis on 2010-05-11
I doubt it'll help, but you can try editing the kernel parameters in grub:
1) Remove "quiet splash".
2) If that doesn't work, try replacing it with "i915.modeset=1".
3) If that doesn't work either, replace it with "i915.modeset=0".
4) If that still doesn't work: "xforcevesa noapic noapci nosplash irqpoll".

---

