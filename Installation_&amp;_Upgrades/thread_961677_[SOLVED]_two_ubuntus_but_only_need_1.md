---
title: "[SOLVED] two ubuntus but only need 1"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by banana jama on 2008-10-28
for some reason there are two ubuntu os on my hard drive( yes i've tried both they both work) this alsomeans that my hard drive is partioned in three :vista, ubuntu, ubuntu. how do i get rid of the second ubuntu. my vista is messed up and i can't install or use the options for managing the hard disk. also i've install gnome partion editior and i still c an't delete the partion it says something about a number being greater than five unmount. the problem is i unmounted it already. is there any other way i can delete the extra ubuntu partion( likes call it ubuntu a) while im on the other ubuntu partion( ubuntu b).

---

### Post by Elfy on 2008-10-28
Please start up the ubuntu you wish to _keep_ - run these commands from a terminal and paste the outputs here

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

---

### Post by banana jama on 2008-10-28
this is what it says. sorry for the delay i had class soon after posting this.

makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-21-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-server (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-server (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-21-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-21-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-openvz (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-openvz (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-21-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-21-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-19-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-server (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-19-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-19-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-openvz (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-19-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-18-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-server (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-server (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-18-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-18-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-openvz (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-openvz (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-18-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-386 (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-386 root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-16-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-server (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-server (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-server root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-16-server
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-rt (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-rt (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-rt root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-16-rt
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-openvz (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-openvz (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-openvz root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-16-openvz
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0538a2cf-a115-47cc-aefa-82f217705d24 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot

akeem@akeem-laptop:~$ sudo fdisk -l
[sudo] password for akeem: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29498de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4857    39013821    7  HPFS/NTFS
/dev/sda2           28844       30401    12508160    7  HPFS/NTFS
/dev/sda3            4858       28843   192667545    5  Extended
/dev/sda5           23417       23481      522112+  83  Linux
/dev/sda6           28616       28843     1831378+  82  Linux swap / Solaris
/dev/sda7            4858       22706   143372029+  83  Linux
/dev/sda8           22707       23416     5703043+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by banana jama on 2008-10-28
o yea i would like to keep vista. i just want the extra ubuntus gone. thanks

---

### Post by SuperSonic4 on 2008-10-28
If you're in the one you want to keep can't the OP just use GParted to unmount and wipe the other ext3 partition? Especially since he can't unmount the one he wants to kee[

---

### Post by ajwak95 on 2008-10-28
Try and make a LiveCD of GParted, and when in there, delete the partition and then expand one of the two partitions you want, either Ubuntus partition or Vista's

---

### Post by banana jama on 2008-10-29
it worked thanks.

---

