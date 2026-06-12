---
title: "Problems using GRUB bootable Cd and USB drive bootings"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by gabeyg on 2007-07-19
I don't know why I can not either write the grub to my external usb drive's MBR (I tried many suggestions), but anyway, I tried to boot installed ubuntu 7.04 by using grub bootable Cd. ([http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html#fn-1](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html#fn-1)) 
I successfully made iso files and burned and boot from CD. I got grub menus (since made menu.lst file) and made it to boot ubuntu which is in USB drive,  but it shows me error 25, Disk read error. 
This is my hard disk
/dev/sda (XP, not usb drive)
/dev/sdb (ubuntu, usb external drive)
Before, I tried to install ubuntu with using installing GRUB to MBR of /dev/sdb, but after loading from that usb disk, it failed showing Operating System Not Found. Also, I tried to install grub to /dev/sda's MBR and install ubuntu and load from /dev/sda's MBR to /dev/sdb's /boot file but it shows me of error 25:Disk read error. 
I don't know this is the reason, but in my one external usb drive, it has two SATA disks on it, but in operting system and GParted, it is showed as one usb disk (My disk is WD MY Book Pro Edition II 1TB edition). 
Here is my grub.iso that includes menu.lst. Please notify me that if my menu.lst is not good. 
[http://gabeyg.myi.cc/grub.iso](http://gabeyg.myi.cc/grub.iso)

Also, do I need device.map like in real HD booting?
Also, if MBR is the problem, is there a way to activate or merge two disk's MBR?
This site for Western Digital: [http://www.wdc.com]("http://www.wdc.com")
[http://support.wdc.com]("http://support.wdc.com")
site for product infos: [http://westerndigital.com/en/products/products.asp?driveid=270&language=en]("http://westerndigital.com/en/products/products.asp?driveid=270&language=en")

---

### Post by scrooge_74 on 2007-07-19
I am not sure if I can be of any help 

 I would advice you reinstall the system with the usb drive connected, then when it is time to install grub, it should go on the first drive detected by the system at boot time, which I imagine is where your XP partition is.

I also I am not sure which way linux looks at the SATA drives that are on a external drive.

You could also at install time, rezise the disk inside the PC and make a partition of about 10 GB for the system and tell it that /home is on the USB drive (grub is still install on the mbr of the first disk)

Hope this helps

---

### Post by gabeyg on 2007-07-19
> **scrooge_74 said:**
> I am not sure if I can be of any help 

 I would advice you reinstall the system with the usb drive connected, then when it is time to install grub, it should go on the first drive detected by the system at boot time, which I imagine is where your XP partition is.

I also I am not sure which way linux looks at the SATA drives that are on a external drive.

You could also at install time, rezise the disk inside the PC and make a partition of about 10 GB for the system and tell it that /home is on the USB drive (grub is still install on the mbr of the first disk)

Hope this helps

I tried with grub being in Win XP's MBR and files on dev/sdb1's /boot, but it fails loading with not showing grub menu and with error 25.

---

