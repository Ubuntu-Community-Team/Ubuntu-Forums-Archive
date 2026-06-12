---
title: "Can't load liveUSB to install on ee PC ~1215"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by danila4 on 2014-09-22
I have 12 inch eee pc with atom n570 and win 7.
Wanted to give a try to lubuntu 14.04.1 (installed ubuntu through wubi before, was pain in the ass too and interface was laggy so deleted it)
Used few mentioned programs for creating liveusb (linux liveusb maker, [FONT=Ubuntu][COLOR=#333333]UNetbootin) and the main problem - my netbook "sees" the flashdrive (usb 2.0 jetflash 4gb, win7 livecd was working fine with it) but can't "boot" it. It just stay on the black screen with blinking underscore _ (led on pendrive indicates some activity but 1 hour has passed with no results).
[/COLOR][/FONT]

---

### Post by Michael_McKenney on 2014-09-22
Try burning the ISO to a CD or DVD and booting it.

---

### Post by danila4 on 2014-09-22
> **Michael_McKenney said:**
> Try burning the ISO to a CD or DVD and booting it.
Can't do - no cd/dvd drive.
Win7 installation and also win7 liveCD worked fine from same usb flashdrive and on the same notebook.

---

### Post by yancek on 2014-09-22
Plug the flash drive you have into a port and boot or reboot the computer.  Enter the BIOS setup and check to see if the flash drive shows anywhere, look under Boot and/or boot priority to see if it is listed.  I have a notebook with several usb ports but a flash drive will only boot from one of them so try all the ports you have.

---

### Post by danila4 on 2014-09-22
> **yancek said:**
> Plug the flash drive you have into a port and boot or reboot the computer.  Enter the BIOS setup and check to see if the flash drive shows anywhere, look under Boot and/or boot priority to see if it is listed.  I have a notebook with several usb ports but a flash drive will only boot from one of them so try all the ports you have.
It sees the flash drive, I can choose to boot from it. The problem is - it can't load from it. If I eject it - then pc loads into windows saying can't load from usb. If not - it stays on black screen with _ forever.

---

### Post by Michael_McKenney on 2014-09-22
Look in the BIOS for USB legacy settings and enable them.  Check the boot order and move the USB thumb drive up in it.

---

### Post by danila4 on 2014-09-22
> **Michael_McKenney said:**
> Look in the BIOS for USB legacy settings and enable them.  Check the boot order and move the USB thumb drive up in it.
There is no usb legacy settings. And as I said - i moved and enabled everything. It clearly TRIES to load from flashdrive but for some reason fails. And it worked with windows liveCDs.

---

### Post by Rex Bouwense on 2014-09-22
It sounds like you have done everything correctly.  Just a few questions.  When you downloaded the ISO did you check the MD5Sum?  Which program did you use to create the bootable flash drive?  (You mentioned several.)  I have been using Lubuntu on my ASUS EeePC since before it was officially recognized by Canonical.  
Also, while you are in the BIOS, navigate to Boot and then down to hard drive to insure that the flash drive is not recognized as another hard drive (which it probably is).  If that is the case move it in front of your hard drive, save, exit and continue with the boot.

---

### Post by danila4 on 2014-09-23
lubuntu-14.04.1-desktop-amd64
md5 is fine.
LinuxLiveUsb Creator and Unetbootin.

Did that.
It recognizes the flash because without it it simply skips to loading windows and with it it stays on " _ " screen forever.

---

### Post by danila4 on 2014-09-25
Any ideas?

And can I, for example, install lubuntu through wubi and then use this installation to properly install in under linux? Is that possible?

---

### Post by mörgæs on 2014-09-26
Wubi is deprecated and should not be used. 
Did you try installing a 32 bit ISO?

---

### Post by danila4 on 2014-09-27
> **mörgæs said:**
> Wubi is deprecated and should not be used. 
Did you try installing a 32 bit ISO?
It is present on the ISO and besides - it seems to be the only way to install ubuntu right now (apart from searching for external CD)
Not yet, but N570 is listed as 64 bit

---

### Post by danila4 on 2014-09-28
I solved the problem by using UltraISO and burning the iso onto my usb in usb-hdd+ v2 mode. All other programs didn't work. Hope this helps someone.

---

### Post by mörgæs on 2014-09-28
Good, please mark the thread solved using 'thread tools'.

---

