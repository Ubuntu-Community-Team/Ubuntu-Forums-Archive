---
title: "Install Ubuntu 8.04 to external drive"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by AnotherMuggle on 2008-05-18
I have a 6GB external drive that I would like to install Ubuntu onto.  Is this possible?

I have been using a Live CD for a while but it is slow, I am unable to save and no settings are persistent.  Installing Ubuntu directly to the machine is unfortunately not an option.

Is anyone able to help?

Thanks,
TK

---

### Post by rich86 on 2008-05-29
Hi, i have been researching the same thing. It looks like it is very much possible to do.
If you BIOS can boot from usb (most modern computers can) it is very easy, just install Ubuntu to the external drive from the LiveCD BUT on the last stage tell GRUB (the boot loader) to change the MBR (master boot record) on the external usb drive. It will possiblly be /dev/sdb but make sure you check first. This way if the usb drive is plugged in the bios will boot to it (depending on your boot order) and you can select to run Ubuntu from GRUB, if the external drive is not plugged in it will just run as it did before.
This thread might give more information: [http://ubuntuforums.org/showthread.php?t=433317](http://ubuntuforums.org/showthread.php?t=433317)

Hope that helps,
Richard

---

