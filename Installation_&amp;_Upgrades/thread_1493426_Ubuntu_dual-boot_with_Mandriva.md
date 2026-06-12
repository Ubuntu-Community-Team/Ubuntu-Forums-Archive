---
title: "Ubuntu dual-boot with Mandriva"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by philkahly8 on 2010-05-25
I have Ubuntu 10.04. I used a Gparted live cd to partition it and installed Mandriva spring 2010 in unallocated space. It works fine but I can't get back to Ubuntu. How do I do it?

---

### Post by oldfred on 2010-05-26
I would reinstall Ubuntu's grub2 to the MBR and I would expect it to find and let you boot Mandriva on a sudo update-grub.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by philkahly8 on 2010-05-26
I tried  
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5   but it said cannot create directory file exists. the I typed   sudo grub-install --root-directory=/media/sda5 /dev/sdalike it said, and it told me it was reading BIOS driver or something like that. I walked away then came back and the computer had shut off. I turned it on, it said loading grub then it booted Mandriva without asking me.

---

### Post by oldfred on 2010-05-26
You installed mandriva's grub to sda's MBR so now you are booting mandriva.

sudo grub-install --root-directory=/media/sda5 /dev/sda

Should be to get mandriva's grub into the partition.
sudo grub-install --root-directory=/media/sda5 /dev/sda[COLOR=Red]5[/COLOR]

Drives which control booting from startup are sda, sdb, sdc etc. the MBR or master boot record is the first sector of the hard drive and is not part of any partition.

Partitions which may have boot sectors (like windows does) allow chainloading. they are sda1, sda2, sdb1 etc.

You should reinstall mandriva to sda5 and reinstall Ubuntu's grub2 to sda.

---

### Post by philkahly8 on 2010-05-29
My brother, who is a computer programmer, stopped by and helped me with it. He had me type 

gedit /boot/grub/menu.lst and add Ubuntu's information to it. Now I can select Ubuntu from Mandriva's grub but it says it can't find it. He kept having me change it to try and fix the problem but he had to leave before we could fix it. The file is attached.

---

### Post by philkahly8 on 2010-05-29
Never mind, I fixed it with: 
			  title Ubuntu 10.04
root (hd0,0) 
kernel /boot/grub/core.img



Thanks anyway!

---

