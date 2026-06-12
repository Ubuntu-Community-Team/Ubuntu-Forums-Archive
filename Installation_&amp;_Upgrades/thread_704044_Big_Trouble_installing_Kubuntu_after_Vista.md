---
title: "Big Trouble installing Kubuntu after Vista"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by Redlazer on 2008-02-21
Ive been having one hell of a time getting Kubuntu installed along with Vista.

I have it installed already on my laptop, which went off without a hitch. Im doing essentially the same thing as on my laptop, which is splitting the main drive (windows C:\ drive) into requisite Kubuntu drives. 

Everytime i install Kubuntu (any way - manually, guided, without Grub, with Grub, etc) both OS's get hosed, and neither is bootable.

The Vista install is especially upset, and im not even able to repair the MBR (without some mysterious rebooting voodoo).

When i repaired the MBR once so far, with Vista, it of course hosed the GRUB bootloader.

Thanks for your help!

-Fred

---

### Post by jrusso2 on 2008-02-21
What are you using to shrink the vista drive?  From what I have read the best way to do this is withing vista using the vista disk manager.  I have read that using gparted to shrink vista will make it unbootable?

I don't have vista so I have not tried it myself yet

---

### Post by iheartubuntu on 2008-02-22
I still consider myself new to linux, but ive been reading that HP computers running Vista are difficult to make changes to. Formatting, resizing, etc the HD on a new HP system screws things up.

---

### Post by Redlazer on 2008-02-22
Actually, one of the trademark lucky reboots fixed the problem - it suddenly works now.

Thanks for your help!

What appears, in detail, is that after the first Kubuntu install that hosed the OS, i reformatted the ext3 drive and installed it again, and that, magically, fixed the problem.

Thanks for your help : )

-Fred

---

