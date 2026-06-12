---
title: "No GUI, Lucid on Toshiba laptop"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Perey on 2010-07-03
I've just done a clean install of Kubuntu 10.04 on my Toshiba Tecra laptop, and it hangs every time it goes to start the X server

Wait, scratch that. I've just *finally managed* to get Kubuntu 10.04 installed. Every time I tried the install (first netbook, then desktop), it would hang at a black screen. This came after (1) either telling it to "try without installing" or "install", and (2) sitting through the "Kubuntu" loading screen for a while.

Completely hung; even the caps lock light is nonresponsive.

So I got the alternate install CD instead. Installed fine. Boot up, got through GRUB, and then... same thing happens.

So I booted into recovery mode and got to the menu OK. Told it to try failsafe X mode... same black screen, but this time it was nice enough to dump me back to the recovery mode menu. So I went to a root prompt and started digging. (I'm no expert, but I have a vague idea of where to find config and log files.)

This is tail /var/log/Xorg.failsafe.log
```
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
f000:576f: 01 ILLEGAL EXTENDED X86 OPCODE!
 ddxSigGiveUp: Closing log
```

A bit of Googling has led me to [https://launchpad.net/bugs/155312](https://launchpad.net/bugs/155312), which documents a similar problem (in Gutsy!), though in that case users could boot up and use the system for a short time before it hung. But the two reported systems are also Toshiba laptops.

For what it's worth nowadays, that bug suggests switching the driver being loaded. But I have no idea how. /etc/X11/xorg.conf doesn't exist, and /etc/X11/xorg.conf.failsafe has completely generic values in it.

Help?

---

### Post by oldfred on 2010-07-03
I had to do this with my desktop & nvidia, nomodeset seems to work for some others as well:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Perey on 2010-07-03
Hooray for fast replies! Since my laptop doesn't have Nvidia graphics, I skipped straight to [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) (which described my situation perfectly -- my Google-fu is weak!)

And all's well. Actually it's just restarting after finishing the second step now, but the fact that it booted properly after the first stage is an excellent sign.

Thank you!

---

