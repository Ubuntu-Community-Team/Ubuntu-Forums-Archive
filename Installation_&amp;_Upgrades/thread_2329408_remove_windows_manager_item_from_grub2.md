---
title: "remove windows manager item from grub2"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by RichardET on 2016-07-01
I reformatted the whole 1 TB disk for Mate;  but the menu still lists a dummy windows manager selection;  Do I need to re-install linux, destroy all partition boundaries first?  It must have used an existing partition for some windows restore as the swap, but I thought a reformat removed all traces of a boot flag?

---

### Post by Impavidus on 2016-07-01
I'm not entirely sure what you did, but after all Windows boot files have gone, you have to run```
sudo update-grub
```to rebuild the menu.

---

### Post by RichardET on 2016-07-01
> **Impavidus said:**
> I'm not entirely sure what you did, but after all Windows boot files have gone, you have to run```
sudo update-grub
```to rebuild the menu.

doesn't seem to handle it - very strange to me:

rthornton@Inspiron-3655:~/Desktop$ sudo update-grub2
[sudo] password for rthornton: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-41-generic
Found initrd image: /boot/initrd.img-4.2.0-41-generic
Found linux image: /boot/vmlinuz-4.2.0-16-generic
Found initrd image: /boot/initrd.img-4.2.0-16-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

---

### Post by sudodus on 2016-07-01
You seem have an EFI partition, and in that partition you have files for booting Windows.

If you also format the EFI partition, and fix the booting afterwards, for example with Boot Repair, you should get rid to the leftovers from Windows. A maybe better alternative would be to identify and remove the files belonging to Windows (for example the directory /dev/sda1@/EFI/Microsoft/ and the files in it).

As usual when editing the partition table and the boot system, ***it is good to have an up to date backup***, so that you can restore your system, if you happen to remove or damage vital parts of the system.

---

### Post by RichardET on 2016-07-01
I did the radical approach - use the installer of OpenBSD to reformat the who drive BSD4.2, then re-installed Ubuntu Mate 16.04;  problem solved.

---

### Post by sudodus on 2016-07-01
Yes, if you have not installed and tweaked a lot in your linux system, reinstalling is often the best method :-)

---

