---
title: "Two linux distros on one PC"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by paul6 on 2006-10-17
1. I have Ubuntu and I am trying to install DeliLinux on an empty partition. At one point in the DeliLinux installation it asks if I want to install LILO (Linux Loader), the DeliLinux boot method. Do I need to install this or not?

2. Do I need to do any additional configuration, i.e. the GRUB boot loader? If so what do I need to do?

I am new so please keep it simple:p  Thanks in advance.

---

### Post by adwait on 2006-10-17
You could replae GRUB with LILO and it would detect the presence of all other OS on the system and be appropriately configured. On the other hand, if you don't install LILO, ie: you want GRUB, GRUB will not be updated with your newest OS and so you will have to install GRUB again to make it recognise all your installed OS.

---

### Post by paul6 on 2006-10-17
> **adwait said:**
> You could replae GRUB with LILO and it would detect the presence of all other OS on the system and be appropriately configured. On the other hand, if you don't install LILO, ie: you want GRUB, GRUB will not be updated with your newest OS and so you will have to install GRUB again to make it recognise all your installed OS.

Supposing I choose to keep GRUB, what would be the terminal command(s) to reinstall GRUB under Ubuntu?

---

### Post by Predius on 2006-10-17
sudo grub-install /dev/hdX

---

### Post by paul6 on 2006-10-17
I've installed DeliLinux (without LILO) on hda3. Now I am on Ubuntu trying to reinstall GRUB so that I can access DeliLinux. I tried typing the above command:

> paul@ubuntu:~$ sudo grub-install /dev/hda1
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda

I tried rebooting after and no boot menu appeared, I just booted into Ubuntu. What's wrong?

---

### Post by paul6 on 2006-10-18
OK, searching through other threads, it looks like I have to add DeliLinux as an entry on my boot/grub/menu.lst file. Does anyone know what that entry should look like?

---

### Post by akshaysrinivasan on 2006-10-18
I'm not sure about this, but try reconfiguring grub then reinstalling

---

### Post by pradeepadapa on 2006-10-18
hi man, i hav an doubt that if we install 2 linux distros nd if i want the same UBUNTU GRUB to show up at the starting of the OS select screen, what hav we to do.are there any commands to keep up the same GRUB .

---

### Post by Herman on 2006-10-18
One way would be to mount your DeliLinux filesystem in Ubuntu first. To do that you would first make a 'mount point' (a folder) for it in /media, and name it DeliLinux.sudo ```
mkdir /media/DeliLinux
``` Then, you need to know its partition number and what type of filesystem it has. You can look at that in GParted. Just go 'System'-->Administration'-->'Gnome Partition Editor', and find out and copy down those details ready for the next step.

Then, you add an entry in your /etc/fstab file for the new filesystem, if DeliLinux has an ext3 filesystem, and I dont know that, you will need to check for yourself, then an example of a possible entry for your /etc/fstab file would be something like this, as follows, > [COLOR=#330099]/dev/hda1           /media/[/COLOR]DeliLinux[COLOR=#330099]     ext3  rw,user                 0             2[/COLOR] Where 'hda1' is the partition number for your DeliLinux, replace the 'h' with an 's' if you havve a SCSI or Sata hard disk, replace the '1' with another number if DeliLinux is not on partition number 1.
Where: DeliLinux is on an ext3 filesystem, replace ext3 with reiserfs or whatever type of filesystem DeliLinux is on.

Make a back up copy of your /etc/fstab file before you work on it in case something goes wrong and you need to restore it with the following command, ```
sudo cp /etc/fstab /etc/fstab_backup

```Open your /etc/fstab file with, ```
sudo gedit /etc/fstab
``` Then add your entry for DeliLinux. You might tbe able to just copy the example I jsut gave you and paste it right into your file, or you might need to change some parts of it to match your system. When you have it right, save the file and close it.

Then enter 'sudo mount -a', and you should see an icon on your Desktop that you can click on to open up DeliLinux, ```
sudo mount -a
``` If it doesn't work, just reboot and you should have an icon if you did everything right.

To see an illustrated example of something like what I just explained in case you still aren't sure, [Click Here]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu").

Now, you can open up DeliLinux and look around for DeliLinux's /grub/menu.lst or grub.conf file. You might need to search around for that, and it could even have some different name. When you find it, you should be able to open it and copy it's grub menu entry.
Next, open your Ubuntu /boot/grub/menu.lst, ```
sudo gedit /boot/grub/menu.lst
``` and paste your DeliLinux menu entry at the very bottom of your menu.lst in Ubuntu, underneath the end of your automagic kernels list. Make sure you paste it below your automagic kernels list, not inside it, or your DeliLinux entry will be deleted next time Ubuntu gets a new kernel during an update.

An even better style of boot entry for DeliLinux, can be made by finding out what partition DeliLinux is on, and what the file path and name is of it's grub configuration file (eg /boot/grub/menu.lst, or /GRUB/grub.conf, or whatever), and add a 'configfile boot entry to the Ubuntu menu.lst instead.
For example, 
```
  title        DeliLinux
    savedefault
    configfile   (hd0,1)/boot/grub/menu.lst
``` That one would be much better than DeliLinux's own grub entry that I told you about earlier, because it will boot DeliLinux by it's own whole Grub menu, and when DeliLinux gets a new kernel, Ubuntu's grub will be booting DeliLinux by it's most up to date kernel that way.

If you want to know more about Ubuntu's Grub, here's a webpage all about that, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm").

I hope all that was easy enough for you to understand and it will all work okat for you. If you have any questions or difficulties, I'll be back sometime to check this thread, so be sure to let me know, I'll explain more if needed. :D

Regards, Herman :D

---

