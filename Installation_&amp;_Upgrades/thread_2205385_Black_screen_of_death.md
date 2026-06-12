---
title: "Black screen of death?"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by seth7 on 2014-02-13
Okay so I just purchased a Toshiba Satellite C55DT-A5305 yesterday, general specs are AMD A6 quad-core processor, AMD Radeon HD 8400 chip, 4gb of ram, and touchscreen. 
Anyway, so I burned 13.10 AMD 64bit to a DVD, and I restart the computer, the grub menu pops up letting me try ubuntu, or install it, ect. But when I choose to install it or try it even, I just get a black screen after the splash screen of ubuntu. I would try the whole nomodeset but there isn't any F key options.

---

### Post by bc.haynes on 2014-02-13
When you get to the screen with the little keyboard and man icon at  the bottom, try pressing F-6.

---

### Post by grahammechanical on 2014-02-13
If pressing F6 at that first purple screen does not work (I have never tried it), then try pressing Enter. At the next screen select the language (English default) and press Enter. Now you should be at a text based Try - Install screen. Now press F6 and select nomodeset and press enter. Press Esc to get back to the Try - Install screen.

Regards.

---

### Post by ubfan1 on 2014-02-13
For the new UEFI machines, at the black grub menu screen (which may be the first thing you see), you need to type "e" to enter the edit mode (instructions at bottom of screen), add the nomodeset keyword at the "splash quiet" keywords, and type control X or F10 to boot.  Add your proprietary drivers when you get connected so the nomodeset is not required to boot.

---

### Post by samwillc on 2014-02-13
> **ubfan1 said:**
> For the new UEFI machines, at the black grub menu screen (which may be the first thing you see), you need to type "e" to enter the edit mode (instructions at bottom of screen), add the nomodeset keyword at the "splash quiet" keywords, and type control X or F10 to boot.  Add your proprietary drivers when you get connected so the nomodeset is not required to boot.

I was just going to post something about this. I am building a new pc with a uefi motherboard (asus z87 gryphon). I presume I will also get the black screen when I try and install ubuntu 12.04. I'm used to old school 'press F2 to get into BIOS' so I have no idea what all this uefi/secure boot stuff is about. Is UEFI causing problems just for people who dual boot with windows or does it cause grief even when only installing linux? Thanks.

---

### Post by seth7 on 2014-02-13
> **ubfan1 said:**
> For the new UEFI machines, at the black grub menu screen (which may be the first thing you see), you need to type "e" to enter the edit mode (instructions at bottom of screen), add the nomodeset keyword at the "splash quiet" keywords, and type control X or F10 to boot.  Add your proprietary drivers when you get connected so the nomodeset is not required to boot.

Alright, so that let me install ubuntu, but I can't install proprietary drivers till I boot into the system. As of right now I'm just able to boot into a tty1 login

---

### Post by ubfan1 on 2014-02-13
OK, there are some other options you can add to the grub boot line.  You didn't say what your video hardware is, so hopefully, some of the below will be appropriate: For UEFI machines (with a black screen grub (grub-efi)  without any function key options, like the older grub-pc, edit the grub menu and add the below options on the "linux" line, then boot with F10 or ctrl-X.   Options for Video problems:  nomodeset acpi=0 acpi_osi=linux acpi_backlight=vendor noalpic i915.i915_enable_rc6=1 video=1280x1024-24@60 video=VGA-1:1280x1024-24@60  To allow Nvidia hybrid machines to boot. nouveau.blacklist=1

---

### Post by seth7 on 2014-02-13
> **ubfan1 said:**
> You didn't say what your video hardware is

AMD Radeon HD 8400 chip, I clearly said that in my OP.

---

### Post by seth7 on 2014-02-13
Okay, so it turns out that the fix for this particular problem was simply changing the UEFI to the compatibility setting in the BIOS, and then installing under nomodeset. There actually aren't any proprietary drivers for my graphics chipset, so I'm guessing the opensource is working fine. It boots into system fine now.

---

