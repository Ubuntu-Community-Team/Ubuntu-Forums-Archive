---
title: "feisty fawn uninstall issues"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by darklakota on 2008-01-15
Previously I had both Windows xp and Ubuntu feisty fawn installed using a dual boot with grub. However, I had recently installed a new video card ( a nividea geforce fx 5500 256mb ) and installed a new 20.1 inch wide screen monitor. After which I couldn't get Ubuntu to load it kept coming up with errors about the resolution and wouldn't allow me to go in and change it. I decided since I didn't use Ubuntu any more here recently that I would remove it. So using partition magic in xp I removed the Ubuntu partition and the swap partition and set it so that xp would use all the free space. XP worked fine till I rebooted now when I try to load XP is goes to the grub loader still and then says error 22 ( stage 1.5 I believe ) I have tried putting the Ubuntu disk back in but it doesn't allow me to continue to Ubuntu, so since I have uninstalled my video card and new monitor so that I can get Ubuntu to load from the disk but I still can't get the grub loader off so that I can boot up my xp again. If anyone has an answer I would greatly appreciate it.

---

### Post by jimbob on 2008-01-15
If you want to restore the XP boot loader and you have your XP install CD, boot it and let it run through setup until you see a screen that gives you the selection of entering R for repair.  When the C-prompt appears enter fixmbr and it will re-write your boot sector.

---

