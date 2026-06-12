---
title: "Grub error 29 (disk write error) after edgy install"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by pgilmon on 2006-11-13
Hi all.

I experienced the following problem when installing ubuntu in a P-III 800MHz with an 80 Gb IDE disk:

After installing Edgy in the primary disk (the only HDD in the system) I was unable to boot either ubuntu or the previously installed XP. I always got error 29 from GRUB (disk write error). I tried installing ubuntu as the only operating system in the whole disk (letting the installer wipe out the entire  disk), and also changing master/slave with the CD and reinstalling again, but I always ended up with the same problem.

I realized that the recovery option worked allright, then found that the problem was realted to the 'savdefault' GRUB command. The solution was just booting with the recoery option and eliminating any reference to the grub command 'savedefault' in /boot/grub/menu.lst 

I post this here just in case anyone has the same problem, since I wasn't able to find the solution by either googling or searching in these forums.

---

### Post by devinfo.net on 2007-03-15
Hi,

I've had the same problem on my Compaq EVO N1020v.
But I had to also comment out the line 'makeactive' in /boot/grub/menu.lst.
XP was then booting again without problems.

Thanks.

---

