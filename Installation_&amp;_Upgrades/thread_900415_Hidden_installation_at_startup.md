---
title: "Hidden installation at startup"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by DJCalarco on 2008-08-25
Hi all,  I hope I am putting this in the right place.

Basically, Im trying to hide the Ubuntu installation on my computer.  Maybe if there was a way I could set it up so that it only shows the option to boot Ubuntu if I have a certain flash drive inserted, or a keypress of sorts.

I dont want Grub to appear at all, just boot into Windows unless the flash drive or keypress is there.

Ubuntu 8.04, Windows Vista, HP DV6700 Notebook

---

### Post by coffeecat on 2008-08-25
Theoretically it should be possible **if** your BIOS supports booting from a usb device, if you set the BIOS to boot from the usb device first and if the BIOS would default to booting from the hard drive if the USB device was absent.

You would have to reinstall the Windows bootloader to the mbr and install grub stages 1 and 1.5 to the mbr of the USB drive with the usual root (hdx,y) and setup (hdx) commands. Again, in theory, if you get the root (hdx,y) command correct, grub would still use grub stage 2 and the menu.lst from your Ubuntu HD installation. In fact, if my theorising is correct, you wouldn't even have to format the USB drive so long as grub stages 1 and 1.5 are installed to it.

Don't forget that Ubuntu would still be visible to a computer-literate person. In Windows Control Panel > I can't remember offhand where next*, you can see all the HD partitions. The Linux ones will be marked as unknown, but they'll still be shown. But at least 'My Computer' won't show anything. 

And, of course, a **really** computer-literate person could boot up with a Linux live CD and examine all your partitions, Windows or Linux. :wink:

* Unmph - you're using Vista. What I said would be for XP. But if XP can see (but not understand) a Linux partition, so will Vista - wherever the Vista equivalent utility is.

---

### Post by DJCalarco on 2008-08-25
Excellent, I will give that a try.

I have it dual booting on my HP laptop which is about to go in for service.  If they try to boot the thing up and see ubuntu on there, they will not only "Void my warranty", but they also flash the drive back to factory.  Itll also keep the boss from snooping around while Im away from the desk.

Thanks alot!

---

