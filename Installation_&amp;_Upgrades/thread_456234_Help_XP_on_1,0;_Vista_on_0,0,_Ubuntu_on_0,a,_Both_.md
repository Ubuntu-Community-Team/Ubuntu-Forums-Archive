---
title: "Help: XP on 1,0; Vista on 0,0, Ubuntu on 0,a, Both Vista and XP bootloaders on 1,0."
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by bdjacobson3 on 2007-05-27
Where should I install my grub to?

Just typing this out has helped me arrange it a bit; I'm thinking I should point the first BIOS boot device to hd0, install grub to hd0, and then have the Vista part of grub be pointing to hd1,0?

Edit:

I tried sudo grub-install hd0 but it can't find a /boot folder.

---

### Post by confused57 on 2007-05-27
> **bdjacobson3 said:**
> Where should I install my grub to?

Just typing this out has helped me arrange it a bit; I'm thinking I should point the first BIOS boot device to hd0, install grub to hd0, and then have the Vista part of grub be pointing to hd1,0?

Edit:

I tried sudo grub-install hd0 but it can't find a /boot folder.

Check out the "Grub Page" section on this website:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
it'll explain grub's numbering system & beaucoups of info on grub

You might want to boot up the live cd(or an installed version), open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L", you might want to designate to the side  which partition contains XP, Vista, data, etc.

You can use the live cd to install grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I believe the correct syntax is "sudo grub-install /dev/hda", or whatever is your (hd0) drive.

---

