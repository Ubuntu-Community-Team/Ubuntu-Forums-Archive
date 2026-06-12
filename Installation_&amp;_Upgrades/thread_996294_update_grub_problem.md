---
title: "update grub problem"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by milocome on 2008-11-28
I recently upgraded to 8.10 with a dual vista boot and then I kept getting error 15 file not found with the grub trying to load 8.04

I managed to reinstall ubuntu and now I have grub4dos and grub.

when I start the computer I have grub 1.5 which then moves on to another choice screen with either a vista and ubuntu choice and then I have to enter on the grub4dos which shows all the code but does work

how do I upgrade the grub 1.5 and get it to work (it is still showing error 15) or am I better keeping the grub4dos

i basically want to tidy up the start up of the laptop

---

### Post by Coreigh on 2008-11-28
Grub throws errors when it can't find something (usually) It is likely that you need to edit the menu.1st file in /boot/grub, or re-install grub.

see this thread for instructions to restore grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I think you will want to remove grub4dos before trying to restore grub.

---

### Post by caljohnsmith on 2008-11-28
If you are using Grub4DOS, that means you must have installed Ubuntu inside of Windows via Wubi. Did you previously install Ubuntu to its own partition? What do you prefer--having Ubuntu inside Windows or having Ubuntu on its own partition? If you have no preference, I would recommend giving Ubuntu its own partition, because Wubi just adds another layer of complexity where things can go wrong.

---

