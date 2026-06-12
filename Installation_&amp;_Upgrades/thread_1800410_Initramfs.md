---
title: "Initramfs"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by accodata on 2011-07-08
I am trying to put ubuntu onto a laptop which wont boot from the CD as the drive is broken, so I have done a startup disk creator through the forums,
so I can't format her window section
so I have run the wubi.exe
ubuntu then reboot the laptop
downloaded ubuntu
and rebooted
gave up waiting for root device. Common problems:
- Boot arts (cat /proc/cmdline)
- check rootbelay= (ddi the system wait for the right device?)
- missing mocules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping into a shell!  
now I have busybox V1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) 
please in very simple terms can this be fixed?
with thanks
Tracey

---

### Post by Dangertux on 2011-07-09
> **accodata said:**
> I am trying to put ubuntu onto a laptop which wont boot from the CD as the drive is broken, so I have done a startup disk creator through the forums,
so I can't format her window section
so I have run the wubi.exe
ubuntu then reboot the laptop
downloaded ubuntu
and rebooted
gave up waiting for root device. Common problems:
- Boot arts (cat /proc/cmdline)
- check rootbelay= (ddi the system wait for the right device?)
- missing mocules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping into a shell!  
now I have busybox V1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) 
please in very simple terms can this be fixed?
with thanks
Tracey

You should check your bootloader configuration. It appears it's looking for something on /dev/sdb1 that it can't find, I would suggest making sure that the paths in the bootloader are correct, this is possibly because you allowed Wubi to install GRUB2 (generally doesn't work well).

You might want to refer to this thread [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

But yes in simple terms it can be fixed. There is a method outlined in that thread that shows how.

Edit : Apparently this is popular today -- you might have a look at this thread it seems similar.

[http://ubuntuforums.org/showthread.php?t=1592470](http://ubuntuforums.org/showthread.php?t=1592470)

---

### Post by jimv on 2011-07-09
If the computer is bootable from a USB drive, you can download UnetBootin to create a thumbdrive that you can install Ubuntu from.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Rubi1200 on 2011-07-09
Hi accodata,

I just want to clarify a few things before suggesting the next step to try and fix this.

> this is possibly because you allowed Wubi to install GRUB2 (generally doesn't work well).Wubi does not install GRUB nor should one attempt to install GRUB to make a Wubi install boot. 

Wubi uses [GRUB4DOS]("http://gna.org/projects/grub4dos/") to _add an entry to the Windows bootloader _which it then appropriates for its own purpose, namely booting a Wubi installed Ubuntu system.

In this situation, the best thing to do is the following so we can see what is where on your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
 sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

