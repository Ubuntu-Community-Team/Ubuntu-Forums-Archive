---
title: "Installing Windows AFTER Ubuntu"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by fatal_error on 2006-03-22
Hello forums,

I'm in the situation where I have ubuntu installed, it uses all of my 80 GB HDD. Now I plan to install WinXP Prof. (for some gaming purposes only hehe), and all HowTo's I can find deal with "first install windows, than ubuntu". I have figured that in theory it should work the other way too, so if someone can confirm that my way of installing things would work or point me to errors that I've overseen I'd be grateful.

So here is how I would commence:

- Resize my "/" partition, thus freeing up approx. 20 Gigs for WinXP (I guess fdisk or the like are capable of resizing?)
- Installing WinXP in the free partition using NTFS (i wont need write access, the XP system is solely for gaming). Will it be possible to install WinXP to a primary partition that is NOT the first primary partition (as this is used by "/boot")?
- The windows install will surely overwrite GRUB. Is there a "rescue" option in the ubuntu installation CD menu, or some other way how i could possibly fix the MBR and reinstall GRUB so that i'm able to boot into both OS's? Thats my main concern in this installation procedure, so any comments on this are mostly appreciated.

That's it, suggestions/tips are welcome!

---

### Post by pitr on 2006-03-22
[quote=fatal_error]
- Resize my "/" partition, thus freeing up approx. 20 Gigs for WinXP (I guess fdisk or the like are capable of resizing?)
[/quote] I think parted is what you want to use for resizing partition. Just remember to backup anything you have that is important before trying.
[quote=fatal_error]
- Installing WinXP in the free partition using NTFS (i wont need write access, the XP system is solely for gaming). Will it be possible to install WinXP to a primary partition that is NOT the first primary partition (as this is used by "/boot")?
[/quote] That should work
[quote=fatal_error]
- The windows install will surely overwrite GRUB. Is there a "rescue" option in the ubuntu installation CD menu, or some other way how i could possibly fix the MBR and reinstall GRUB so that i'm able to boot into both OS's? Thats my main concern in this installation procedure, so any comments on this are mostly appreciated.
[/quote] You could use the rescue mode and then chroot over to your ubuntu system and do a manual grub installation.

---

### Post by fatal_error on 2006-03-22
Thanks for the quick reply...

Currently im checking out parted...if (hopefully) everything went well, I will post the precise way how I did my install...maybe this could be useful for someone else one day.

---

### Post by cotcot on 2006-03-22
I am not sure about installing XP not on the first partition. I think you hide the ubuntu partition (with a live CD or fdisk or Ranish ...); install XP (letting install its bootloader in the MBR.

You can overwrite the XP boot loader : see [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=messed+MBR](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=messed+MBR)

---

