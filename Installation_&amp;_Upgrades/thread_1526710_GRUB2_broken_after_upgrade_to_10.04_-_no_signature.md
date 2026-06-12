---
title: "GRUB2 broken after upgrade to 10.04 - no signature"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by dm239 on 2010-07-08
I took the distribution upgrade from the update manager and can't boot now. Boot into a Live CD (ver. 9.10 - does that matter?), and go through the following steps.

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad56f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90827   729567846   83  Linux
/dev/sda2           90828       91201     3004155    5  Extended
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
/usr/sbin/grub-setup: error: no signature.
root@ubuntu:/# grub-install --recheck /dev/sda
/usr/sbin/grub-setup: error: no signature.

Anyone have an idea here? I have searched a lot and have only found a few references to this issue.

Does the invalid flag message relate here? The partition is flagged as 'boot'.

---

### Post by dm239 on 2010-07-08
By the way, the error generated when I try to boot from the HDD is :

grub reloc offset is out of the segment

---

### Post by dm239 on 2010-07-08
For those who may have run into this as well, you can create a new partition, and when using the LiveCD/CHROOT method of recovering GRUB2 ([https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)), mount the new partition as /mnt/boot. From there, 'grub-install /dev/sda' worked. 

EXT3 resizing how-to here. Useful if the whole drive is one partition and you find that you need another:

[http://howtoforge.com/linux_resizing_ext3_partitions](http://howtoforge.com/linux_resizing_ext3_partitions)


After that I simply created the new partition while booted into the Live CD using GParted.

---

### Post by dm239 on 2010-07-08
So now the (seemingly easier) question is:
How do I get GRUB to see the linux images on sda1?

The system boots, but reaches the GRUB menu and stops.

---

### Post by oldfred on 2010-07-08
Post this so we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by dm239 on 2010-07-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 11809111 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ad56f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,398,811,679 1,398,811,617  83 Linux
/dev/sda2       1,459,135,755 1,465,144,064     6,008,310   5 Extended
/dev/sda5       1,459,135,818 1,465,144,064     6,008,247  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        324ede5a-79bb-43ee-82fe-6174eeff5248   ext4       UBUNTU                        
/dev/sda5        5afe2f7b-420c-435f-a282-7364333a2eb1   ext3       boot                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


============================= sda1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
set root=(hd0,1)
linux /boot/vmlinuz-2.6.31-20-generic root=UUID=ba123456-7890-abcd-efghijklmnop ro quiet splash
initrd /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=324ede5a-79bb-43ee-82fe-6174eeff5248 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=324ede5a-79bb-43ee-82fe-6174eeff5248 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=324ede5a-79bb-43ee-82fe-6174eeff5248 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=324ede5a-79bb-43ee-82fe-6174eeff5248 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=324ede5a-79bb-43ee-82fe-6174eeff5248 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b53a1f8f-7599-4223-b307-9c2bac723f09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.2GB: boot/grub/grub.cfg
  60.2GB: boot/initrd.img-2.6.31-21-generic
  52.4GB: boot/initrd.img-2.6.32-23-generic
 390.4GB: boot/vmlinuz-2.6.31-21-generic
  60.2GB: boot/vmlinuz-2.6.32-23-generic
   1.3GB: grub/core.img
   1.3GB: grub/grub.cfg
  52.4GB: initrd.img
  60.2GB: initrd.img.old
  60.2GB: vmlinuz
 390.4GB: vmlinuz.old

============================= sda5/grub/grub.cfg: =============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 324ede5a-79bb-43ee-82fe-6174eeff5248
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5afe2f7b-420c-435f-a282-7364333a2eb1
set locale_dir=($root)/grub/locale
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
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Other Linux" {
set root=(hd0,1)
linux /boot/vmlinuz (add other options here as required)
initrd /boot/initrd.img (if the other kernel uses/needs one)
}
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 747.6GB: grub/core.img
 747.7GB: grub/grub.cfg

```

---

### Post by dm239 on 2010-07-08
edited grub.cfg with this and got the boot menu to show the entry after running grub-mkimage:

menuentry "Other Linux" {
set root=(hd0,1)
linux /boot/vmlinuz (add other options here as required)
initrd /boot/initrd.img (if the other kernel uses/needs one)
}


so now, I guess I need to know how to get the kernel image names

---

### Post by oldfred on 2010-07-08
If you take out the /boot the "files" there are just links to the most current kernel & initrd in the /boot folder. You do not have to edit grub.cfg but at the menu just press e and edit the lines in the menu, then boot.
"/vmlinuz" and "/initrd.img" instead of "/boot/vmlinuz-............" and "/boot/initrd.img-.....". "/vmlinuz" and "/initrd.img are links to the newest kernel

It looks like you have tried installing grub2 a couple of extra times. You have what looks like just grub in sda5. Your install is in sda1 and you have an extra /grub.cfg in addition to the /boot/grub/grub.cfg

You need to remove the /grub/grub.cfg and any other files in /grub but be sure to keep all the files in /boot/grub.

Once you get into your system reinstall grub.
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by dm239 on 2010-07-09
OK, did that.

I can reach this point:

[http://yfrog.com/muscreenshotqemup](http://yfrog.com/muscreenshotqemup)

---

### Post by oldfred on 2010-07-09
Info on errors and booting from command line:

[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)
See errors section #15 for manual boot info
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot


Reinstall grub once booted:
Install grub to MBR:
sudo grub-install /dev/sda
sudo update-grub

---

### Post by dm239 on 2010-07-09
OK, starting from a LiveCD session:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad56f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       87072   699405808+  83  Linux
/dev/sda2           90828       91201     3004155    5  Extended
/dev/sda5           90828       91201     3004123+  83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo mount dev/sda5 /mnt/boot
mount: special device dev/sda5 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo chroot /mnt

I follow your process:
[http://yfrog.com/msscreenshotqemup](http://yfrog.com/msscreenshotqemup)

then BOOT, and it has booted to ubuntu in qemu



but this is where it gets when booting off the HDD:
[http://yfrog.com/3zwebdlj](http://yfrog.com/3zwebdlj)

I'm beginning to wonder about my hard drive

---

### Post by oldfred on 2010-07-09
You should not chroot into your system to boot it. When you just boot does it not just give a grub> line where you can type the commands.

From chroot you could reinstall grub2 or make other system updates.

---

