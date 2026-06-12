---
title: "Select OS to boot from inside ubuntu"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by anthracy on 2007-06-01
I have been looking around the internet forever to find a way to select to boot XP from the ubuntu log off menu.
(since ubuntu is default)

I would like to be able to start up xp from time to time strait from ubuntu without having to baby sit it.

Anyone that has used suse in the past knows that it offers a way to shutdown and boot to a selection in the grub menu.

Is there anything like this for ubuntu?

---

### Post by epiphiny on 2007-06-01
Hi there,

There is no native way to do this, and nor have I found an application that (as yet) works with it.  However, the next best thing (For me anyway) was to create a rather ugly hack, using two different menu.lst files, and then a bat script (for windows) and shell script for linux to switch between the two.

This is reletively simple; first, you have menu.lst.ubuntu , in which you set the 'default' value to whichever menu entry is ubuntu.

Next, create menu.lst.win , which will default boot to windows.  Here, the default entry should be for your windows entry.

Next, that bat files.  I use a seperate partition to store grub on, as I find it's easier to recover if I make a mistake and delete grub etc, I just use partimage to restore it from a usb key.

Anway, your two files should be win_reboot.sh, and ubuntu_reboot.bat

win_reboot.bat should look like;
```

#! /bin/bash
mount /dev/sda2 /mnt/boot               #replace /dev/sda with whichever drive holds your grub config.
cp /mnt/boot/grub/menu.lst.win /mnt/boot/grub/menu.lst
shutdown -r now

```

Then, in windows, create reboot_win.bat, which should look something like;
```

E:
copy E:\grub\menu.lst.ubuntu E:\grub\menu.lst
shutdown -r now

```
NOTE: I used ext2 IFS to mount my grub partition.

To run the reboot_win.sh easily, I created a shortcut to it on my desktop, prefixed with gksudo so that I would be able to run the commands as root (needed by default to use shutdown and mount).

There is a warning with this; every time you update your kernel, you are going to need to update your menu.lst.x files, as they will not be updated to include the new kernel and initrd files.  If you accidentally forget to include them, you can normally still boot using you old kernel, but won't get the advantages of it.

Hope that helps, sorry for it being such an ugly hack!
J

---

### Post by anthracy on 2007-06-04
Thank you so much, I wish they would add this as a feature, I always believed it to be very useful while I was using openSuse (before the Microsoft deal)

---

