---
title: "Installation of 10.04 problem: bad default resolution = stoned screen"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Nokao on 2010-06-14
Hi ...

Launching the 10.04 installation disk takes me to a screen with a lot of black-white rows, this is a problem I had previously in the 8.0 version with bad resolutions of my monitor, but actually I'm using feisty pretty well.

However, how can I change the resolution before the installation starts?

I have a nForce chipset with integrated nVidia video card.

---

### Post by eggdeng on 2010-06-14
If you get as far as the keyboard and stick figure, you can hit the spacebar and choose
Try ubuntu without installing
Hit F6 to edit the boot command. Add the arguments
```
i915.modeset=0 xforcevesa
```
Then continue installation from the desktop icon.

---

### Post by Nokao on 2010-06-15
That worked for the installation, and also for some reboots after ...

But after an upgrade of my system when I turn on the PC I get a bash login instead of graphics.

After that, if I login from the shell and **sudo /etc/init.d/gdm restart**
Gnome starts ... and I can login via X.

Why I have to do restart it manually?
And why it works after the restart and not in the first boot?

In the logs I found this:
```

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50--829.28 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-61.79 Hz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter...
(II) VESA(0): Configured Monitor: Using hsync range of 31.50--829.28 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-61.79 Hz

(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "2048x1536" (hsync out of range)
(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
(II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
(II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules/libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional i$

 ddxSigGiveUp: Closing log


```

lspci | grep VGA 
00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)

---

### Post by dino99 on 2010-06-15
you may need to remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

and add this ppa to synaptic repo:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update and packages: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings have to be installed

reboot and check that nvidia-current is activated: system admin hardware driver

---

### Post by Nokao on 2010-06-15
It worked except the deleting xorg.conf part.

I had to take it back from a backup.

However I have a small resolution ... and the feeling that another upgrade of the system will wipe up my video again .... :(

I feel unstable.

---

### Post by joncrndl on 2010-06-16
Check out the release notes for Lucid 10.04.  Specifically,  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture")

Before I stumbled onto this jewel, I was getting no where.  Video display looks great in 9.10 and not so good or not at all in 10.04, then check this out.  

Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by  default on most common video chipsets.  While this is a major step  forward for the graphics architecture in Ubuntu, in some rare cases KMS  will prevent your video output from working correctly, or from working  at all.  If you need to disable KMS, you can do so by booting with the nomodeset  option.  You can also save this setting so that it's applied at every  boot by adding it to your grub config (for GRUB 2: edit /etc/default/grub and add nomodeset  to GRUB_CMDLINE_LINUX, then run sudo update-grub; for GRUB 1: edit /boot/grub/menu.lst and add nomodeset  to the line beginning with # kopt=, then run sudo update-grub).  ([533784]("https://bugs.launchpad.net/bugs/533784"), [541501]("https://bugs.launchpad.net/bugs/541501"))

---

