---
title: "&quot;Grub Customizer&quot; does not change Grub menu."
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2014-05-08
My harddrive has a partition for Ubuntu 13.1, Ubuntu 12.4 and Windows 8.1.
Grub was adapted by "Grub Customizer" with 13.1 as first menu option, 12.4 as second, Windows as third, etc.
After updating the latest Windows 8.1 I lost Grub and the possibility to load Ubuntu.:confused: 			

		
 	
This problem is now fixed, but the menu order has changed and I can't anymore customize the menu with "Grub Customizer".
In "Grub Customizer" the menu order and background are still the same as before, but after saving Grub does not change.
It looks like Grub reads the menu on another place than that saved by "Grub Customizer".
Thanks for helping me to fix this problem.

---

### Post by grahammechanical on 2014-05-08
You have two installations of Ubuntu. Each installation will have a Grub configuration file. Which Grub configuration file is Grub looking to? If you want Ubuntu 13.10 to be first in the list of Grub boot options load into Ubuntu 13.10 and run these two commands.

```
sudo update-grub
```

Watch the printout. You should see 13.10 at the top of the list with 12.04 and Windows 8.1 bootloader coming after. Now run

```
sudo grub-instal /dev/sda
```

Alternatively, load into Ubuntu 13.10 and run Grub Customiser again and this time not only Save but find in the menu structure Install to MBR and run  that.

Regards.

---

### Post by jj.wauters on 2014-05-09
[SIZE=3]Updating grub from within 13.1 did not show me Ubuntu 13.1 at the top:[/SIZE]
[I]Generating grub.cfg ...
using custom appearance settings
Found background image: /home/jan/Pictures/wallpaper1.jpg
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda9
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda9
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda9
Found linux image: /boot/vmlinuz-3.11.0-20-generic
Found initrd image: /boot/initrd.img-3.11.0-20-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-17-generic
Found initrd image: /boot/initrd.img-3.11.0-17-generic
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda9
Adding boot menu entry for EFI firmware configuration
done
[/I][SIZE=3]So I did not continue the install procedure.
However the alternate method worked fine and now it's all like before.

Many thanks for the quick and efficient reply[/SIZE]

---

### Post by grahammechanical on 2014-05-09
I am glad it worked. By the way, when we run update-grub from Ubuntu it is normal for the Grub printout not to label the version of Ubuntu we are running the command from. This is what I see when I run sudo update-grub

> Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-23-generic
Found initrd image: /boot/initrd.img-3.13.0-23-generic
Found linux image: /boot/vmlinuz-3.13.0-21-generic
Found initrd image: /boot/initrd.img-3.13.0-21-generic
Found linux image: /boot/vmlinuz-3.13.0-16-generic
Found initrd image: /boot/initrd.img-3.13.0-16-generic
Found linux image: /boot/vmlinuz-3.13.0-15-generic
Found initrd image: /boot/initrd.img-3.13.0-15-generic
Found linux image: /boot/vmlinuz-3.13.0-14-generic
Found initrd image: /boot/initrd.img-3.13.0-14-generic
Found linux image: /boot/vmlinuz-3.13.0-2-generic
Found initrd image: /boot/initrd.img-3.13.0-2-generic
Found linux image: /boot/vmlinuz-3.13.0-1-generic
Found initrd image: /boot/initrd.img-3.13.0-1-generic
Found linux image: /boot/vmlinuz-3.12.0-7-generic
Found initrd image: /boot/initrd.img-3.12.0-7-generic
Found linux image: /boot/vmlinuz-3.12.0-4-generic
Found initrd image: /boot/initrd.img-3.12.0-4-generic
Found linux image: /boot/vmlinuz-3.12.0-3-generic
Found initrd image: /boot/initrd.img-3.12.0-3-generic
Found linux image: /boot/vmlinuz-3.12.0-2-generic
Found initrd image: /boot/initrd.img-3.12.0-2-generic
Found linux image: /boot/vmlinuz-3.12.0-1-generic
Found initrd image: /boot/initrd.img-3.12.0-1-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
Found Ubuntu 14.04 LTS (14.04) on /dev/sda2
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda5
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda6
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sda7
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sda9
Found Ubuntu Utopic Unicorn (development branch) (14.10) on /dev/sdb1
Found Ubuntu Trusty Tahr (development branch) (14.04) on /dev/sdb5
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb9

As you can see I have several installs of Ubuntu but the one I am running sudo update-grub from is not labelled. It will appear in the Grub Menu as "Ubuntu." The printout is showing what the other installs of Ubuntu will be labelled. Although it does not show that some of those installs are flavours of Ubuntu.

Regards.

---

