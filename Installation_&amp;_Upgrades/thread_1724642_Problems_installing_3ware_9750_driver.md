---
title: "Problems installing 3ware 9750 driver"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by jjflag on 2011-04-08
Trying to install 3ware 9750 driver as part of 10.10 install. Instructions that come with 3ware driver:
This procedure installs the LSI 3ware 9750 driver while installing Ubuntu Server 10.10 64bit

1. Copy the drivers (driver-9750.tgz) to a floppy disk or USB flash

2. Boot from the Ubuntu installation CD and select Install Ubuntu Server. 
   Press CTRL+ALT+F2 to switch to console2 when the language screen comes up.

3. Type the following commands:

If a floppy disk is used, type these commands
   
   # mkdir /mnt2  /3ware
   # mount -t vfat /dev/fd0 /mnt2 
   # cp /mnt2/driver-9750.tgz   /3ware
   # cd /3ware ; tar zxvf driver-9750.tgz
   # umount /mnt2
   # insmod 2.6.35-22-generic/3w-sas.ko

 
If USB flash is used, it should be detected as scsi device /dev/sda1 or sdb1 

You can check for the scsi devices by running this command : dmesg | grep sd
   
   # mkdir /mnt2 /3ware
   # mount -t vfat /dev/sda1 /mnt2
   # cp /mnt2/driver-9750.tgz  /3ware
   # cd /3ware ; tar zxvf driver-9750.tgz
   # umount /mnt2
            
   *** Please make sure that you remove the USB flash drive before executing insmod**
   
   # insmod 2.6.35-22-generic/3w-sas.ko
 
4. Press CTRL+ALT+F1 to return to the installer. Continue the installation as usual.

When I enter the command:  mount -t vfat /dev/fd0 /mnt2 , the console says there is no such file or directory. I get the same thing when trying to install from a usb drive. Don't know where to go from here. I'm not sure how to enter the dmesg I grep sd command because I don't know how to enter the vertical line that is in the command. Any help would be great.

---

