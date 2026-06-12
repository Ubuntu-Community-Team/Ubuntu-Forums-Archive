---
title: "Getting grub command line prompt after new install on a triple boot system"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by Jason Spaceman on 2014-10-28
I did a fresh install of Ubuntu 14.10.  My computer triple boots between Win7, OS X Yosemite, and Ubuntu. I am using the Chimera bootloader from tonymacx86.  Normally when I start the computer Chimera displays a menu on the screen allowing me to select Windows, OSX, or Ubuntu.  If I select Ubuntu it hands things off to Grub which loads Ubuntu.

I did a fresh install of Ubuntu 14.10, however the Ubuntu entry has disappeared from Chimera.  It just displays Windows and OSX.

To get into Ubuntu I have to press F12 and go into my computer's BIOS and select Ubuntu from there.  However it doesn't fully load Ubuntu.  Instead I get the Grub command line.  I have to type in:

```
set prefix=(hd0,gpt6)/boot/grub
set root=(hd0,gpt6)
insmod normal
normal
insmod linux
linux /boot/<long name of linux kernel> root=/dev/sda6
initrd /boot/<long name of initrd image>
boot
```

Then Ubuntu finishes loading.

How do I fix this so that I don't get the Grub command line and Ubuntu fully loads?  Grub doesn't reside on the MBR, instead it resides on /dev/sda6.

Bonus points if you can help me get the Ubuntu option back on my Chimera menu as well.  :-)

---

### Post by yancek on 2014-10-28
Boot the Ubuntu installation medium, mount whichever partition on which you have the grub boot files, check what you have posted that works against the actual entry in the /boot/grub/grub.cfg file and change as necessary to test.  To get your Ubuntu entry on the Chimera boot menu, you probably need to check the documentation at their site as it doesn't look like Linux software.  If you installed a new version of Ubuntu, you would have a new kernel so I would not expect that to work until you re-configured your Chimera.  Check their site for documentation.

Did you install Ubuntu in EFI more, you need to do that?

---

### Post by Jason Spaceman on 2014-10-29
> Did you install Ubuntu in EFI more, you need to do that?

I'm not sure how to do that.

---

### Post by yancek on 2014-10-29
Detailed info at the Ubuntu page below:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

