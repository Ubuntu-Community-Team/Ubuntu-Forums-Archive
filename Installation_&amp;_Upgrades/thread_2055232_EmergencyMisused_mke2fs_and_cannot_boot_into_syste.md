---
title: "Emergency:Misused mke2fs and cannot boot into system"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by surlogics on 2012-09-08
I installed  ubuntu with wubi in windows7 64bit, and I had installed  Mandriva 2011  with a disk. I tried to learn linux with Ubuntu and  misused     Code:
      mke2fs 
 ; after I reboot my computer, windows7 and ubuntu has  crashed.

I think I may used the following command

     Code:
     ```
mke2fs -j -L "logical"/dev/sda2 
```but I had forgotten what kind of partition it was before I transfered it into ext3
maybe ntfs

As I have mandriva, I boot into mandriva and found 
```

# df -h                                                       
/dev/sda7        12G  9.8G  1.5G   88% /                                                              
/dev/sda2        15G  165M   14G    2% /media/logical                                                 
/dev/sda6       119G   88G   32G   74% /media/2C9E85319E84F51C                                        
/dev/sda5       118G   59G   60G   50% /media/D25A6DDE5A6DBFB9
/dev/sda9       100G  188M  100G    1% /media/ae69134a-a65e-488f-ae7f-150d1b5e36a6
/dev/sda1       100M  122K  100M    1% /media/DELLUTILITY
/dev/sda3        98G   81G   17G   83% /media/OS


# fdisk /dev/sda
Command (m for help): p
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd24f801e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    6  FAT16
/dev/sda2   *      206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30926848   235726847   102400000    7  HPFS/NTFS/exFAT
/dev/sda4       235728864   976771071   370521104    f  W95 Ext'd (LBA)
/dev/sda5       235728896   481488895   122880000    7  HPFS/NTFS/exFAT
/dev/sda6       727252992   976771071   124759040    7  HPFS/NTFS/exFAT
/dev/sda7       481500243   506674034    12586896   83  Linux
/dev/sda8       506674098   514851119     4088511   82  Linux swap / Solaris
/dev/sda9       514851183   727246484   106197651   83  Linux

Partition table entries are not in disk order
```Data was not lost, and I can view my files as I could in Windows
In Mandriva explorer; which shows me places in my harddisk, there are following disks;
117.2G hard disk, files in it is the same as my Windows D:, and ubuntu   was installed in it&#65307;119.0G hard disk is my G:, with my personal files in   it;12.0G is the same with mandriva / (with means root), 101.3G hard   disk with nothing but lost+found;DELLUTILITY should be Dell computer   utilities preinstalled in my computer ;logical is the disk which I had   spoiled, it contained lost+found folder&#65307;and OS is the C: in my Windows.


After I boot, grub let me choose Mandriva or Windows. I chose windows   and it tells me:```

FILE system type unknown, partition type 0x7 Error 13: Invalid or unsupported executable format
```I doubt something wrong with bootsector
#```


# cat /boot/grub/menu.lst
timeout 5
color black/cyan yellow/cyan
gfxmenu (hd0,6)/boot/gfxmenu
default 0

title linux
kernel  (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux  root=UUID=199581b7-ac7e-4c5f-9888-24c4f213cad8 nokmsboot logo.nologo  quiet resume=UUID=34c546e4-9c42-4526-aa64-bbdc0e9d64fd splash=silent  vga=788
initrd (hd0,6)/boot/initrd.img

title linux-nonfb
kernel  (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux-nonfb  root=UUID=199581b7-ac7e-4c5f-9888-24c4f213cad8 nokmsboot  resume=UUID=34c546e4-9c42-4526-aa64-bbdc0e9d64fd
initrd (hd0,6)/boot/initrd.img

title failsafe
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=199581b7-ac7e-4c5f-9888-24c4f213cad8 nokmsboot failsafe
initrd (hd0,6)/boot/initrd.img

title windows
root (hd0,1)
makeactive
chainloader +1
```I can boot into linux, but not ubuntu, it boot into Mandriva

I dont have a boot disk



Help me find a way to make it work again, Thanks in advance.

I had checked my bootsector; details are here [http://paste.ubuntu.com/1193796/](http://paste.ubuntu.com/1193796/)

---

