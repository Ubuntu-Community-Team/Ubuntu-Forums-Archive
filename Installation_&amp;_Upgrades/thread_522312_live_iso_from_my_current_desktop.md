---
title: "live iso from my current desktop?"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by mpgarate on 2007-08-10
is there a way to take my current ubuntu with all its tweaks, and copy it to a cd or multiple cds (via iso i assume) to install on the same machine in case of a crash?

im using feisty 7.04, and a dell n series designed for freedos
amd 64 dual core, running x86 ubuntu
2g ram

---

### Post by PhrankDaChickenGeek on 2007-08-10
You can try 'bootcd' - It's in the repos:
```

Description: run your system from cd without need for disks                     
 Build an image of your running Debian System with the command bootcdwrite.     
 You can also build a bootcd ISO image via NFS on a remote System.              
 When you run your system from CD you do not need any disks. All                
 changes will be done in ram. To reuse this changes at next boot time           
 you can save them on FLOPPY with the command bootcdflopcp. If booting          
 from your CD-drive is not supported, booting from FLOPPY is possible.          
 It is possible to install a new system from the running CD with the            
 command bootcd2disk. Bootcd2disk can also find a target disk, format           
 it and make it bootable automatically. Bootcd also supports lilo,              
 grub, initrd, udev, lvm, transparent-compression ISO 9660 fs and               
 syslinux/isolinux.   

```

Or maybe Reconstructor: 
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)
```

	Reconstructor is an Ubuntu GNU/Linux CD Creator.

It uses the Desktop(Live), Alternate(Install), or Server disc as a base, and then allows for user customization.

For the Ubuntu Desktop base, you can customize the entire environment.  For instance, you can add/remove software, change the default look (splash, themes, fonts, wallpaper, etc.), add desktop links, etc. 

For the Alternate and Server bases, you can add any additional software to the disc that you would like installed.

Reconstructor is written in python and is licensed under the GNU General Public License (GPL). 

```

I'm sure there are others...

---

### Post by mpgarate on 2007-08-10
i've looked at reconstuctor... i could customize it, but I already have a desktop customized... and bootcd... will that let me install the cd created to the HD?

---

