---
title: "Installation freezing at &quot;installing grub package&quot;"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by marlun on 2005-11-16
Hello!

I've got 2 harddrives (hd1, hd2). I want windows on the first one and Ubuntu on the second one. However, everytime I try to install Ubuntu it freezes at the installation of grub packages. 

If I install Windows first on hd1 and then when I install Ubuntu on hd2 theres a boot loader marker on both the windows partition and the Ubuntu partition (they are on two different harddrives).
 
I've tried to remove the boot loader marker (the lightning) from the windows partition and I've tried to remove it from the ubuntu partition and even both at the same time but it allways freezes in the same place.

What is wrong? What can I do?

Thanks in advance!

---

### Post by marlun on 2005-11-16
Hello again,

Now I tried to remove everything and only install Ubuntu on hd1 and not install Windows at all. That didn't work either. :(

---

### Post by stevenrnelson on 2006-03-03
I'm having a similar problem with a single SATA drive, and an nvidida controller. When the installer gets to Installing GRUB bootloader (or something similar to that), the progress bar stops, disk activity stops, and the only way to get anything moving (short of a reboot) is chaing to a virtual console, and kill the apt procs. Then the installer recognizes a failure to install and lets me try to go back to the menu. I also tried Lilo and it it gets 50% through before failing as well. I don't think it's a patience issue, as I waited on that one package for longer than the entire install had taken up to that point.

---

### Post by stevenrnelson on 2006-03-03
Okay, I'm not sure if this makes sense, but here's how I fixed the problem. I moved my IDE optical drive to the secondary IDE port on the motherboard. I didn't think it would be a problem for it to be in the primary slot seeing as the hard drive was (and is) over on SATA, but I guess I was wrong. Can anyone enlighten us as to why this is true?

---

