---
title: "Windows Xp Partion Hid Ubuntu"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by GroogFish on 2009-11-21
When I installed Ubuntu I left space to install windows xp as well. I just installed windows xp in the free space that I left and now it doesn't give me the option to boot ubuntu when I restart. It just goes straight to xp.

Are their any settings I need to change so that ubuntu will show up?

---

### Post by darkod on 2009-11-21
It's still there but windows wrote their own bootloader on the disk MBR and it ignores Ubuntu. :)

Do you have 9.10 installed? Because the restore grub procedure is different for 9.04 and before, and for 9.10.

---

### Post by GroogFish on 2009-11-21
That's what I had expected. 
 
I have 9.04 because 9.10 gave me errors both times I installed it.

---

### Post by darkod on 2009-11-21
I think this should help:
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

That's for grub1. If you want to make sure that you have grub1 after you start with the Live CD look in /boot/grub folder. If there is file menu.lst then it's grub1. Grub2 doesn't use menu.lst

---

### Post by GroogFish on 2009-11-21
It worked! Except now I can't login to windows xp. I think their may already be a topic on it though, I'll check that out ^^

---

### Post by darkod on 2009-11-21
Adding XP to grub1 shouldn't be a problem, in menu.lst. Adding manually to grub2 is much more hassle and sometimes even impossible.

---

