---
title: "Lucid Lynx Upgrade -&gt; No more progress bar (boot screen)"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by ouija on 2010-05-05
Hey,

Recently took the plunge and upgraded to Lucid Lynx.   Had a few issues with my HP machine and getting the NVIDIA drivers reconfigured, but I found instructions here that helped me get past this hurdle: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

The only other issue I seem to be experiencing (on this and my laptop as well) is that the "progress bar" or boot up screen does not appear on either machine (The cursor just flashes on the "Starting up.." text, and eventually Gnome/xserver boots fine)

How can I get the progress bar back?  I've tried a number of things and cannot seem to get it working, so I though I'd ask and see if anyone knows a solution.

I know that Lucid is now using Plymouth or something now instead of usplash, and I tried re-installing it (along with re-installing the Ubuntu/Plymouth theme and reconfiguring it) but still no go.

My grub menu.lst file hasn't been modified, still contains the splash bit in it, and the bootloader should appear but doesn't..

Any thoughts/Suggestions?

Thanks!

---

### Post by dino99 on 2010-05-05
grub menu is hidden by default on single system, holding "shift" key down at end of bios process will pop it up. (can be changed using gconf-editor)

progress-bar is gone now and replaced by plymouth.

most of the issues as yours are due to either grahic driver issue or timing conflicts with plymouth: that should be fixed soon. If you cant wait, try:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure "your xserver-xorg-video-driver"
sudo dpkg-reconfigure plymouth

sudo update-initramfs -u

---

