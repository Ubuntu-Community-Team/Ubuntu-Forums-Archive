---
title: "Installed Windows XP Home on Ubuntu"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by okanss on 2006-12-21
Hello there,
Yesterday my laptop's harddrive caused a lot of problems and i formatted and reinstalled Windows XP Home Edition on my C partition. I installed Ubuntu 6.10 one week ago to another partition so my grub was failed to load and automaticlly Windows is loading now. 
I tried to change the boot sequence and add Ubuntu to booting by using boot.ini from windows but it didnt worked cause windows didnt saw the partition that i installed ubuntu and i could not named the partition  inside boot.ini file. 
After that i loaded from Ubuntu CD and tried to change the sequence from Gnome partition editor but missing OS failure happened.I changed the boot flag to my C partition back and after that i reinstall the grub after i booted from Ubuntu CD also that didnt worked too. 
I have datas at the Ubuntu drive but i couldnt reach it. Any help will be gladly accepted.

I

---

### Post by holdinout on 2006-12-21
[http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")
See if that helps.

---

### Post by NetOS on 2006-12-21
If you only want to extract data from the ubuntu partition, load the ubuntu live CD, open a console and mount your partition:
sudo mkdir /mnt/temp ; mount -t ext3 /dev/sda5 /mnt/temp

replace /dev/sda5 with your ubuntu partition, you can find it by examing ' fdisk -l '.

to repair grub:

sudo grub
find /boot/grub/stage1      
root (hd0,5)                 # replace 0,5 with the output of the find command
setup (hd0)                  # to install in MBR
quit

Then restart. I hope i could help.

P.S Recently i had the same problem, but since i deleted a partition, their order changed. If that's the case, mount the ubuntu partition and edit /boot/grub/menu.lst and /etc/fstab according to the changes in the order. i.e /dev/sda5 (hd0,4) changed to /dev/sda4 (hd0,3)

---

### Post by okanss on 2006-12-21
Yeah i tried to load the ubuntu CD and tried to reinstall grub and it worked.Now i have an error like Error 17: Cannot Mount Selected partition after i selected the linux at grub interface.
I tried to access to my data at my linux partition and i typed sudo mkdir /mnt/temp as we said but that turned me mkdir: cannot create directory 'mnt/temp' : No such file or directory exception.
Another try to solve this error 17 by me ended with nothin. I downed to console at grub startup by pressing "c" then remade the root() and setup() commands and nothing changed.

---

### Post by NetOS on 2006-12-21
It sounds like the order of the partitions changed. Can you paste your ' fdisk -l', grub.lst, and fstab ? i'm not sure if we can make a dir with the live CD, so try mounting at /mnt instead of making a new partition in it.

Sorry for the bad English.

---

### Post by okanss on 2006-12-21
So hello back,
I press C again at the grub menu and 
geometry (hd0)  command returned me
drive 0x80: C/H/S = 1023/255/63 , the number of sectors = 117210240 , LBA
[INDENT]Partititon num: 0, Filesystem type unknown, partititon type 0x7[/INDENT]
[INDENT]Partititon num: 1, Filesystem type unknown, partititon type 0x82[/INDENT]
[INDENT]Partititon num: 2, Filesystem type is ext2fs, partititon type 0x83[/INDENT]
[INDENT]Partititon num: 4, Filesystem type unknown, partititon type 0x7[/INDENT]

and my setup command
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

---

### Post by okanss on 2006-12-21
I reopen my LiveCD and now 
**my fdisk -l**

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        2805     2048287+  82  Linux swap / Solaris
/dev/hda3            2806        4717    15358140   83  Linux
/dev/hda4            4718        5992    10241437+   f  W95 Ext'd (LBA)
/dev/hda5            4718        5992    10241406    7  HPFS/NTFS

**grub.lst is**
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda4 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
boot
[B]
annddd[/B]

# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[B]
and GRUB information i can add[/B]

grub> geometry (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x82
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> root (hdo,3)  

Error 23: Error while parsing number

grub> root (hd0,3)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 

ANY one can help for the ERROR?

---

