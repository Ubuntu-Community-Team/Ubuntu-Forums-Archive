---
title: "Bootloader Problem"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by rickyardo on 2005-02-13
I currently have a system with Windows XP and White Box Linux installed.  I am using Grub bootloader.  I installed it with my White Box install.  The boot loader is located on the MBR.  When i install Ubuntu, i am unable to get it to update grub.  What steps should i take in order to remedy this problem.  any help is appriciated.  thanks.

---

### Post by m4ng0 on 2005-02-13
First of all check if
/boot/grub/menu.lst
is correct. Then type:
sudo grub
which gives you grub prompt ("grub>"). Now you have to tell grub which partition contains the boot directory. E.g.:
grub> root (hd0,2)
You have to insert the partition where your Ubuntu boot directory lives. Remember that grub name conventions are different from Linux: for example
/dev/hda1 is (hd0,0) (if hda is your first HD)
/dev/hdb3 is (hd1,2) and so on.
To install grub on the MBR you type:
grub> setup (hd0)
where hd0 means your first HD (hd1 means the second...). Now you can quit and try to reboot your system.

---

### Post by rickyardo on 2005-02-13
[QUOTE=m4ng0]First of all check if
/boot/grub/menu.lst
is correct. Then type:
sudo grub
which gives you grub prompt ("grub>"). Now you have to tell grub which partition contains the boot directory. E.g.:
grub> root (hd0,2)
You have to insert the partition where your Ubuntu boot directory lives. Remember that grub name conventions are different from Linux: for example
/dev/hda1 is (hd0,0) (if hda is your first HD)
/dev/hdb3 is (hd1,2) and so on.
To install grub on the MBR you type:
grub> setup (hd0)
where hd0 means your first HD (hd1 means the second...). Now you can quit and try to reboot your system.[/QUOTE]
 That is just the problem.  Grub's menu.lst does not get updated with the new menu option.  I dont know what the menu information should say either.  I have edited the menu.lst to customize other menu options.  however am lost when it comes to creating a whole new entry.  Ubuntu is loaded on the fourth partition of the first drive.
thanks

---

### Post by m4ng0 on 2005-02-13
[QUOTE=rickyardo]That is just the problem.  Grub's menu.lst does not get updated with the new menu option.  I dont know what the menu information should say either.  I have edited the menu.lst to customize other menu options.  however am lost when it comes to creating a whole new entry.  Ubuntu is loaded on the fourth partition of the first drive.
thanks[/QUOTE]

Make sure you are using Ubuntu grub and not White Box Linux one... just to be sure, boot Ubuntu and then install grub as I told you before. Since your Ubuntu partition is the fourth on the first drive, type:
sudo grub
grub> root (hd0,3)
grub> setup (hd0)

Once you have installed grub, you don't have to reinstall it when you edit menu.lst.

If you want to add a new entry in menu.lst, things depend on which OS you want to boot. If you have problems booting the other Linux distro, assuming that its partition is the second one of your first drive, you can type:
title  Other Linux Distro
root (hd0,1)
kernel /boot/other-distro-kernel root=/dev/hda2 [other kernel parameters if needed]
boot

If you use a initrd file you have to add also
initrd /boot/other-distro-initrd
between kernel and boot.

---

