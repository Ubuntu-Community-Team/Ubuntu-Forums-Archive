---
title: "Startup-Manager, background image/menu"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by psychotonomy on 2007-12-15
I have an issue with StartUp-Manager. 

I've installed Kubuntu 7.10 (Gutsy Gabbon) and everything else is working fine.

I've a dual-boot system running Win XP on another disc and have installed background images for the bootloader menu. However, during boot-up, I get the new background images but the old black box menu (from the previous bootloader/GRUB) that I had before. and there's no way to see the blinking cursor so it's difficult to know which option you're selecting. moreover, with respect to the StarUp-Manager, nothing happens when I change the bootloader menu's colors to: background-normal = cyan, background-highlighted =  green, etc... or enable the blinking option.

I figure it's one of two things: 1) the old bootloader menu is being displayed on top of the new startup-manager's one (this would also explain why I can't see a cursor and can't change any of the colors or enable blinking) or 2) the background of the bootloader menu (which is displayed on top of the background image) is black (making it look the same as the old one)...and maybe the cursor is somehow black too.

I can still guess where the cursor is so I can still work the computer after boot, but I'd like to figure this out.

ideas?

---

### Post by psychotonomy on 2007-12-15
figured it out. sorry about that. when I disabled 'Use Colors in Boot Loader Menu' it did the trick.

---

