---
title: "&quot;Proper&quot; install to USB"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by belovedmonster on 2008-01-28
I've been reading up on how to get Ubuntu installed on a USB stick but it seems all the tutorials are basically installing the live CD but with the added benefit of then being able to save the changes to a second partition.

My question then is whether this is ultimately not as good as having a full blown proper install of Linux on the usb stick? Would running what is essentially a live disk version be slow to boot up?

If it is better to install "properly" to a usb device then can someone point me towards a tutorial to do this?

Thanks in advance!

---

### Post by DRPend on 2008-01-28
I've never known anyone to create a full install of linux on a USB drive, but I did have an associate that used 2 gigs of flash ram to install a boot kernel for a remote astronomy system. This was for robustness in boot capability obviously and had no x windows on it. If you can get a large enough USB stiick you might be able to run a CD install and specify the USB stick as a partionable drive, but you'd have to use a tect based installer. None of the GUI ones will let you do this. You'd probably have to build the files system by hand and untar the kernel files onto the drive. Not sure why you'd want to do this as in being a removable drive you'd be asking for some headaches later on. A live CD install would be more logical. I'm not sure if any Ubuntu will work like this, but my friend used Debian Sarge.

Good Luck!

---

### Post by belovedmonster on 2008-01-28
If what you say is true then I guess theres no question I should go with the live option.

If a proper install is a no go then I'll follow [this]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") tutorial using a 4GB stick.

---

