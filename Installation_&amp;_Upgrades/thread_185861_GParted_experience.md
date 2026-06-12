---
title: "GParted experience?"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by marbleheadman on 2006-06-01
Dapper's new graphical installer looks swell.  The partitioner looks extremely powerful, too.  I'm a bit wary, though, to use it to resize an NTFS partition, given how uncompatible Linux usually can be with them.  Has anyone used parted/GParted to resize a Windows XP/2000 partition?  Is it (relatively) safe?  Did you need to do anything besides a couple of defragmentations first to ensure no data loss?

---

### Post by johnc4510 on 2006-06-01
Back up your data to be safe!!!!

---

### Post by Klaidas on 2006-06-01
When installing breezy, I shrinked Windows's partition. (text-mode installer) and used it for Breezy :)
Now, when installing dapper today, I used Espresso installer to reformat existing Breezy's partition and install dapper on it.

Well, it works! :)
Just make sure partition are unmounted when you do resizing, etc ;)

---

### Post by aysiu on 2006-06-01
johnc4510 is right if you want to be 100% sure your data remains intact.

If you want to be 99.9% sure, don't back it up and then defragment and use GParted. Linux can resize NTFS just fine. It can read off NTFS just fine. It just can't write to NTFS just fine.

---

### Post by marbleheadman on 2006-06-04
OK, cool.  But, before I proceed, does Dapper correctly set up GRUB for booting Windows as well if a Windows partition is detected, or does dual-booting require further configuration?

---

### Post by aysiu on 2006-06-04
[QUOTE=marbleheadman]OK, cool.  But, before I proceed, does Dapper correctly set up GRUB for booting Windows as well if a Windows partition is detected, or does dual-booting require further configuration?[/QUOTE] Yes, it does automatically. I'd say about 99% of the time, it does it correctly. Otherwise, you can still add Windows manually to the boot menu with some help from other forum members.

---

### Post by az on 2006-06-04
All linux partitioners use the same backends.  From what I see on the forums, people tend to have more success partitioning NTFS using *linux* tools than windows tools.


I would say that it is as safe as partitioning can be.

---

### Post by marbleheadman on 2006-06-05
Thanks, guys.  All went well, and now I have a nice Dapper installation to use.

One more question: Dapper successfully mounted both of my Windows partitions (as I requested in the installer) and set them as icons on the desktop.  I want to keep them mounted, but I certainly don't think I'll be using them enough to merit keeping them on my otherwise clear desktop.  As a desktop minimalist, how can I remove the icons from the desktop while still keeping the partitions mounted?

---

### Post by aysiu on 2006-06-05
In Gnome: Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Show Volumes

In KDE: Right-click desktop > Desktop Behavior > File Icons

---

