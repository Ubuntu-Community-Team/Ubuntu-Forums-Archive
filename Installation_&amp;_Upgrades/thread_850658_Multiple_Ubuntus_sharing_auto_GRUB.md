---
title: "Multiple Ubuntus sharing auto GRUB"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by Habbit on 2008-07-05
Is there a way for multiple Ubuntu installation (say, one Ubuntu and one Kubuntu, both 8.04) to share one GRUB installation with automatic updating of the GRUB menu? For reasons that are difficult to explain here, I'd like the setup mentioned instead of installing both desktop environments in a single system, but I'd like the two installations to share the /boot partition. This might cause conflicts amount their "grub" packages and particularly with the menu configuration files.

---

### Post by wolfen69 on 2008-07-05
grub will automatically update as each ubuntu is added. install away!

---

### Post by Miljet on 2008-07-05
As Wolfn69 says, each time you install another Ubuntu (or any Linux) distribution GRUB will update itself. However, it will use the menu.lst in the /boot/grub directory of the last distro you install.

If however you mean to install GRUB on its own partition, that is indeed possible. That way your GRUB is not tied to any particuliar distribution. Also the easiest way to accomplish the same thing is to make a GRUB boot floppy, if your machine has a floppy drive.

Detailed instructions for either of these options can be found here:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
This is by far the best tutorial on GRUB that I have found. When I first started experimenting with GRUB, I printed out the entire tutorial (all 116 pages) for reference.

Good luck.

---

### Post by Habbit on 2008-07-06
> **wolfen69 said:**
> grub will automatically update as each ubuntu is added. install away!

The problem is that kubuntu does not feel like collaborating: if I set the /boot partition to my already existing /boot during my installation and ask it not to format, it shows a rather scary message "even though the partition won't be formatted, all system folders like /bin will be deleted". I'd very much rather not delete my kernel, though I suppose they will be the same for both flavors of Ubuntu...

---

