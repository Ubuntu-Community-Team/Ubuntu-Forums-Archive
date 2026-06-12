---
title: "Installing GRUB on a USB stick WITHOUT using Ubuntu"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by MagicalDean on 2011-10-23
I've installed Ubuntu on the second partition of my second hard drive, but unfortunately didn't manage to install GRUB on the same hard drive. Consequently, I seem to have an install that worked but that I can't access.

Is there any way I can install GRUB on a USB stick, and use that instead of installing it on a hard drive as I use Windows most of the times and so don't want to make any changes to that?

---

### Post by raja.genupula on 2011-10-23
Hi 

i didn't understand your problem actually , what you wanna do ? 

ok i am giving the solution from what i got .

```
sudo dpkg-reconfigure grub-pc
``` 

do this & while doing,  install the grub to your desired hard drive.

All the best.

---

### Post by MagicalDean on 2011-10-23
My issue is that I currently can't get into Ubuntu, hence trying to get GRUB installed on a USB stick. I can access Ubuntu on a different computer, but not sure that's any help.

---

### Post by raja.genupula on 2011-10-23
> **MagicalDean said:**
> My issue is that I currently can't get into Ubuntu, hence trying to get GRUB installed on a USB stick. I can access Ubuntu on a different computer, but not sure that's any help.

ok look at my signature for grub recovery link

all the best

---

### Post by MagicalDean on 2011-10-23
I tried the "Using the Ubuntu Alternate CD" option, but was greated by:
"Auto-detection of a filesystem of /dev/mapper/u-root failed.

I forgot to mention that I install using the encrypted LVM, which I assume is what is causing the issues. Is there any solution to this?

---

