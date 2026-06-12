---
title: "reinstalling XP on dual-boot system"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by chupucabras on 2005-08-13
Hi,

I've had a dual-boot xp/ubuntu setup on my computer for a few months. XP and Ubuntu are on separate drives, XP on the primary master, ubuntu on the primary slave drive. I am using GRUB to let me choose which OS to boot.

I now wish to format my windows drive and do a clean reinstall with the intention of using windows only for some music software. My question is: is there anything special I need to do to preserve my dual-boot capabilities? Will XP's setup detect that there is another OS present and allow me to dual-boot? Will this result in windows' boot manager being used instead of grub?

Thank you.

Dan

---

### Post by enquiry on 2005-08-13
When installed, Windows will overwrite the MBR with its own information. Some users have experienced that Windows won't even boot after being installed (apparently the MBR can become corrupted when NTLDR is installed on top of Grub).

In any event, the solution is to have Grub write its information to the MBR again, after you have installed Windows (or you can back up the MBR, but that's probably more of an effort).

To make a boot disc (so you can boot Ubuntu after installing Windows), write:
sudo grub-install '(fd0)' 
in the terminal (have a formated disc in the floppy drive -- and make sure it works before reinstalling Windows).

When Windows is reinstalled, boot Ubuntu with your boot disc, and then write
sudo grub-install /dev/hda 
in the terminal (given your primary master is indeed hda). Everything should now be back to normal.

NB. Things *can* go wrong, so make backups of your important files before doing anything!

Edit: Forgot the sudo thing ...

---

### Post by Surfcat on 2005-08-14
I  need to reinstall XP on my laptop which does not have a floppy drive.  Can I reinstall Grub from the live cd?

---

### Post by enquiry on 2005-08-14
[QUOTE=Surfcat]Can I reinstall Grub from the live cd?[/QUOTE]
Sure you can, just remember that you must have Grub using the current menu.lst config file (the menu.lst config file on the LiveCD won't work).

So after reinstalling Windows, boot the LiveCD and mount the partition containing your Ubuntu install:
sudo mkdir /mnt/hda2 (so you have a place to mount the partition)*

sudo mount /dev/hda2 /mnt/hda2

Now that Grub can access the menu.lst file, you can install it to the MBR:
sudo grub-install --config-file=/mnt/hda2/boot/grub/menu.lst /dev/hda

* I don't know if Ubuntu is indeed installed on hda2. If you don't know, type sudo fdisk -l for a list of all partitions, and you should have a good idea what partition to mount. If it is for example hda3, just replace hda2 with hda3.

---

### Post by pailhead on 2005-08-28
[QUOTE=enquiry]
Now that Grub can access the menu.lst file, you can install it to the MBR:
sudo grub-install --config-file=/mnt/hda2/boot/grub/menu.lst /dev/hda

* I don't know if Ubuntu is indeed installed on hda2. If you don't know, type sudo fdisk -l for a list of all partitions, and you should have a good idea what partition to mount. If it is for example hda3, just replace hda2 with hda3.[/QUOTE]

I've got a question.. my linux partition is hdb7.  So if I do the above grub-install would I do:

sudo grub-install --config-file=/mnt/hdb7/boot/grub/menu.lst /dev/hda or hdb?

THanks..

---

### Post by enquiry on 2005-08-30
[QUOTE=pailhead]I've got a question.. my linux partition is hdb7.  So if I do the above grub-install would I do:

sudo grub-install --config-file=/mnt/hdb7/boot/grub/menu.lst /dev/hda or hdb?[/QUOTE]
If your primary master disk is hda, the command must end with /dev/hda

---

### Post by filemanager on 2005-08-31
[QUOTE=enquiry]Sure you can, just remember that you must have Grub using the current menu.lst config file (the menu.lst config file on the LiveCD won't work).

So after reinstalling Windows, boot the LiveCD and mount the partition containing your Ubuntu install:
sudo mkdir /mnt/hda2 (so you have a place to mount the partition)*

sudo mount /dev/hda2 /mnt/hda2

Now that Grub can access the menu.lst file, you can install it to the MBR:
sudo grub-install --config-file=/mnt/hda2/boot/grub/menu.lst /dev/hda

* I don't know if Ubuntu is indeed installed on hda2. If you don't know, type sudo fdisk -l for a list of all partitions, and you should have a good idea what partition to mount. If it is for example hda3, just replace hda2 with hda3.[/QUOTE]
 I did that and I got this error:

> sudo: grub-install: command not found


---

### Post by enquiry on 2005-09-02
I see. If you boot from the Ubuntu install CD instead, and choose rescue mode, I believe you can restore the MBR.

---

### Post by rado_london on 2005-10-26
Unfortunately the command didnt work with rescue mode.I have Breezy on my laptop but i tried the rescue mode with hoary disk.
Do u know whAT IS the reason?

---

