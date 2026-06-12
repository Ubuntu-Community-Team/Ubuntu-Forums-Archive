---
title: "Can I install lucid, and keep karmic on another partition?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Mr_VeRiTy on 2010-05-25
Hi, I'm installing lucid on my brothers desktop pc, but he wants to keep karmic just in case he doesn't like it. Can I keep karmic on another hard drive and still choose between them on boot?

Also, when im installing it I have the option "install boot loader" but isn't grub already installed? (from karmic) and if i install it twice will there be errors?  and also since they are on different different hard drives will grub still show both of them?

p.s is there anything i would have to do that I wouldn't normally have to do in a normal install?


Thanks.


EDIT:I don't know if this changes anything but i also have xp on the same hard drive as karmic.

---

### Post by darkod on 2010-05-25
Yes, you can install it on another partition/disk. I guess he's used to the grub2 he is using right now so you don't have to install grub2 from Lucid.

In the installer on the last screen there is Advanced button. You can select not to install bootloader there.

After the install the computer will probably boot straight into Karmic because it's still not aware of the Lucid install (if you decide not to install grub from Lucid). Just execute:

sudo update-grub

and it will find Lucid and create the menu for dual boot.

PS. Having XP doesn't change anything.

---

### Post by Mr_VeRiTy on 2010-05-25
oh that clears things up, thanks.:)

---

