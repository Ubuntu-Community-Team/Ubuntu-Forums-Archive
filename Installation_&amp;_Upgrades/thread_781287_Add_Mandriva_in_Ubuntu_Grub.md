---
title: "Add Mandriva in Ubuntu Grub"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Mohamed Fahim on 2008-05-04
Hi Guys,
   I have one internal hard disk with Ubuntu 8.04 and Windows Xp running i installed Mandriva in Externald Hard disk now i want to access this mandriva which is installed in external hard disk from ubuntu grub which is stored in Internal hard disk i tried adding it manually with configfile commands it didnt work any idea how to do it.Thanks in advance

---

### Post by bobnutfield on 2008-05-04
With the external disk connected, from the terminal, type:

sudo fdisk -l

and post the results back.  From there, we can create the entry into the menu.lst file for grub to boot into Mandriva.

Bob

---

### Post by Mohamed Fahim on 2008-05-04
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1da51da4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       10198    40957717+   7  HPFS/NTFS
/dev/sda3           10199       15297    40957717+   7  HPFS/NTFS
/dev/sda4           15298       19457    33415200   83  Linux

Disk /dev/sdb: 41.1 GB, 41173056512 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d30bfcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        5005    19719787+   5  Extended
/dev/sdb5            2551        5005    19719756   83  Linux

This is my fdisk - l result on /dev/sdb5 is my mandriva installed

---

### Post by bobnutfield on 2008-05-04
OK, you will need to look in the /boot directory of the Mandriva installation to get the vmlinuz information.  In that directory, you will find a file called:

vmlinuz-2.6.x.x-x and initrd-2.6.x.x-x

You will need the EXACT names of those files to create an entry in your Grub menu.lst file that looks like (but not necessarily the same as) this:

title   Mandriva
root    (hd1,4)
kernel  /boot/vmlinuz-2.6.x.x-x  root=/dev/sda5 ro quiet splash
initrd  /boot/initrd-2.6.x.x-x

How is the drive connected?  If it is USB and your computer allows you to boot from the USB port, the you may be able to boot into by just selecting that option (usually pressing F12 at startup, if you have that option.)

You are also showing windinws partitions on that drive.  Are you booting into windows on it?

Bob

---

### Post by Mohamed Fahim on 2008-05-04
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/boot/gfxmenu
default 4

title linux
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=b055db31-8520-4714-b3d6-14cc9cffea45  splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

title linux-nonfb
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=b055db31-8520-4714-b3d6-14cc9cffea45 
initrd (hd1,4)/boot/initrd.img

title failsafe
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=b055db31-8520-4714-b3d6-14cc9cffea45  failsafe
initrd (hd1,4)/boot/initrd.img

title Ubuntu 8.04 
root (hd0,3)
configfile /boot/grub/menu.lst

title windows
root (hd0,0)
chainloader +1

Hi this is my Mandriva grub Menu.lst entries now what are the things to be cut and pasted in Ubuntu grub. Thanks in advance

---

### Post by bobnutfield on 2008-05-04
> title linux
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=b055db31-8520-4714-b3d6-14cc9cffea45 splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

If you paste this into your Ubuntu menu.lst, this is the entry.  However, I am not sure how using the UUID for root will work on an external drive.  Try it, but if you get an error, change it to:

> title linux
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5 splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

Tell us how this works for you.

Bob

---

### Post by bobnutfield on 2008-05-04
There is another option.  That is to chainload Mandriva.  That entry would be:

title  Mandriva
root (hd1,4)
chainloader +1

This will simply pass the boot option to the grub on the external drive and you can load Mandriva from there.

Bob

---

### Post by Mohamed Fahim on 2008-05-04
Hi Friend,
  I tried all your methods but still no success. Anyother way you can find please let me know. Thanks in advance

---

### Post by bobnutfield on 2008-05-04
What errors are you getting?

---

### Post by Mohamed Fahim on 2008-05-04
itle Linux Mandriva
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=b055db31-8520-4714-b3d6-14cc9cffea45 splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

[COLOR="Red"][B]
Error : Bad File or Directory Type[/B][/COLOR]


#title linux Untried
#kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5 splash=silent vga=788
#initrd (hd1,4)/boot/initrd.img 

E[COLOR="Red"]**rror : Bad File or Directory Type**[/COLOR]

#title Mandriva
#root (hd1,4)
#chainloader +1
[COLOR="Red"][B]
Error : Invalid or Unsupported executable format.[/B][/COLOR]

Please see the errors i got under each try i gave and let me know any solutions you know. The errors are in bold and red color after each try

---

### Post by Mohamed Fahim on 2008-05-11
anybody any new ideas to do it

---

