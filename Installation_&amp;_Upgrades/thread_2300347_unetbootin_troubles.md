---
title: "unetbootin troubles"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by enriqueenforo on 2015-10-25
At some point, some months ago I tried to install ubuntu in a Eee PC with no CD or USB boot capacity.
I just remember that I use unetbootin. There was some problem and I just put the computer away.
Now I want to solve the problem. I do not remember all the steps I did. Just the actual situation.
The computer is working fine with XP windows, but I do want to have dual boot with ubuntu.
And my previous attempt make that I have a big partition that it taking a good portion of the hard disk.
I am attaching pictures to show what is going on hoping that some of you could help me.

---

### Post by kurt18947 on 2015-10-25
That doesn't appear to be a Unetbootin issue to me (hobbyist). Unetbootin creates bootable CD/DVD/USB from .iso files. Your problem appears to be a missing or corrupted Windows file. Can you copy that file from another working Windows machine running the same O.S. version? I'm not very knowledgeable about fixing Windows problems, my usual solution is to reinstall or preferably reload an image of that partition created soon after installation and updates.

---

### Post by yancek on 2015-10-25
Unetbootin is generally used to create a bootable Live CD on a flash drive.  You then boot from the flash drive and install it to a partition(s) on your hard drive.  What you have in the boot options menu is a "frugal install".  The link below is to the unetbootin site which explains how to use this to actually install to a hard drive. I'd suggest reading the entire page with emphasis on "making a full, standard hard disk install".

 [http://sourceforge.net/p/unetbootin/wiki/installmodes/](http://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by enriqueenforo on 2015-10-25
Many thanks!

---

### Post by enriqueenforo on 2015-10-25
> **yancek said:**
> Unetbootin is generally used to create a bootable Live CD on a flash drive.  You then boot from the flash drive and install it to a partition(s) on your hard drive.  What you have in the boot options menu is a "frugal install".  The link below is to the unetbootin site which explains how to use this to actually install to a hard drive. I'd suggest reading the entire page with emphasis on "making a full, standard hard disk install".

 [http://sourceforge.net/p/unetbootin/wiki/installmodes/](http://sourceforge.net/p/unetbootin/wiki/installmodes/)


Thank you. I will look the link. I have discovered that my netbook do have usb boot capacity... and I was able to create a bootable flash drive that worked fine as a demo. The problem in the boot options is that I expected to have an Ubuntu option, and not Unetbootin. And the problem with the windows message appears when I click the Unetbootin option. I will read carefully the link you are sending. I am afraid to destroy the windows installation though. I do not have the original XP installation disk and it is working pretty well.

---

### Post by yancek on 2015-10-25
>  The problem in the boot options is that I expected to have an Ubuntu option, and not Unetbootin

No,  you won't see that.  If you select the unetbootin option when booting from the hard drive, I would expect that you would see the same thing you see when you boot a flash drive with an Ubuntu install iso on it.  You should be able to select that option and install Ubuntu from it.  That's my understanding from the reading on their site.  If you are new to all this and now have a bootable flash drive, I would use that.  In order to boot from the flash drive, you will have to enter the BIOS setup immediately on boot and change the boot priority so the usb/flash drive is first in order.

Looking over your first post again, the third image shows the unetbootin software is installed and you have the Ubuntu iso in that same location.  So did you actually run unetbootin from windows and select the Ubuntu iso and install it on a separate partition on the drive?  If you can boot the flash drive with Ubuntu on it and open a terminal, type in the following command and post the output here as it will give some useful information:  sudo fdisk -l(Lower Case Letter L in the command)

---

