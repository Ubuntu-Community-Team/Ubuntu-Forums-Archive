---
title: "Dual boot Fiesty/Fedora"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by gaaslight on 2007-07-28
I just installed Fedora 7 x86_64 on the free space left on my hard drive. I choose the "do not install GRUB" option. I assume that I can edit menu.lst in my Ubuntu Boot/Grub folder to dual boot both OS's. Has anyone ever tried doing this? Can it work? If it can, please tell me how.

---

### Post by tuxcantfly on 2007-07-28
Well I'm dual-booting Ubuntu and Sabayon, (should be the same process as with Fedora though), and this worked fine for me:

I let Sabayon install GRUB to the MBR, so there was no menu for Ubuntu

I then went into the GRUB commandline (press c), and entered this:
```

root (hd0,2)
configfile /boot/grub/menu.lst
```

Which brought me to Ubuntu. I then re-installed the Ubuntu bootloader to the MBR:

```
sudo grub-install /dev/sda
```

And opened up /boot/grub/menu.lst, uncommented the "hiddenmenu" option, set the "timeout" to 10, and added the following lines at the end:

```
title Sabayon
root (hd0,3)
configfile /boot/grub/menu.lst
```

Then I mounted the Sabayon drive, edited /boot/grub/menu.lst on the Sabayon drive, and set the "timeout" to 0

This way, I now see the Ubuntu GRUB menu, and have a 10 second timeout in which I can select between Ubuntu and Sabayon

---

