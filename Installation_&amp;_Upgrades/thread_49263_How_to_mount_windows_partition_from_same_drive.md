---
title: "How to mount windows partition from same drive"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by carlos_ on 2005-07-15
Hi,

I am dual-booting Ubuntu and XP from the same physical drive.  Ubuntu was installed after the windows install so I thought it would have added the windows partition to be automatically mounted.  I'd like to access the windows partition from Ubuntu and thought it might be automounted under "/mnt" as it is in my Mandriva installation, but I don't see it.  Am I looking in the wrong place?  Is it not automounted in which case I'd have to do some fstab editing?.  If I do have to edit fstab, what is the best way to see the mapping of the drives/partitions?

TIA,
Carlos

P.S. I'm not a complete newbie, but am new to Ubuntu.

---

### Post by DancingSun on 2005-07-15
You'll need to modify the fstab file to mount the windows partition on startup:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Edit: That guide is very useful, make sure you bookmark it!

---

### Post by carlos_ on 2005-07-15
Thanks DancingSun... exactly what I was looking for.  The Starter Guide seems very complete for common tasks... I'll definitely spend some time exploring it.

-Carlos

---

### Post by Aikon- on 2005-07-15
[QUOTE=carlos_]Hi,

I am dual-booting Ubuntu and XP from the same physical drive.  Ubuntu was installed after the windows install so I thought it would have added the windows partition to be automatically mounted.  I'd like to access the windows partition from Ubuntu and thought it might be automounted under "/mnt" as it is in my Mandriva installation, but I don't see it.  Am I looking in the wrong place?  Is it not automounted in which case I'd have to do some fstab editing?.  If I do have to edit fstab, what is the best way to see the mapping of the drives/partitions?

TIA,
Carlos

P.S. I'm not a complete newbie, but am new to Ubuntu.[/QUOTE]
 This is exactly what I am trying to do.. only Ubuntu refuses to play nicely with XP...

XP was installed first, then I installed Ubuntu.. when it rebooted the first time (i.e. eject cd, press return), I got this:

"Error loading operating system".. my guess is from the GRUB bootloader.

The only way I know how to fix it (and it does fix it.. works every time) is to set the NTFS partition as the drive's active partition using QtParted (on my Knoppix cd), and then XP boots fine, no problems, no complaints.

AGH

---

### Post by DancingSun on 2005-07-15
[QUOTE=Aikon-]This is exactly what I am trying to do.. only Ubuntu refuses to play nicely with XP...

XP was installed first, then I installed Ubuntu.. when it rebooted the first time (i.e. eject cd, press return), I got this:

"Error loading operating system".. my guess is from the GRUB bootloader.

The only way I know how to fix it (and it does fix it.. works every time) is to set the NTFS partition as the drive's active partition using QtParted (on my Knoppix cd), and then XP boots fine, no problems, no complaints.

AGH[/QUOTE]

If you set the NTFS as the active partition, you should be able to get dual boot working correctly on the first try.  I think I marked both the "/" and the ntfs partition as the primary partition, and with NTFS as the boot partition, then installed Ubuntu.  Everything just worked afterwards.

---

