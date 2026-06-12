---
title: "Installing Ubuntu to External Hard Disk Partition (Help!)"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by mrhthepie on 2008-10-13
Ok, so I have Windows Vista installed already on my computer. I want to install Ubuntu to an external hard disk. This is what I think I need to do:

1. Download/burn Ubuntu CD
2. Boot from CD
3. Install normally, choosing the correct hard disk/partition to install to.

I'm using Vista to create a Partition on the Disk to install to (since I already have some files on it). Is this correct? Will it work? Anything else I need to know? Help appreciated.

---

### Post by caljohnsmith on 2008-10-13
> **mrhthepie said:**
> Ok, so I have Windows Vista installed already on my computer. I want to install Ubuntu to an external hard disk. This is what I think I need to do:

1. Download/burn Ubuntu CD
2. Boot from CD
3. Install normally, choosing the correct hard disk/partition to install to.

I'm using Vista to create a Partition on the Disk to install to (since I already have some files on it). Is this correct? Will it work? Anything else I need to know? Help appreciated.
Just one big caveat that I think is worth understanding before you install, because it can save you lots of headache in the long run: 

Grub, the boot loader for Ubuntu, will by default install to the MBR (Master Boot Record) of drive (hd0) (otherwise known as /dev/sda) which in most cases is your internal HDD. The thing to keep in mind is that Grub actually lives in two places: 
[LIST=1]
[*]In the MBR of the HDD so you can boot it on start up.
[*]Grub also has files necessary to boot which reside in the /boot/grub folder in your Ubuntu install.
[/LIST]
So if you install Grub to the MBR of your internal HDD, it will look for its boot files on the external HDD in the Ubuntu /boot/grub directory. That will work just fine as long as nothing happens to your external HDD; if you disconnect your external HDD, or if anything happens to it, you won't be able to boot any of your OSes including Windows, because Grub won't be able to access its necessary boot files on the external drive. Also, if you uninstall Ubuntu, you will have to use a Windows Install/Recovery CD to replace Grub in the MBR of the internal drive with a Windows MBR to get Windows to boot again. If that is acceptable to you, then you don't need to do anything special about Grub when you install Ubuntu. 

But personally what I would recommend is setting your BIOS to boot the external drive on start up instead of your internal drive, and then you can install Grub to the MBR of the external drive; that leaves your internal HDD completely untouched, so if anything happens to your external drive (including if you decide to uninstall Ubuntu), you will still be able to boot Windows on your internal drive. Also note that you can easily add an entry in your Grub menu so that you can boot Windows on your internal drive, so you don't need to change your BIOS just to boot the internal Windows drive. I think this scenario is more ideal than what I described above where Grub is installed to the MBR of your internal drive. If you want to do this, all you have to do is change your BIOS boot order so that your external drive boots first, and then when you go through the Ubuntu installer, at the final installation step click on the "advanced" button, and tell Grub to install to /dev/sdb or whichever is your external drive. If you aren't sure which is your external drive, you can open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
And that will show all your drives. I know all this may seem a bit much for someone new to Ubuntu, but in the long run it can save you a lot of headaches if you understand some of these concepts up front, so you can make the best choices. If you have any questions, let me know. :)

---

### Post by Pumalite on 2008-10-13
Check this thread; there are a few details you need to know:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

