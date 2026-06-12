---
title: "customize grub/menu.lst on livecd"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2008-04-01
I just customize a live-cd and like to customize also grub/menu.lst but I cant find it.

How to customize menu.lst on ubuntu livecd?

---

### Post by dstew on 2008-04-01
> I just customize a live-cdDo you mean you *created* a custom Live CD? What method did you use to create it, if that is what you did?

---

### Post by gruadp on 2008-04-01
I did not create a live-cd but customized the existing 7.10 - livecd.

Mainly I unpack the squashed fs, chroot & change it and repack it and burn the iso

see:
[http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd](http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd)
and
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
or the new one on my server:
[http://www.goldfisch.at/knowwiki/howtos/customize_ubuntu](http://www.goldfisch.at/knowwiki/howtos/customize_ubuntu)

But I couldnt find out howto change menu.lst ...

---

### Post by dstew on 2008-04-01
OK, that is pretty cool. Did you add programs, or create a Live CD in your native language?

I still don't understand your question about grub's menu.lst file. The Live CD does not use a grub menu.lst as far as I know. There is an opening menu, but I don't think it is a grub menu. In a regular Ubuntu installation, the menu.lst file is in /boot/grub.

EDIT: The Live CD may use the isolinux boot loader instead of grub. Check step 9 in this detailed HowTo: [http://souptonuts.sourceforge.net/cdrom.htm](http://souptonuts.sourceforge.net/cdrom.htm). The isolinux menu is the product of two files: menu.txt, and isolinux.cfg, both in the /boot/isolinux directory.

---

