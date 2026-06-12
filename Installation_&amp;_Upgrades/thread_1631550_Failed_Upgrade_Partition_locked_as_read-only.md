---
title: "Failed Upgrade: Partition locked as read-only"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Chevy787 on 2010-11-26
I was updating from 10.04 to 10.10 earlier today when my laptop shutoff in the middle. I fixed a grub error by reinstalling it with a live-cd, and found out I had a "kernel panic-not syncing: VFS: unable to mount root fs on" waiting for me. I booted an alternative kernel and tried fixing things from there, but got "general error mounting filesystem". So, I tried a live-cd and when I mount the partition, it is read-only. I tried running fcsk to no avail. Any help?
The only thing I could find helpful was this.
["It's probably because your filesystem has suffered a failure - it is configured by default (in /etc/fstab) to remount as read-only in such cases in order to minimise the risk of data loss."]("http://ubuntuforums.org/showpost.php?p=4741315&postcount=3")
Thanks.

---

### Post by mikewhatever on 2010-11-27
If fsck doesn't help, I'd just backup personal files and reinstall.

---

### Post by Rubi1200 on 2010-11-27
Hi and welcome to the forums :)

Did you try running these commands from the LiveCD?:

Run the following commands:
> sudo e2fsck -C0 -p -f -v /dev/sdax 

If there are errors, run this:
>  sudo e2fsck -f -y -v /dev/sdax 
Where x represents your actual Ubuntu partition.

---

### Post by Chevy787 on 2010-11-27
Ran
```

sudo e2fsck -C0 -p -f -v /dev/sda4

```
Retunred
```

  233838 inodes used (3.29%)
     170 non-contiguous files (0.1%)
     360 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 203560/78
 5290315 blocks used (18.62%)
       0 bad blocks
       2 large files

  168421 regular files
   29035 directories
     163 character device files
      31 block device files
       0 fifos
     528 links
   36131 symbolic links (29948 fast symbolic links)
      48 sockets
--------
  234357 files

```

Still is read only :( . And thanks for the warm welcome/help ;)
Edit: forgot to replace x, sorry.

---

### Post by Rubi1200 on 2010-11-27
Chevy787,
what is the number of the partition on which Ubuntu is installed?

On the LiveCD, use this to find out:

```
sudo fdisk -lu
```

Post the output please.

---

### Post by Chevy787 on 2010-11-27
Should be /dev/sda4
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73e3aaa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       293684265   312576704     9446220    7  HPFS/NTFS
/dev/sda3       291467295   293684264     1108485   82  Linux swap / Solaris
/dev/sda4            2048   291465215   145731584   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65536000 bytes
33 heads, 63 sectors/track, 61 cylinders, total 128000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32      127999       63984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(63, 32, 63) logical=(61, 18, 47)

```
btw: I did resize this partition a minute ago, I was being fickle about putting a new installation of ubuntu onto another pation...

---

### Post by Rubi1200 on 2010-11-27
But you ran the command on sda4 right?

What about running the second command?

And, where is sda1? Also, I do not see a boot flag for Windows?

Right now, it might be best to run the boot info script linked at the bottom of my post and get the results back here so we can really see what is going on.

---

### Post by Chevy787 on 2010-11-27
Correct, I edited my above post, sorry.


Ran
```

sudo e2fsck -f -y -v /dev/sda4

```
Returned
```

e2fsck 1.41.12 (17-May-2010)

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  233838 inodes used (2.57%)
     170 non-contiguous files (0.1%)
     360 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 203560/78
 5415731 blocks used (14.86%)
       0 bad blocks
       2 large files

  168421 regular files
   29035 directories
     163 character device files
      31 block device files
       0 fifos
     528 links
   36131 symbolic links (29948 fast symbolic links)
      48 sockets
--------
  234357 files

```



To explain why sda1 no longer exists: 
This pc previously had vista, but I migrated by wubi installation to a new partition and deleted vista.
The partitions that exists now consist of
1. Ubuntu (/dev/sda4)[ext4]
2. Linux-Swap (/dev/sda3)[linux-swap]
3. Vista Recovery Partition {in the rare chance of reinstalling it} (/dev/sda2) [ntfs]


Resulsts from boot info attached.

---

### Post by Rubi1200 on 2010-11-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2         293,684,265   312,576,704    18,892,440   7 HPFS/NTFS
/dev/sda3         291,467,295   293,684,264     2,216,970  82 Linux swap / Solaris
/dev/sda4               2,048   291,465,215   291,463,168  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 65 MB, 65536000 bytes
33 heads, 63 sectors/track, 61 cylinders, total 128000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32       127,999       127,968   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        ACB097CAB0979982                       ntfs       HP_RECOVERY                   
/dev/sda3        4d8d80b8-4442-43f8-ab5f-e6abd66d0045   swap                                     
/dev/sda4        5ffd1736-990d-4a4f-9711-707804faf3ce   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        088C-F048                              vfat       DO                            
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/DO                vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda4/boot/grub/menu.lst: ===========================


title UNetbootin-partitionmanagerrev146
   root (hd0,)
   kernel /ubuntu/disks/boot/ubnkern noapic root=/dev/ram0 init=/linuxrc ramdisk_size=200000 keymap=us liveusb vga=791 quiet toram
   initrd /ubuntu/disks/boot/ubninit
   boot


=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux    /boot/vmlinuz-2.6.35-23-generic root=/dev/sda4 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=/dev/sda4 ro single 
    echo    'Loading initial ramdisk ...'
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5ffd1736-990d-4a4f-9711-707804faf3ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 5ffd1736-990d-4a4f-9711-707804faf3ce
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set acb097cab0979982
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0


# root was on /dev/sda4 when wubi migrated
UUID=5ffd1736-990d-4a4f-9711-707804faf3ce    /    ext4    errors=remount-ro    0    1
# swap was on /dev/sda3 when wubi migrated
UUID=4d8d80b8-4442-43f8-ab5f-e6abd66d0045    none    swap    sw    0    0

=================== sda4: Location of files loaded by Grub: ===================


  21.7GB: boot/grub/core.img
  39.6GB: boot/grub/grub.cfg
  21.6GB: boot/grub/menu.lst
    .1GB: boot/initrd.img-2.6.32-21-generic
    .1GB: boot/initrd.img-2.6.32-24-generic
  18.6GB: boot/initrd.img-2.6.32-26-generic
  21.6GB: boot/vmlinuz-2.6.32-21-generic
  21.6GB: boot/vmlinuz-2.6.32-24-generic
  21.6GB: boot/vmlinuz-2.6.32-26-generic
  21.6GB: boot/vmlinuz-2.6.35-23-generic
  18.6GB: initrd.img
    .1GB: initrd.img.old
  21.6GB: vmlinuz
  21.6GB: vmlinuz.old
```

I offer my apologies Chevy787 because I should have asked you to run the script in the first place.

The problem seems to be that you have vestiges of legacy-GRUB mixed with GRUB2:
> Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

The way to resolve this is to purge and reinstall GRUB using the chroot method outlined in this guide by drs305:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Use sda4 as your partition for the instructions.

---

### Post by oldfred on 2010-11-27
You look like you are half updated. You have the new kernel but not a new initrd, so the grub entry is missing the initrd for the new version.

You could try chrooting into your system and do a full update from that.

kansasnoob's change sda4 to correct partition
sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Then run these commands:

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Chevy787 on 2010-11-27
When I attempt to chroot...
```

Floating point exception (core dumped)

```

Meaning something went wrong, right?

---

### Post by Rubi1200 on 2010-11-28
I would try running the commands again:

From the terminal:
```
sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```Copy/paste to avoid mistakes.

You should then come to a root prompt on the LiveCD which will allow you to perform the updates and cleaning commands suggested by oldfred (note: you do not need to use sudo once you are in the chroot environment).

(edit: there were extra spaces in some of the lines which I now corrected; should be good to go)

---

### Post by Chevy787 on 2010-11-28
Soryy, the file I saved the output to got corrupted.
But, running the line you mentioned above tells me that /etc/resolv.conf does not exists. I checked myself, and it is not there.

---

### Post by dino99 on 2010-11-28
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO)

---

### Post by Chevy787 on 2010-11-28
Rubi1200, resolv.conf was there on reboot. Does it only create itself once I connect to the internet?

Anyways, ran the commands you posted...
```

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
Floating point exception (core dumped)

```

dino99, I'll look at what you said too and see how it goes.
Edit: dino99, are you saying you want me to create a duel boot system? I feel like that wouldn't help fix the underlying problem.

---

### Post by dino99 on 2010-11-28
> **Chevy787 said:**
> Rubi1200, resolv.conf was there on reboot. Does it only create itself once I connect to the internet?

Anyways, ran the commands you posted...
```

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
Floating point exception (core dumped)

```

dino99, I'll look at what you said too and see how it goes.

was only if you cant fix your install with the previous command :)

---

### Post by oldfred on 2010-11-28
I have not seen a exception like that. It seems to be a code error of some sort.

Lets try each command and see if we can see which command is causing the error.

multiline version of above from kansasnoob
MOUNT:
sudo mount /dev/sda4 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt

If it happens to work then run the rest of the commands.

---

### Post by Chevy787 on 2010-11-28
already checked, it's chroot that causes the error.

---

### Post by oldfred on 2010-11-28
As near as I can tell if the mount does not exist then the chroot may give that type of error.

This may be back to your original issue of kernel panic and not mounting sda4.

I would run the second fsck command to fix errors just to see if it does anything. Beyond that I am lost. Perhaps loading testdisk and see what it says about the partition.

---

### Post by Rubi1200 on 2010-11-28
+1 for Testdisk.

This should help:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Chevy787 on 2010-11-28
Good news, I booted Parted Magic (in order to run testdisk) and it seems that I can actually read and write files onto the partition in Parted Magic. Anyhow, I'm gonna go ahead and figure out how to run testdisk. I'll post results in a few minutes

---

### Post by Chevy787 on 2010-11-28
This is what testdisk tells me after a quick search.
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1 11429 254 63  183622887
P Linux                11430   0  1 18142 254 63  107844345
P Linux Swap           18143   0  1 18280 254 63    2216970
P HPFS - NTFS          18281   0  1 19456 254 63   18892440 [HP_RECOVERY]

```

If you want me to run a deeper search or do something else with testdisk, just tell me.

---

### Post by oldfred on 2010-11-28
Testdisk does not seem to match the fdisk listing. It still shows the NTFS partition at the beginning of the drive. I thought testdisk showed old partitions but with a d and then you had to figure out if they overlapped or which was the correct version.

What does a fdisk from your parted magic boot show? Since that seems to be working.

---

### Post by Chevy787 on 2010-11-28
```

fdisk -lu

```
Returned this Parted Magic
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73e3aaa4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       293684265   312576704     9446220    7  HPFS/NTFS
/dev/sda3       291467295   293684264     1108485   82  Linux swap / Solaris
/dev/sda4            2048   291465215   145731584   83  Linux

Partition table entries are not in disk order

```

---

### Post by oldfred on 2010-11-28
It matches teh original fdisk. Not sure what testdisk was showing. Have not used it much.

Were you chrooting from Parted Magic or an older Ubuntu? Not sure if it would work with ext4 partition. Maybe that is why it did not mount?

---

### Post by Chevy787 on 2010-11-28
I've only attempted chrooting from the ubuntu 10.10 x64 live-cd
I can try doing it from Parted Magic and seeing what sorta results I get.

---

### Post by Chevy787 on 2010-11-28
Tried running it on Parted Magic
```

root@PartedMagic:~# mount /dev/sda4 /mnt && mount --bind /dev /mnt/dev && mount --bind /proc /mnt/proc && mount --bind /dev/pts /mnt/dev/pts && cp /etc/resolv.conf /mnt/etc/resolv.conf && chroot /mnt
cp: overwrite `/mnt/etc/resolv.conf'? y
chroot: can't execute '/bin/bash': Exec format error

```
Edit
Found this....
[URL="http://en.gentoo-wiki.com/wiki/Chroot_from_a_livecd#Exec_format_error"]Exec format error
If the chroot command returns with the error "chroot: cannot run command `/bin/bash': Exec format error", this usually indicates that the livecd environment is not compatible with that of the installed system.
For example, the error is most frequently seen when trying to chroot to a 64-bit system (eg. amd64) from a 32-bit livecd (eg. x86).[/URL]

I don't think there is a x64 Parted Magic...
Edit2:
Was looking around...
Would it be possible to just uninstall Grub and install Grub2? I found some instructions for deleting Grub and the MBR [here]("http://www.linuxquestions.org/questions/linux-hardware-18/how-to-remove-grub-using-partedmagic-789555/"), but I fear that destyoring the MBR would cause further problems.

---

### Post by oldfred on 2010-11-28
The quick version of installing grub2 to the MBR just mounts the install partition (and /boot if one) to install. The full version is a chroot and will probably give you the same error.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Chevy787 on 2010-12-24
took awhile...
Solution:
Booted from gentoo x64 live-cd
Followed: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
Seeminly works now.
Thanks for all the help, couldn't have done it without the all your guidance.

---

