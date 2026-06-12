---
title: "ubuntu on external hard drive?"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by nthali on 2010-11-05
Alright, after my rather expensive previous debacle, before i commit the same mistake again, i'd like to ask:
is there a way to do a full ubuntu install on an external hard drive, and then have the option to boot from my normal laptop hard drive into Windows XP, or into Ubuntu from my external drive?
i had read before somewhere that the master boot record needs to be on the primary 
disk. 
thanks,
Nilesh

---

### Post by dino99 on 2010-11-05
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by nthali on 2010-11-21
sorry for getting back after such a long time, but i looked through the installation documentation, and i guess didn't find what i wanted to find :)
the section on booting from usb was geared towards older computers that didn't have the option. i also would prefer not to use a separate CD etc.
i once again installed ubuntu 10.10 on an external hard drive partition (which is the second partition on that drive, the first one being NTFS), then restarted, and at boot time, chose the "boot from usb" option, and it didn't find ubuntu and just booted up my XP.
any other options to be able to install on an external hard drive and then either dual boot, or specifically boot ubuntu from the external drive?
Thanks,
Nilesh

---

### Post by oldfred on 2010-11-21
You have to be sure to install grub to sdb or whatever the external is. You do not want to modify the MBR in sda, so you can still boot the windows on the internal drive.

So many people had the problem the author of the boot script posted this page on reinstalling boot loaders.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If you want to know what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by C.S.Cameron on 2010-11-21
You can install to the USB drive with your internal drive plugged in.
When you get to partitioning use the manual method.
Add new partitions as you require.
Select the root of your external for grub, ie sdb not sdb2.

If you already have a bootable USB drive, boot from it and do a update-grub.
It will find your internal O/S and add it to your grub menu.

---

