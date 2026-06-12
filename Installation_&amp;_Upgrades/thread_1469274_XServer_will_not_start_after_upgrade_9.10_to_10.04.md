---
title: "XServer will not start after upgrade 9.10 to 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by brucehvn on 2010-05-02
Ok, I'm at my wit's end here with this.  I had a working Karmic installation on a P4 with an Nvidia 210 video card using the proprietary drivers installed by 9.10.

Last night I upgraded to 10.04 and when trying to boot, the computer would hang at the splash screen.  Going into recovery mode showed nothing in the log files.  The Xorg and gdm logs were zero bytes but had the proper timestamp.  I tried and tried, but could not get it to boot until I removed the nvidia-current package.  Then the computer will boot, but the screen is partially corrupted with just a blue background.  I can hit enter, then type my password and I can actually login, but I can't see a thing.  I can cycle through the resolutions with Ctrl +, but the screen just still has a blue background and nothing else.  Trying to boot in failsafe X mode gives the same screen.  I tried putting the vesa driver in the xorg.conf, but no change.

I've tried the i915.modeset=0 boot option.  I've tried the "xforcevesa" boot option, but nothing will give me a readable screen.  As soon as I re-installed the nvidia-current package and ran nvidia-xconfigure, the problem came back and it hangs again.

At this point, I'm stuck.  I would settle for a plain VGA screen at this point, but I can't even seem to get that.  I've read several posts here with similar problems and tried every solution put forth, I think, but have not found a solution.

When the upgrade wanted to install the new /etc/default/grub, I kept my old one.  I compared the two files at the time, but I didn't see anything new, but maybe I missed something.  What new items if any does the upgrade put into /etc/default/grub?

---

### Post by brucehvn on 2010-05-02
Well finally in my second day of this, I am able to get into my desktop.

I did an "apt-get purge nvidia*" to get back to the nouveau drivers.  I then used the device "nv" in my xorg.conf and am able to get in and use my Ubuntu.

I realised I have been using the wrong kernel option to try and turn off KMS.  I was trying i915.modeset=0 when I should have been using "nouveau.modeset=0", however it made no difference in my problem.  The computer still locked up with the nvidia drivers.

Now that I'm in the gui, when I go to System-Administration->Hardware Drivers, it does not list any proprietary drivers that I can use.

I'm hesitant to try and install nvidia-current again, but at least I know how to get back to a working configuration should I end ujp the same again.

---

