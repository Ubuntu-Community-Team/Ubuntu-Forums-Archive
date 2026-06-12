---
title: "windows HD"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Lam on 2005-09-09
I have 2 harddisk in my computer. I have installed windows in the first harddisk and ubunta in the second harddisk. However, I cannot find the first harddisk when I boot into the ubunta. Where to find the windows harddisk?

---

### Post by amohanty on 2005-09-09
When you boot up the GRUB menu should show up, with a list of available options. When you were installing Ubuntu, it should have prompted you about Windows being present on the system. That is what will show up in the GRUB menu. Typically it will look like:

Ubuntu ....
Ubuntu ... Failsafe mode
memtest86
Windows XP Professoinal...

Do you see it or not?

AM

---

### Post by Lam on 2005-09-09
[QUOTE=amohanty]When you boot up the GRUB menu should show up, with a list of available options. When you were installing Ubuntu, it should have prompted you about Windows being present on the system. That is what will show up in the GRUB menu. Typically it will look like:

Ubuntu ....
Ubuntu ... Failsafe mode
memtest86
Windows XP Professoinal...

Do you see it or not?

AM[/QUOTE]
 I don't mean to boot up into windows. After I boot into linux, the windows partition should be mounted to /mnt directory (this is what happened when I used mandrake). Therefore, I can read the file in windows partition when I am in the linux. However, I cannot find the windows partition after I boot into ubuntu.

---

### Post by amohanty on 2005-09-10
I have never used Mandrake/Madriva so I cannot really say how it works there. In Ubuntu you will have to either mount it after you login using something like:
mount -t ntfs /dev/<drive name usually hda/hdb> /mnt/win

on the terminal, please note that you have to create a folder called /mnt/win first.

To make it so that it loads at bootup you will need to edit you /etc/fstab and add it in there. Please note that you will have to use sudo to do so. For e.g.:
sudo gedit /etc/fstab

This is what I have in my fstab to load up my win partition:
> /dev/sda1       /mnt/win           ntfs    ro,auto        0       0 

Since NTFS support is still not so great, ro makes sure you cannot write to it, auto will mount it at boot. A good basic explanation of fstab is here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

HTH
AM

---

### Post by Lam on 2005-09-10
[QUOTE=amohanty]I have never used Mandrake/Madriva so I cannot really say how it works there. In Ubuntu you will have to either mount it after you login using something like:
mount -t ntfs /dev/<drive name usually hda/hdb> /mnt/win

on the terminal, please note that you have to create a folder called /mnt/win first.

To make it so that it loads at bootup you will need to edit you /etc/fstab and add it in there. Please note that you will have to use sudo to do so. For e.g.:
sudo gedit /etc/fstab

This is what I have in my fstab to load up my win partition:
 

Since NTFS support is still not so great, ro makes sure you cannot write to it, auto will mount it at boot. A good basic explanation of fstab is here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

HTH
AM[/QUOTE]
 Thanks a lot.

Lam

---

