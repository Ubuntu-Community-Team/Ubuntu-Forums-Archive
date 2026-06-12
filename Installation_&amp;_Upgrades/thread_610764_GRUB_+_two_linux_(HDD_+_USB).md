---
title: "GRUB + two linux (HDD + USB)"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by tomek_p on 2007-11-12
Hi all !

I've got huge problem with configuration of my GRUB... :-(

I've got two linux: one is installed on my HDD (it is Ubuntu ofcourse ;-) ) and the second one is installed on external USB drive. Unfortunately, while installing the second linux my GRUB has been overwritten and now his configuration is on the second linux so on USB drive. What should I do to move the configuration back on HDD (to be able to make configuration from Ubuntu) ?

Second problem:

If i manage to move the configuration into HDD what should i do to be able to boot the system even then when external drive is disconnected (but i still want to have the second linux there and sometimes i want to run it) ?  

Thank you guys for help and sorry for my english :-)

---

### Post by Herman on 2007-11-12
Hello tomek_p,
First problem:
You should do something like what I explained in this other thread, here:                               [HOW-TO install boot loader from Ubuntu]("http://ubuntuforums.org/showthread.php?t=609548")
That should explain to you how to re-install Grub from your Linux installation in your first hard drive to MBR in your first hard drive.
You should be able to install and GRUB from anywhere to anywhere once you can understand the method. 

Second problem:
First you will need to install the USB disk's GRUB to the MBR of the USB disk, or to the first sector of the Ubuntu partition in the USB, or both.
Use the same how-to again but make sure you change the partition numbers for the 'root' command, (where you are installing FROM), and the setup command, (where you are TO). Make sure you install the USB's GRUB to the USB.

Open your /boot/grub/menu.lst file in your internal hard disk installed Ubuntu, and add a boot entry for booting the USB using GRUB's chainloader command.

An example of a chainloader command for booting a MBR in another hard disk would look something like this,
```
root (hd1)
chainloader +1

```Replace the (hd1) with whatever your system thinks your USB hard drive number should be.

I'm pretty sure that will work as long as your computer's BIOS supports booting from USB. 

Regards, Herman :)

---

