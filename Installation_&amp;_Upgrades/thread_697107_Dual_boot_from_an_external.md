---
title: "Dual boot from an external"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by ranger_cole on 2008-02-14
I have successfully installed Ubuntu 7.10 on an external HD.  It work fine.  1 partion and a swap file.  I want to add another linux so I can dual boot.  I know I will need to resize my U 7.10 and then create a new partition for 2nd linux.  I am guessing I could use gparted for this.  Do I create new partition and then boot from the Linux cd I want to install and go through the set up and just install it on new partition? Will this install add my new linux to the U 7.10 boot menu?  I am a newbie and would like some  guidance on how to do this.

---

### Post by Pumalite on 2008-02-14
Some distros do give you a menu with others included; others don't.
You can always reinstall Ubuntu Grub which it does.

---

### Post by ranger_cole on 2008-02-27
I am so new I do not know how to reinstall grub.  Do you know of a link or a site than gives the details?  Thanks for your information.

---

### Post by confused57 on 2008-02-27
> **ranger_cole said:**
> I am so new I do not know how to reinstall grub.  Do you know of a link or a site than gives the details?  Thanks for your information.
Here's how to reinstall grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

The new distro will probably overwrite your current Ubuntu's IPL(Initial Program Loader) on the external hard drive's mbr...You can just leave it set up this way or reinstall your current Ubuntu's IPL to the mbr, then add a configfile entry to boot your new distro:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

