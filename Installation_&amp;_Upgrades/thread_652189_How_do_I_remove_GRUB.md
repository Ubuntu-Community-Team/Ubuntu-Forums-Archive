---
title: "How do I remove GRUB?"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by gatoz on 2007-12-28
I guess I jumped the gun a little early, I wanted to remove Ubuntu so I went and deleted the partitions BEFORE fixing my MBR, now GRUB is stuck with an Error 22 and I can't boot into Vista, I have no install disc. Can someone please help? :(    ( I do have a XP install disc, but my comp is vista)

---

### Post by forestpixie on 2007-12-28
not sure if it'l help, never having used vista - but supergrub can restore windows mbr so I assume it should do it

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by gatoz on 2007-12-28
The only way I can do it is with usb, but the command it tells me to type won't work

---

### Post by gatoz on 2007-12-28
Is there a way to fix the MBR from the live cd?

---

### Post by forestpixie on 2007-12-28
did you see the USB part of the download page - just above the  [bottom]("http://supergrub.forjamari.linex.org/?section=download#more")

as far as using the livecd - I don't believe it will be able to fix the mbr - that's a windows thing, but you can use it to get online

you might be able to use [easybcd]("http://neosmart.net/dl.php?id=1") - not sure

---

### Post by meierfra on 2007-12-28
Click on FixMBR  my signature.  It list three ways to fix the MBR, The third method can be done from the LiveCD.

---

### Post by forestpixie on 2007-12-28
ms-sys now that's a handy thing to know about :)

---

### Post by gatoz on 2007-12-28
Okay, I reinstalled ubuntu, the grub works now.
I am using windows right now, how do I  remove grub?

---

### Post by meierfra on 2007-12-28
You can use EasyBCD (see post 7)

---

### Post by forrestcupp on 2008-01-02
EasyBCD didn't remove GRUB for me.  All it did was repair Vista's bootloader.  There was no problem with Vista's bootloader to begin with.  When you choose Vista from GRUB, it goes to the bootloader.

edit:
SuperGrub was the only thing I could get to work.

---

