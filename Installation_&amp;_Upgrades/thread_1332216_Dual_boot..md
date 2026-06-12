---
title: "Dual boot."
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by lover_of_sc on 2009-11-20
I guys,

I currently have ubuntu 9.10 installed on my Sony Vaio W-series netbook, just love Ubuntu!! Although I would like to install Windows XP as a dual boot - this since some programs thast I used before doesn't support Linux. (Tried WINE but that didn't do the trick) 

I have no CD/DVD rom as it is a netbook.

I have a Windows XP version stored as a DAT file, but I don't know how to make a bootable USB stick out of that?

Also,if I do manage to do that, what do I do next??

I assume that I need to create a small partition of FAT32, then reboot the computer (booting from the XP USB stick)

Then install XP on the FAT32 partition.

I guess that Windows installation will wipe out my GRUB so maybe use the ubuntu bootable USB afterwards and restore the GRUB system?

Soooo many questions... Sorry guys. Hope someone can help?

/Regards Anders

---

### Post by darkod on 2009-11-20
Yes, you got it. The one thing to consider is that XP usually likes to be on the first partition, beginning of the drive. If you shrink with Gparted you might want to make space in front of linux, not after.
If it doesn't work with the DAT just find XP CD to borrow, and look for tutorials how to create bootable USB with that. Shouldn't be hard.
You are right, you will have to restore grub2 after XP is installed.

---

