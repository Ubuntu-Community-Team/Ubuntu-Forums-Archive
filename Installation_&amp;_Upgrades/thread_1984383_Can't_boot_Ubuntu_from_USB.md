---
title: "Can't boot Ubuntu from USB"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by JesseThomas on 2012-05-21
*** I said SD card in the title my bad i mean USB! Sorry :/

I have a 2001 Intel premium 4 desktop that I have been struggling to Install Ubuntu onto. I Downloaded the ISO from Ubuntu then used unetbootin to create a bootable drive onto my USB. Once it said everything was complete i restarted my computer and pressed Esc to go to the boot menu. To my surprise i only had two options "press F12 for network service boot" and "Press f2 for setup" I continued by pressing f2 and going into the BIOS setup utility and using the boot option there to make my main hard disk driver my SD card so i could boot from it. Then i saved changes and exited, once my computer loaded up i just got a boot error message and then it said system halted... not really sure were to go from there... My BIOS options should give me a boot menu to choose what to boot from, but maybe it's to old... any suggestions?

---

### Post by darkod on 2012-05-21
Do you have USB-HDD device in the boot order devices? Usually usb sticks boot with that option.

Your computer might be too old to allow usb boot too, are you sure it can boot from usb?

Go into the BIOS again and look at the boot order and what devices it offers. If there is something like USB-HDD, put it in front of HDD and it should boot from the usb.

Are you sure the boot error wasn't from the usb stick, if it's badly created? Otherwise, if it doesn't even try to boot from the usb, it should boot from your hdd. Why would you have boot error from the hdd, it doesn't even boot anything?

---

### Post by oldfred on 2012-05-21
Edited title for you. Only new posts will have updated title.

If computer is that old, it probably does not have a USB boot option. Only in the last 6 years or so, did BIOS  get updated to use USB2 ports for booting. If system is that old it may still be USB1 and be very slow.

Some have reported plop works to boot from USB ports that BIOS does not support. But if USB1 it may be slow.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by Rex Bouwense on 2012-05-21
Sometimes a USB flash drive is recognized as another hard drive.  Go back into set up and move to boot.  Go to hard drive and see if your flash drive is recognized there.  If it is just set it to boot ahead of the hard drive and you should be good to go (if has already been said your computer can boot from a flash drive.)

---

