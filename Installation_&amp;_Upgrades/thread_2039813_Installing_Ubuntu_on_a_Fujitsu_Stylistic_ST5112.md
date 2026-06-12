---
title: "Installing Ubuntu on a Fujitsu Stylistic ST5112"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by remn on 2012-08-09
I'm planning to install Ubuntu 12.04 on my Fujitsu ST5112 slate and am wondering if there are any issues I should be ready to deal with, such as the wacom, pen, rotation buttons, etc. I searched on this issue but didn't find anything very recent. It seems there have been calibration issues (getting the screen and stylus to work in sync when rotating) in the past, but I'm wondering whether these have been dealt with in the last couple years. So I'd appreciate any tips from anyone with experience running ubuntu on the Stylistic or similar Wacom slates. I don't have a lot of experience with Linux, so I'd like to be able to anticipate as many issues as possible before attempting the installation. I'm planning on using Wine and would rather not set up a Windows dual boot.

Here are the specs for the ST5112:

Fujitsu-Siemens Stylistic ST5112
Core2 U7600 1.2Ghz
Intel 945GM chipset
Wireless controller: Atheros Super AG
Raplaced OEM HDD with Samsung 470 SSD (128GB)

---

### Post by Favux on 2012-08-09
Hi remn,

You should be OK with the Wacom stuff.  You can use a rotation script, say one from the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830") or xrotate.py from [Magick Rotation]("https://launchpad.net/magick-rotation") to rotate.

Magick Rotation also has a new fujitsu-tablet.ko in MagickExtras that might handle your buttons.  But while it does pick up the bezel buttons they don't seem to do much even though the key code assignments are made.  We're sort of waiting for Robert Gerlach to ride to the rescue on that.  Or maybe investigate Xmodmaps for them it they show up in xev.

---

### Post by remn on 2012-08-11
Thanks for the tips, Favux. Glad to know I'll be able to run Linux on my slate.

---

### Post by tyj on 2012-10-12
I have installed Ubuntu 12.04 on my Stylistic ST5112.  After researching for quite a while, I booted from a USB install using the USB Universal Install from pendrivelinux.com.  The USB boot was flawless!  Everything just ran!  Wireless, Ethernet, Pen/Tablet.  I was quite enthralled.  So I went ahead and did a dual partition side by side with Vista (yuk, I know, but I wasn't willing to part with Win completely!)  Install appeared to go flawlessly, however after reboot the usb mouse and keyboard stopped working and the ethernet AND wireless devices completely disappeared!

I'm a bit discouraged at this point, since the onscreen keyboard is a MAJOR pain and I'm functionally cut off from the rest of the world!  I've thought about running from USB full-time, but obviously that is not an optimal solution.

And so I am humbly requesting any insight, help, etc.  I'm pretty handy around a terminal, but must admit I'm a relative newb with ubuntu.

My network hardware is as follows:

1.) eth0 = Marvel Yukon 88E8055 PCI-E Gigabit Ethernet (info from WinVista Device Info), when booted from USB the network manager showed driver sky2
2.) wlan0 = Intel Pro/Wireless 3945ABG (also from WinVista Device Info), when booted from USB the network manager showed driver iwl3945

---

### Post by Favux on 2012-10-12
Hi tyj,

Since it is a fresh install the simplest thing to do would be to try a re-install.

Since things were working OK with the usb stick try that first before assuming you have a corrupted download of the iso on the usb stick.  If that doesn't work try a new iso and reinstall.

---

### Post by tyj on 2012-10-13
Hi favux,

Thanks for the reply!  Thought I should let you know that I posted this to a new thread

[http://ubuntuforums.org/showthread.php?t=2070510](http://ubuntuforums.org/showthread.php?t=2070510)

I hadn't assumed that I had a corrupted .iso, and I've already tried a reinstall, second time tried with disabling legacy usb in the bios, but that did nothing but completely disable the usb ports.

Should I indicate this thread solved(or something?) and use the other one (noted/linked above)

---

### Post by tyj on 2012-10-13
Well, I did a fresh install, using a different USB stick and everything works.

I didn't select the "Download Updates" for the install, just to see if maybe there was something going on with the update process during download.

I'm updating now and will repost afterwards to indicate the final status after update.

Cheers

---

### Post by Favux on 2012-10-13
Nice job!

Hopefully it isn't something in the updates that is knocking your stuff out.
> Should I indicate this thread solved(or something?) and use the other one (noted/linked above) 
Only the OP can change the thread status like that.  So you'll be able to do that on the thread you started.

---

