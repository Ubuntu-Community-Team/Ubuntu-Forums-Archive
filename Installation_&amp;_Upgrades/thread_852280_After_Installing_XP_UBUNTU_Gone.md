---
title: "After Installing XP UBUNTU Gone"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by mostafamehiri on 2008-07-07
[CENTER][FONT=Comic Sans MS][SIZE=4][COLOR=RoyalBlue]I have UBUNTU 8.04
And
After installing XP  UBUNTU didn't show up
and i am sure i haven't formated the UBUNTU partition
 i need help and i don't want to install it again
because i have files that i need in that partition !!!![/COLOR][/SIZE][/FONT]
[/CENTER]

---

### Post by Rallg on 2008-07-07
This is normal. When you install Ubuntu after Windows, the Ubuntu boot loader (Grub) detects Windows. But when you install Windows after Ubuntu, the Windows boot loader does not detect Ubuntu (or any Linux), and it over-writes Grub. That makes Ubuntu un-bootable, for now.

If you use the Ubuntu live CD (or any Linux live CD), you can look at your disk drive partitions, and see that the Ubuntu files are still there.

You need to re-install Grub, WITHOUT re-installing all of Ubuntu. There are other forum posts on that subject. Actually, I found a helpful explanation here:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
Be sure to read ALL of the above page, before you do anything. The code will work "as written" for some systems, but not others. The rest of the page tells you what changes you might need to make, for your own system.

---

