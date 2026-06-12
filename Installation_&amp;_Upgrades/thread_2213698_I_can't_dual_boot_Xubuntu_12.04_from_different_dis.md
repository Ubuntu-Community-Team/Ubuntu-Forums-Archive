---
title: "I can't dual boot Xubuntu 12.04 from different disk"
date: 2014-03-28
forum: Installation &amp; Upgrades
---

### Post by Thagor on 2014-03-28
My main  OS is Windows 7 Pro 64bit. It is installed on a SSD. I have 3 more HDD  drives in my system and I want to use a variant of Xubuntu, OSGEO-live 7.9  which is based on Xubuntu 12.04 LTS. I booted into OSGEO from a live  USB-Stick. From there I used Ubiquity to start the installation. During  the process when there is the option to choose if I want to install  parallel to Win7 or to erase Win7, I toke the third option "something  else". On one of my 3 other HDDs is create a ext4 partition that is  mounted as root and a swap partition. I did choose the ext4 parition as the  target for the boot loader installation. I hit "Install Now" and everything works fine.

  How I imagined it would work was that I choose the HDD with the  Xubuntu partion as first boot device and it would boot the OS. But it  dosen't. I tried all my HDDs and no matter which one I choose, the system is  stuck at "Loading operation system..."

  So where did I go wrong? 

  thanks in advance for your advice :)

---

### Post by sudodus on 2014-03-28
Welcome to the Ubuntu Forums :-)

> **Thagor said:**
> I did choose the ext4 parition as the  target for the boot loader installation. I hit "Install Now" and everything works fine.


This is wrong. You should install the bootloader into the head of the drive, not to a partition, so for the first drive /dev/sda, for the second drive /dev/sdb. There should be no partition number, only the device letter a, b, ...

You can either reinstall the bootloader or redo the whole installation.

If you want to reinstall the bootloader try according to this link (when booted from the Xubuntu install CD/DVD/USB drive).
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System[/URL]

```

sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

---

### Post by Thagor on 2014-03-28
thanks a lot! I will do that when I get home :)

---

