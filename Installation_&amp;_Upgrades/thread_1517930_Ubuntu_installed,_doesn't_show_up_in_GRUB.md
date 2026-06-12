---
title: "Ubuntu installed, doesn't show up in GRUB"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Lijnk on 2010-06-25
I recently put Ubuntu 10.04 on my netbook. The installation went perfectly fine, but when I get into GRUB, the entry to load Ubuntu 10.04 is missing. The only thing that I can think of to do is to modify the grub.cfg file since it doesn't seem to be able to find Ubuntu when using this suggestion:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The terminal said everything was all right and the installation finished, but then when I reboot, GRUB hasn't actually changed at all. I'm pretty much at a loss as to what to do next.

EDIT: Solved. I reinstalled the distro. See [this post](http://ubuntuforums.org/showpost.php?p=9527860&postcount=16) for more details.

---

### Post by darkod on 2010-06-25
What is the other OS you are running?

---

### Post by Lijnk on 2010-06-25
Windows 7 Starter.

---

### Post by darkod on 2010-06-26
Sounds very odd grub2 to have entry for win7 but not for ubuntu. Unless you installed wubi inside windows but are saying you installed ubuntu. Because there is huge difference.

Go to the link in my signature and run the boot info script as per the instructions there. Post the content of the results file as it says, that will show us more details of your setup.

---

### Post by Lijnk on 2010-06-26
Here's the boot info:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *          2,048   167,772,159   167,770,112   7 HPFS/NTFS
/dev/sda2         167,774,206   208,787,455    41,013,250   5 Extended
/dev/sda5         167,774,208   173,631,487     5,857,280  82 Linux swap / Solaris
/dev/sda6         173,633,536   193,163,263    19,529,728  83 Linux
/dev/sda7         193,165,312   208,787,455    15,622,144  83 Linux
/dev/sda3         291,569,664   312,541,183    20,971,520  1b Hidden W95 FAT32
/dev/sda4         208,796,805   291,563,684    82,766,880   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2A06D0A206D07075                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        86F4-D40A                              vfat                                     
/dev/sda4        3F19E35E258F5F75                       ntfs                                     
/dev/sda5        cffc7c11-1cc9-456b-9c90-7ffe90ea463e   swap                                     
/dev/sda6        bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72   ext4                                     
/dev/sda7        7c57d339-a3c2-4ee0-8117-283786b18b2f   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         9646-389E                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2a06d0a206d07075
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod fat
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 86f4-d40a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=bf1f74fb-0f68-4701-81e8-6a7c6e6eaa72 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7c57d339-a3c2-4ee0-8117-283786b18b2f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=cffc7c11-1cc9-456b-9c90-7ffe90ea463e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  91.1GB: boot/grub/core.img
  91.2GB: boot/grub/grub.cfg
  91.3GB: boot/initrd.img-2.6.32-21-generic
  91.3GB: initrd.img

```

---

### Post by Sonsum on 2010-06-26
Maybe try booting it manually? [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto")

And if the method described here doesn't work, do a little Googling. I found a method somewhere which I could use to boot Ubuntu and Windows perfectly when my grub install was messed up.

Once you get back to Ubuntu run "sudo update-grub".

Hopefully that'd fix your problem.

---

### Post by Lijnk on 2010-06-27
tried to boot manually using:

```

grub> set root=(hd0,6)
grub> chainloader +1
grub> boot

```

However I got 'invalid signature' after the 'chainloader +1' command.

---

### Post by confused57 on 2010-06-27
Here are Herman's instructions for booting from grub's cli:
[http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html#How_To_Enter_GRUBs_CLI_MODE](http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html#How_To_Enter_GRUBs_CLI_MODE)

---

### Post by darkod on 2010-06-27
Good luck booting it manually, you have no kernels:

91.1GB: boot/grub/core.img
  91.2GB: boot/grub/grub.cfg
  91.3GB: boot/initrd.img-2.6.32-21-generic
  91.3GB: initrd.img

I have no idea how it happened. Anyone knows how to add a kernel in chroot?

You will need to chroot into your install from live mode:

sudo -i
mount /dev/sda6 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt

Some people have reported apt-get doesn't work with chroot /mnt, maybe you'll need instead of the last command:
chroot /mnt/bin/bash

Try to add the kernel:

apt-get install linux-image

I have never done this so I don't know if it will work with these exact commands. Maybe someone else will jump in. Update the grub.cfg:

update-grub

Exit the chroot and unmount:

exit
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc

Restart and if it worked, you'll see different menu.

---

### Post by Lijnk on 2010-06-27
Everything worked and showed no error, however when getting the new image, It returned that it was already installed. I skipped to updating the grub and it only returned the same list it already has, so no new changes have been made.

---

### Post by Lijnk on 2010-06-28
Anyone have a solution to what's going on? :confused:

---

### Post by confused57 on 2010-06-28
I don't know what's going on with your install, but found this:
[http://www.linuxquestions.org/questions/ubuntu-63/crash-and-kernel-reinstall-719188/](http://www.linuxquestions.org/questions/ubuntu-63/crash-and-kernel-reinstall-719188/)

Try chrooting into your install per Darko's instructions and running the commands in post#2 from the above link.

Edit:  On second thought, it probably wouldn't work, since uname -r wouldn't find a kernel installed.

---

### Post by Lijnk on 2010-06-29
Tried it anyways and, as you said, there was no change.

---

### Post by wilee-nilee on 2010-06-29
> **Lijnk said:**
> Tried it anyways and, as you said, there was no change.

If it was me I would make sure you have a good ISO with a md5sum check and delete the Lucid install and reinstall. I believe this is a fresh install so you have nothing to save just reinstall it. You would use gparted in the install thumb or cd to remove Lucid.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by darkod on 2010-06-29
We can make another "desperate" attempt, using the full filename of the kernel:

I'll start from the chroot command to save time, you have the previous commands in my earlier post.

chroot /mnt
apt-get update
apt-get --reinstall install linux-image-2.6.32-22-generic

If that still doesn't do anything, make another attempt with /bin/bash in the chroot, I'm still not sure if you need it or not:

chroot /mnt /bin/bash
apt-get update
apt-get --reinstall install linux-image-2.6.32-22-generic

---

### Post by Lijnk on 2010-06-29
I got it to work :p, but I'll put some information for the next person to get the same problem:

I didn't even try the last part and skipped to reinstalling it all. My .iso file was perfectly fine, I do a md5checksum against all linux image files before mounting them. I'm thinking it may have to do with how I partitioned everything. Initially, I had a logical partition (sda2) with everything in it (swap space, /, /home). When I first tried it, it wouldn't let me put the / mount point in, so I had to put swap first, then /, then /home. When I redid the install, I was able to put / first, then /home all in separate partitions (I didn't redo the swap space since that would be redundant).

Thanks to all that helped with my problem (especially darkod).

---

### Post by darkod on 2010-06-29
I don't think the order of the partitions made any difference. The new install probably simply installed the kernel this time, as it was supposed to do it last time too.
Anyway, it's working now. :)

---

### Post by Lijnk on 2010-06-29
Probably one of those weird flukes that happened. At least it's solved and I can go on to fixing other problems like customizing the UI :lol:.

---

