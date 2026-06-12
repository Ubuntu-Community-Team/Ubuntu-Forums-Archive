---
title: "Dell and Karmic xorg and grub"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by lazar689 on 2009-11-25
I am using Karmic for one long day, but rebooting is more of White Screen (WSoD).
So I stop the boot sequence to add "nomodeset" and continue with 1280x800 screen on my Dell 1535.
I don't have these famous files called xorg.conf and grub.conf to edit the last for this switch

How can I generate them in my system? May be some stuff is missing on my system. It works fine, but the boot phase is punishment

Thanks for any help. I like Karmic and never go back to Windows 7

---

### Post by coffeecat on 2009-11-25
If you want to add nomodeset to your kernel options in grub 2, have a look at this:

[http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS]("http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS")

...under "No Xv support for Intel 82852/855GM video chips with KMS". I know you have an ATI card in that laptop (according to google) but the instructions for adding nomodeset are good.

---

### Post by lazar689 on 2009-11-25
Thanks a lot. I'll try the idea and br back soon

---

### Post by lazar689 on 2009-11-25
No such file menu.lst. Back to my problem.

---

### Post by coffeecat on 2009-11-25
> **lazar689 said:**
> No such file menu.lst. Back to my problem.

That's because you have grub 2 in Karmic, not grub 1 (legacy grub). Have a look at the link again and follow the instructions for grub 2. If you have any problems, post back and I'll take you through it.

---

