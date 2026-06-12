---
title: "How do I uninstall ubuntu?"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by andrewwg94 on 2008-09-20
I want to completely remove it, and install it again. How do I go back to the windows boot-loader? I don't have my Windows XP CD because windows was pre-installed on my PC.

---

### Post by Neo_The_User on 2008-09-20
So you want to re-install Ubuntu? Put in the Ubuntu live cd into your CD-ROM drive and you should be able to graphically re-install Ubuntu on your computer. It will overwrite your current distribution and any other OSes you might have on your computer if you decide the "Guided - Use Entire Disk" option on Step 3 or Step 4 of the installation. If you installed Ubuntu and didn't select that option the first time you installed it, restart your computer and hit the "Esc" button (escape button) on your keyboard when it says something about grub. Grub allows you to select the kernel version, operating system, and distribution you want to run on your system. If you used the entire disk during the first time you installed Ubuntu, the windows operating system will not show up in the menu.lst file on start-up.

(might not need this information at all but the menu.lst file that has all the options you can select is located at /boot/grub/menu.lst)

---

### Post by andrewwg94 on 2008-09-20
> **Neo_The_User said:**
> So you want to re-install Ubuntu? Put in the Ubuntu live cd into your CD-ROM drive and you should be able to graphically re-install Ubuntu on your computer. It will overwrite your current distribution and any other OSes you might have on your computer if you decide the "Guided - Use Entire Disk" option on Step 3 or Step 4 of the installation. If you installed Ubuntu and didn't select that option the first time you installed it, restart your computer and hit the "Esc" button (escape button) on your keyboard when it says something about grub. Grub allows you to select the kernel version, operating system, and distribution you want to run on your system. If you used the entire disk during the first time you installed Ubuntu, the windows operating system will not show up in the menu.lst file on start-up.

(might not need this information at all but the menu.lst file that has all the options you can select is located at /boot/grub/menu.lst)
I have to uninstall it first because i want to move files around from 2 hard drives. so, i have to be able to use the windows boot-loader.

---

### Post by Neo_The_User on 2008-09-20
To admins: Please do not ban me because of this post. I am trying to be as serious and as helpful as possible. I DID NOT post any malicious commands and made it obvious that this WILL ERASE UBUNTU / UNINSTALL IT MEANING LOSS OF FILES

Well I can't post the command here because it's against the rules but deleting your linux partition (meaning loss of files) would erase Ubuntu (not exactly uninstall it.)

Another thing you could do which is pretty safe is to make a copy of the menu.lst file and save it to your flash drive and take out the part in the file that says

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5958022a-509a-4730-9161-4ddbda53f024 ro
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5958022a-509a-4730-9161-4ddbda53f024 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

That will make it invisible on the boot loader.

Option 3:

[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)
[B][U]
CAUTION: Also never try to do this while you put windows into hibernation mode. You will corrupt all of your files. -scole[/U][/B]

---

### Post by jdong on 2008-09-20
Hi andrewwg94,

Typically the removal of Ubuntu requires the windows CD in order to access the recovery console for the "fixmbr" tool which removes GRUB and puts back the Windows bootloader. You may find for download bootable recovery console disk images and CD images which will enable you to access this tool. First run fixmbr/fixboot from such a CD to make sure that Windows boots okay, then you can just delete the Ubuntu partition within Windows.

---

### Post by Partyboi2 on 2008-09-20
You could try using  [[COLOR=Blue]supergrub [/COLOR]]("http://www.supergrubdisk.org/")to fix the mbr

---

