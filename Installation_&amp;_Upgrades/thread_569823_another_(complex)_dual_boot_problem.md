---
title: "another (complex?) dual boot problem"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by johncf1018 on 2007-10-07
First a little background:  Last week, I only had one hard drive running windows XP.  I successfully installed Ubuntu using wubi to do the virtual install thing.  It ran great and I was able to dual boot without any problems.  I then decided to add an extra hard drive in order to run a proper installation.  It arrived and I installed it.  I thought I'd be thorough, so I started running some diagnostics from a CD seagate included with the hard drive.  Unfortunately this screwed up the first hard drive so I could no longer boot to any OS!   I quickly reinstalled XP on the new drive, and was able gain to gain access to my old files after running testdisk to fix the boot sector.  I'm not able to boot to my original drive, but thats not my problem. 

My problem is, I have installed Ubuntu on a partition of the 2nd hard drive, but am unable to boot it.

The Grub menu has two separate windows XP options to choose from.  The first one boots successfully to my reinstalled copy of windows on the second hard drive.  The 2nd option doesn't boot at all.  There is no option to boot to ubunto.  I tried the instructions I found on this forum for reinstalling grub from the live CD:

sudo grub
find /boot/grub/stage1               This returned the value (hd1,2)
root (hd1,2)
setup (hd0)
quit

...but nothing has changed.  I'm at a loss, and am eager to get back to using Ubuntu!  Any help or insight anyone could provide would be most appreciated!  Thanks!

---

### Post by nawitus on 2007-10-07
You can edit grub by using the command
```

sudo nano /boot/grub/menu.lst

```
You can find all the boot options and edit them. Read the file carefully and edit accordingly. 

this command runs a script to generate menu.lst. Use it and tweak menu.lst until you get what you need AFTER running update-grub.
```

sudo update-grub

```

Type "man update-grub" for more information.

Helpful commands to get information and edit the menu.lst
```

sudo fdisk -l
pico /etc/fstab

```

You can also temporarily edit grub settings by pressing 'e' in the selection. If you need more help, please reply the output of "sudo fdisk -l", and the contents of the file /etc/fstab.

This guide will tell you how to edit grub boot options:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
This will assist you even more:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu)

---

### Post by arkara on 2007-10-07
> **johncf1018 said:**
> First a little background:  Last week, I only had one hard drive running windows XP.  I successfully installed Ubuntu using wubi to do the virtual install thing.  It ran great and I was able to dual boot without any problems.  I then decided to add an extra hard drive in order to run a proper installation.  It arrived and I installed it.  I thought I'd be thorough, so I started running some diagnostics from a CD seagate included with the hard drive.  Unfortunately this screwed up the first hard drive so I could no longer boot to any OS!   I quickly reinstalled XP on the new drive, and was able gain to gain access to my old files after running testdisk to fix the boot sector.  I'm not able to boot to my original drive, but thats not my problem. 

My problem is, I have installed Ubuntu on a partition of the 2nd hard drive, but am unable to boot it.

The Grub menu has two separate windows XP options to choose from.  The first one boots successfully to my reinstalled copy of windows on the second hard drive.  The 2nd option doesn't boot at all.  There is no option to boot to ubunto.  I tried the instructions I found on this forum for reinstalling grub from the live CD:

sudo grub
find /boot/grub/stage1               This returned the value (hd1,2)
root (hd1,2)
setup (hd0)
quit

...but nothing has changed.  I'm at a loss, and am eager to get back to using Ubuntu!  Any help or insight anyone could provide would be most appreciated!  Thanks!

i think you must do 
setup(hd1) not (hd0)

---

