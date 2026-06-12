---
title: "Windows Reinstall - How Simple Will it Be?"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Sly_R on 2007-04-13
I have a laptop running both Windows XP Home and Ubuntu Edgy (Grub boot manager).  It seems I may benefit from a complete reinstall of Windows.  Is this possible without messing up anything else?

---

### Post by Ptero-4 on 2007-04-13
Reinstalling windoze is gonna f*ck your grub by replacing it with it`s propietary bootloader which can only boot M$ OS`s.

---

### Post by jordanmthomas on 2007-04-13
Luckily, as long as you still have your Ubuntu LiveCD around it will be simple to reinstall grub.

So, yes, Windows will mess things up, but it's nothing too hard to fix.

**edit** also, you *can* use the Windows boot loader to load up grub.  I've even seen it used to dual boot OS X and Windows.

---

### Post by Ptero-4 on 2007-04-13
How do you do that? Do you need to patch any system files to prevent compliance checks (a la uxtheme.dll)? B/c I was under the impression that the bootloader was written so that it will proactivelly block non-M$ OS`s.

---

### Post by jordanmthomas on 2007-04-13
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)
This has information on how to boot to GRUB from the Windows (using the standard boot.ini) bootloader.  You basically trick Windows, but it does work.

As for the OS X one, I was referring to hackintoshes so I don't know if I am actually allowed to link to anything or not and I'd rather not break any rules.  Basically, it involves putting a file in the root of your Windows installation and using boot.ini to chain to OS X.

But to answer your question...no, you don't need any patches, but you *do* have to edit boot.ini (which is to be expected).

---

### Post by Ptero-4 on 2007-04-14
Thanks. I always thought that M$ apps are full of boobytraps to keep you from using them with apps from rival providers.

---

