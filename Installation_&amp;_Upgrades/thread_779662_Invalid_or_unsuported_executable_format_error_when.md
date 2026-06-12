---
title: "Invalid or unsuported executable format error when setting up dual boot"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by ali999 on 2008-05-02
Hi

I've been trying to set up windows XP to dual boot with my Ubuntu 8.04. I had Ubuntu installed first, then installed windows XP on another partition on the same hard disk. XP installed fine and loaded up perfectly and everything. I then reinstalled GRUB using the live CD so I could boot with Ubuntu again and that worked just fine as well. I then edited my /boot/grub/menu.lst file to be able to boot XP as well however, whenever I restart I can only load up Ubuntu. If I choose Windows XP I get an error message saying "Error 13: Invalid or unsupported executable format." I added the following lines to my menu.lst file:

title 		Windows XP Professional
root 		(hd0,1)
makeactive
chainloader +1 

### END DEBIAN AUTOMAGIC KERNELS LIST

I thought this was possibly because I need to add map functions to the XP part, however since all partitions with the operating systems on it are on the same hard disk I am not sure if I need to do this or how should I do this if it is needed. All the tutorials I have seen online that require you to put in the map lines have windows and ubuntu installed on seperate hard disks. I am just lost as to what I should do now. Can someone please help. Thanks in advance.

---

### Post by Pumalite on 2008-05-02
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by ali999 on 2008-05-02
Well the second link contains the instructions which I originally used to do the installation. The first link suggests the the NTFS partition may be corrupted and I should use the program testdisk to try and fix it. However, I am not sure if its my computer or the ubuntu archives are down because I cannot connect to them and download the program for the life of me. Anyone have any other suggestions?

---

### Post by ali999 on 2008-05-02
alright..i got testdisk installed however it doesn't really seem to detect any errors in my disk. However, if i choose to list the files in the NTFS partition, I get a message saying segmentation fault and testdisk stops running. Now i'm just confused.

---

### Post by ali999 on 2008-05-03
Does anyone have any ideas? I really need to get windows running so i can run various applications i have

---

### Post by Herman on 2008-05-03
Please post the output from 'sudo fdisk -lu'
```
sudo fdisk -lu
```

---

### Post by ali999 on 2008-05-03
Disk /dev/sda: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30892994    15446466   83  Linux
/dev/sda2   *    30892995    33688304     1397655   82  Linux swap / Solaris
/dev/sda3        33688305    66027149    16169422+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe94ee94e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   240107489   120053713+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf609ea59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   625137344   312568641    7  HPFS/NTFS

---

### Post by Herman on 2008-05-03
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title         Windows XP Professional
 root         (hd0,2)
 makeactive
 chainloader +1 
```:) Hello ali999,
Your Ubuntu operating system is in partition 1, which is called /dev/sda1 in Linux, but in GRUB terms it's called (hd0,0), because GRUB always starts counting from zero, rather than one.
That means your swap area will be (hd0,1) to GRUB, so it appears that you were trying to boot your swap area.

Your Windows partition is partition 3, or /dev/sda3, which will be called (hd0,2) by GRUB, and if you try editing your /boot/grub/menu.lst file with that partition number it should boot, (I hope). :)

Also, you should cut your Windows boot stanza from inside of the Debian automagic kernels list area and paste it either above that area or below it.
If you paste it above the line that says: ### BEGIN AUTOMAGIC KERNELS LIST, (way up around the middle of your /boot/grub/menu.lst file), then Windows will boot first by default.
If you paste it below the line that says: ### END DEBIAN AUTOMAGIC KERNELS LIST, then Ubuntu will be listed first in your boot menu and Ubuntu will boot by default. That's the way most people like it.

If you leave your Windows or any other foreign boot stanza inside the Debain automagic kernels list area of the menu.lst file, it will be automagically deleted every time Ubuntu gets a new kernel in an update and I don't think you will enjoy that.  :)

Regards, Herman :)

---

