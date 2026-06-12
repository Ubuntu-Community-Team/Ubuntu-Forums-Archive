---
title: "Installing Grub2 on a floppy"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rumpty on 2009-10-08
Tried installing grub2 on a floppy disc with the command
sudo grub-install /dev/fd0
but there is an error message "grub-probe: error: cannot find a GRUB drive for /dev/fd0. Check your device map

My device map has (fd0) /dev/fd0 in it.
Should that command above work?

---

### Post by VMC on 2009-10-08
If you know about Super Grub Disk, they now have a floppy version, found [**here**]("http://prdownload.berlios.de/supergrub/grub-rescue-floppy.img").

Version121 is for grub2

---

### Post by Rumpty on 2009-10-08
Yes, I have used Super Grub Disk, so that's good if there is a version for Grub2. I'll investigate that.

But should that command I ran work in Karmic Koala? It certainly works in Jaunty with Grub1.

---

