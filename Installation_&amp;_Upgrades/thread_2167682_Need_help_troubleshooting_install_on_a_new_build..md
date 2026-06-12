---
title: "Need help troubleshooting install on a new build."
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by ratdog on 2013-08-14
Hello all,

I have recently bought some new goodies from newegg to build a home media server.  I'm having trouble getting Ubuntu 12.04LTS (or any other version) to load.

I have tried loading from both DVD and USB {side note: I can't seem to make a USB image that passes the integrity test} and have had no luck.  

I have integrity checked the DVD and ran the memory check.  I have also sent for a replacement motherboard and the new one gives me the same problem.

The problem is:  After selecting 'try ubuntu' or 'install ubuntu' from the initial menu, the resolution changes and the ubuntu loading page is shown, the screen will flicker a few times (display drivers loading?) while the progress dots move back and forth and then the computer will freeze with all of the progress dots orange and the dvd drive will wind down.  This seems to always happen in the same place.  I have tried loading without the messages hidden (don't remember the command) but I don't see any obvious error messages.

I'm not an expert on this, hence asking for help here.  Where do I start?

Here are the hardware basics:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157259](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157259)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819106014](http://www.newegg.com/Product/Product.aspx?Item=N82E16819106014)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145278](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145278)

Thank you so much for any suggestions!

---

### Post by oldfred on 2013-08-14
Are you booting in BIOS/CSM/Legacy or UEFI mode?
If you get grub menu it is UEFI, if you get accessibility (purple with icons) screen it is BIOS mode.

Which do you want BIOS or UEFI?

I do not know about AMD graphics as I have nVidia.
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by ratdog on 2013-08-14
If I hit 'enter' after I see the BIOS splash, I get the text-based loader options (UEFI ?).  If I wait without touching any keys, it continues and tries to load the more graphical interface I think.  It never makes it through this way though.

Thanks for the links.  I'm not sure if I want BIOS or UEFI??

---

### Post by ratdog on 2013-08-14
Ok, I'm confused.  My motherboard BIOS (but not BIOS?) is UEFI.  Can I install the OS directly from the UEFI BIOS screen?

---

### Post by ajgreeny on 2013-08-14
Here you go; plenty of info about how to boot an installation DVD/USB and then install on a new machine where you have the option of UEFI or legacy BIOS mode to choose from.

I have my system installed as a single boot machine (no Windows in this household!) with Xubuntu 12.04 in UEFI mode, and once I followed all the necessary steps in this linked page it all went very quickly and easily, and now runs like a dream.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ratdog on 2013-08-14
Thanks,

I did go to that link, but am still having problems.  I've figured out how to boot the liveDVD in Legacy or UEFI in the BIOS.  I was initially using Legacy, but have tried using UEFI to load Ubuntu Live with no success.  My BIOS does not have the Quickboot/Smartboot or SRT options to play with.  The LiveDVD never finishes loading and so I never have the option to Install Ubuntu from the LiveDVD.

In short, I don't think Legacy vs. UEFI is the source of my problems.

---

### Post by oldfred on 2013-08-14
No, it probably is video issues which is real common. Even my  BIOS sytem with nVidia has needed nomodeset since 10.10 on install and first boot after install.

If in UEFI mode you get grub menu, press e for edit and scroll down to linux line. Replace quiet splash with nomodeset. If in BIOS mode while tiny icons are on screen press any key then f6 and choose nomodeset.
Some new systems also need other boot parameters. 
What video card or chip and what motherboard?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

See also link in my signature for info and links to many good UEFI sources of info.

---

### Post by ratdog on 2013-08-14
oldfred - It appears to be working with nomodeset.  Install in progress!
I'll let you know how it turns out.

---

