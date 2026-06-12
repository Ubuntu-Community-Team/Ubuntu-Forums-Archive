---
title: "[SOLVED] Creating a grub dongle"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by V-600 on 2007-11-25
Sorry I missed this one.
[http://ubuntuforums.org/showthread.php?t=622817](http://ubuntuforums.org/showthread.php?t=622817)

I have found a few posts regarding creating a boot floppy but in this case I don't think it applies as the machine in question (belonging to my dad, who dislikes changes to his computer which "works fine as it is thank you very much") does not have one. I have been thinking then about using a USB flash drive as a more modern replacement (similar to a dongle).

Connect the USB drive, the computer boots and points to a partition with ubuntu on. Remove the usb drive and the windows bootloader is still on the MBR and windows boots. This way the computer is not affected at all by uninstalling ubuntu, or forcing me to try and find the windows cd to reinstall it.

I have installed xubuntu on a laptop and seem to remember that either at the end of the install or the last option before you are presented with the option to write grub to the MBR or the start of the partiton (i think). At this point could you select a USB flash drive and would that work.

Many thanks for any advice or info (I have looked at the GRUB website but I think its aimed at those more knowledgeable than me)

---

### Post by Pumalite on 2007-11-25
You can do that and it will work most of the time. Some people prefer disconnecting all internal drives.

---

### Post by V-600 on 2007-11-25
Thanks. I want to install to the hard drive so will leave that connected i reckon.

---

