---
title: "Create USB on Linux Mint"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by SMOKE14 on 2013-01-21
I need to create a bootable Ubuntu 10.04 USB (yes, 10.04 for a reason), and the PC is currently running Linux Mint 14. I've tried Unetbootin, but when the PC restarts and boots, the only option is default. I press enter, and it just restarts the automatic boot in 10 seconds, and if I let the timer run down, it just restarts.

---

### Post by SMOKE14 on 2013-01-21
Oh, I also have some dual layer Memorex DVDs.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

If you have burned the ISO to the USB, you will probably have to make sure that the BIOS boots off the USB. It would be easier to use DVDs to burn, and if you choose to use this options, then open up Brasero and click the last option called;

[IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/07/Brasero-Main1.jpg[/IMG]

And then find your ISO, select it and then it "burn". I also use Linux Mint 14, so I could always provide images if needed. Or you can check here for the [DVD method]("http://www.addictivetips.com/ubuntu-linux-tips/use-brasero-to-burn-cddvd-in-ubuntu-linux/").

As for the USB method, please check out Linux Mint's site instructions.

[http://community.linuxmint.com/tutorial/view/744](http://community.linuxmint.com/tutorial/view/744)

---

### Post by SMOKE14 on 2013-01-21
Thanks for the help, using Brasero now. Will report back with details.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Alright, I will be here if you need the help. Make sure you are burning the correct bit type for your computer, too. (:

---

### Post by madhank65 on 2013-01-21
I have excellent results with "Live-USB-Creator".  It works on windows or linux.  It always provides option for persistance(SP?). for linux, download live-usb-install-2.3.2-all.deb.  Google it.  It's not LiLi linux -live.  It's persistance is buggy and it uses Virtual Box.  Live is a joy to use.  Mint will take ABOUT 8-10 to load depending on persistance. I carry around a 32 with Ubuntu Studio to use at gigs.  good luck.

---

### Post by SMOKE14 on 2013-01-21
Hmmm.... couldn't get it working using Lightning Dragon's suggestions, don't know why. They refuse to boot, and they are set first priority in BIOS. I'll try madhank's suggestion.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

What do you mean it refused to boot? Was it a black screen, errors, anything? Did your DVD have enough space for the iso and did you use a bit type your computer supports (and did you get a text-based installer?)? Also, "they"? If you used the DVD method, you will have to make sure you selected the correct burner (if you have more than one) through the boot option in BIOS.

If you burned it right, then it shouldn't be a problem with the disc. It might be something with your BIOS/computer if it isn't allowing you to boot.

---

### Post by SMOKE14 on 2013-01-21
I tried two different DVDs, both using the correct settings, and they just didn't boot. It went straight to Grub boot menu, prompting me to boot to Linux Mint or Windows 7. But, using madhank's suggestion, I got a USB to work. Thanks to both of you for your suggestions though!

---

