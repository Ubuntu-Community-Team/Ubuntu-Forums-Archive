---
title: "Install w/o Changing Grub Settings?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by klausner on 2010-05-13
Is there a way to do an install from the iso image to a new disk (USB or whatever), without changing the grub settings on the systems existing hard drive?

Every time I try to do a full install to a USB stick, it hoses grub on my hard disk, even though I specify the partitioning during the install, and leave /dev/sda untouched. This has happened now with both Karmic and Lucid.

FWIW, I'm still using grub-0.97.

---

### Post by fuzzyworbles on 2010-05-13
my 2 cents: don't install a full-blown distro on a stick. get something reasonable like puppy or damn small linux.

---

### Post by klausner on 2010-05-13
That might have made sense when the sticks were only 64MB or so in size. But with 8GB+, why not install the whole enchilada?

Anyway, that still leaves my original question.

---

### Post by darkod on 2010-05-13
Yes. In the ubuntu installer, when you reach the last screen (before clicking Install), click on Advanced.

That will open a window where you can select grub2 install location (the disk or a specific partition although that's not recommended), OR you can uncheck installation of grub2 completely.

You are perfectly right, once you have any grub1/grub2 on your hdd, any future linux install should not install grub. You just add the new OS in the existing. Unless of course, you decide you prefer using the newer grub, like in this case 10.04 comes with grub2.

---

### Post by klausner on 2010-05-13
> **darkod said:**
> Yes. In the ubuntu installer, when you reach the last screen (before clicking Install), click on Advanced.

That will open a window where you can select grub2 install location (the disk or a specific partition although that's not recommended), OR you can uncheck installation of grub2 completely.

You are perfectly right, once you have any grub1/grub2 on your hdd, any future linux install should not install grub. You just add the new OS in the existing. Unless of course, you decide you prefer using the newer grub, like in this case 10.04 comes with grub2.

Excellent!! That's exactly the fix. never even noticed there was an advanced option on that screen.

Thanks a lot! \\:D/

---

