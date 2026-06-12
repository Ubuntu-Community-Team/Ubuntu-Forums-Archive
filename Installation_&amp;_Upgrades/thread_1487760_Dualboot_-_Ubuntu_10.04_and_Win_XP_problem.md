---
title: "Dualboot - Ubuntu 10.04 and Win XP problem"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by a546 on 2010-05-19
I recently upgraded from Karmic Koala to Lucid Lynx and after the next reboot I couldnt boot Win XP. When i choose it on the bootloader, the screen goes black for a few seconds and then the Bootmenu returns. I can only choose Ubuntu 10.04.

---

### Post by oldfred on 2010-05-19
Please post the results.tx from this script. It will show just about everything related to booting your system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If you know that you installed grub to the windows partition not just drives:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by supriyo on 2010-05-19
I just installed Lucid Lynx on my Pentium 4,2.66Ghz machine. with 250GB HDD, ubuntu was as bual booting with Windows XP SP3 installed. I updated the Lucid and rebooted the system after update there was no OS choice was shown either XP or Linux. Only Memory test were shown.
I tried to mount and reinstall the GRUB from Live CD.but same problem persisted.Please help me out:(.

---

### Post by oldfred on 2010-05-19
supriyo - Welcome to the forums

But this is A546's thread on his boot problem. Unless you problem is identical, please open your own thread. (In fact I think I told a546 the same in another thread). Boot problems while similar vary so much because everyone has different configurations. You can also help in your new thread by posting the boot info script I have a link to in post #2. It gets too confusing on who's boot script we are looking at and comment on when more than one is in the same thread.

---

### Post by a546 on 2010-05-20
> **oldfred said:**
> Please post the results.tx from this script. It will show just about everything related to booting your system.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If you know that you installed grub to the windows partition not just drives:
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Here.

---

### Post by darkod on 2010-05-20
> **a546 said:**
> Here.

Use this fix on your XP system partition /dev/sda1. So you need to repair the partition #1 on the disk /dev/sda.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After that XP should boot fine.

---

### Post by a546 on 2010-05-20
> **darkod said:**
> Use this fix on your XP system partition /dev/sda1. So you need to repair the partition #1 on the disk /dev/sda.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After that XP should boot fine.

Works, thanks a lot. : )

---

### Post by supriyo on 2010-05-20
> **oldfred said:**
> supriyo - Welcome to the forums

But this is A546's thread on his boot problem. Unless you problem is identical, please open your own thread. (In fact I think I told a546 the same in another thread). Boot problems while similar vary so much because everyone has different configurations. You can also help in your new thread by posting the boot info script I have a link to in post #2. It gets too confusing on who's boot script we are looking at and comment on when more than one is in the same thread.
Ok here is my boot log results after I tried FIXMBR command in XP and booted in XP but did no harm to linux partition ..I will also post the original state I faced after I tried to remount the OS.

---

### Post by darkod on 2010-05-20
> **supriyo said:**
> Ok here is my boot log results after I tried FIXMBR command in XP and booted in XP but did no harm to linux partition ..I will also post the original state I faced after I tried to remount the OS.

Hmmm... as if grub2 never detected ubuntu and XP. No entries in grub.cfg. You should be able to get everything up and running by booting into ubuntu live mode and in terminal executing:

sudo mount /dev/sda8 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys

sudo grub-install --root-directory=/mnt/ /dev/sda
sudo chroot /mnt update-grub

sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc

After running the update-grub command pay attention if it reports the ubuntu kernels and XP found. Anyway, after all the commands reboot and see if it worked.

---

### Post by oldfred on 2010-05-20
supriyo you already have your own thread that darko & I both responded to.
[http://ubuntuforums.org/showthread.php?t=1488103](http://ubuntuforums.org/showthread.php?t=1488103)

We are all volunteers here and duplicating information in two threads wastes our time in helping others.

---

