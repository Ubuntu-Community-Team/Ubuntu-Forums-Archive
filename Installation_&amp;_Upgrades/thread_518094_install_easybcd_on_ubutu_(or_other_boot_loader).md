---
title: "install easybcd on ubutu? (or other boot loader)"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by gimpster123 on 2007-08-05
install easybcd on ubutu? (or other boot loader)


Hello, I'm running Ubuntu Feisty Fawn, and Vista Buisness. They boot from seperate partitions on the same Hard drive.

GRUB has been corrupted, and now the only way to boot into Ubuntu is through a Super Grub disc i made. Vista won't boot at all.

I need to install a new boot manager via linux, as i can't even get into Vista to install from there. Any suggestions?

Thanks,
Gimp

---

### Post by logos34 on 2007-08-05
You could try reinstalling Grub from the [ubuntu live cd]("http://ubuntuforums.org/showthread.php?t=224351"). 

If that fails to solve the problem, try repairing/reinstalling your vista boot loader (using the vista install disc), and then use a program like [EasyBCD]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home") to add ubuntu.

---

### Post by gimpster123 on 2007-08-05
im trying to boot back into vista so i can install a 3rd party boot manager- the downloads are all .exe's :(

---

### Post by logos34 on 2007-08-05
I realize that--that's why I suggested using the vista dvd (if you have one) to restore the bootloader first so you could get into windows.

---

### Post by Computer Guru on 2007-08-07
Boot from the Vista DVD.
Repair Options | Command Prompt:
```
bootrec /fixmbr
bootrec /fixboot
```
 
That should get you into Vista. Once in, download and install [the latest EasyBCD build]("http://neosmart.net/forums/showthread.php?t=642") and use it to add Ubuntu (check the "GRUB isn't installed to the bootsector" box to make it easier).

---

