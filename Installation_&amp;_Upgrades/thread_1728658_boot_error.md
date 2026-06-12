---
title: "boot error"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by jsthrower on 2011-04-14
Tonight I installed ubuntu 10.10 (32 bit) on an external usb harddrive with a dvd I burned and I used my older desktop.  I disconnected all internal and external drives first so everything had to be put on the usb drive I selected (only option available).  I used the option to load extra software, use the entire hard drive, and let the software do it's thing.  I basically had no options where to put things and it didn't have much choice.  

When I boot the usb drive on my laptop (win 7 64 bit) by telling the bios to boot to it first... I get an error:
modprobe: FATAL Could not load /lib/modules 2.6.35-22 generic modules No such file or directory.

This message appears twice and then it does boot into ubuntu and seems to work fine.  I'm new to this OS so that is an uneducated guess but the things I have done seem to be  working.

So exactly what is this error referring too? Is there a way to fix the problem or do I just ignore it.

Also, does this OS automatically update or do I hopefully get to do it manually?

---

### Post by Hedgehog1 on 2011-04-14
A few things:

To keep Ubuntu updates from including the booting of your laptop hard drive, please do this from the terminal (Menu to: Applications >> Accessories >> Terminal) in Ubuntu:

```
sudo rm /etc/grub.d/30_os-prober
```


Next, so we can get a look at your various setup files and see why you are getting that annoying error, please do this:


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.


***The Hedge***

:KS

---

### Post by jsthrower on 2011-04-14
This is what I got when I did step one:  I guess it didn't accept my password the first time.

```
jst@ThrowerUbuntu:~$ sudo rm /etc/grub.d/30_os-prober
[sudo] password for jst: 
Sorry, try again.
[sudo] password for jst: 
jst@ThrowerUbuntu:~$ sudo rm /etc/grub.d/30_os-prober
rm: cannot remove `/etc/grub.d/30_os-prober': No such file or directory
jst@ThrowerUbuntu:~$ 

```

---

### Post by jsthrower on 2011-04-14
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   976,771,119   951,988,272   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   485,326,847   485,324,800  83 Linux
/dev/sdb2         485,328,894   488,396,799     3,067,906   5 Extended
/dev/sdb5         485,328,896   488,396,799     3,067,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        C4A8977AA89769A6                       ntfs       SYSTEM RESERVED               
/dev/sda3        C4309F26309F1F0C                       ntfs       Gateway                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0dc730b5-a957-4afe-b8f5-93288a4a95ca   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        bf075a99-4eb5-4e01-bde6-14f6b9b3c99f   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0dc730b5-a957-4afe-b8f5-93288a4a95ca ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0dc730b5-a957-4afe-b8f5-93288a4a95ca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0dc730b5-a957-4afe-b8f5-93288a4a95ca
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bf075a99-4eb5-4e01-bde6-14f6b9b3c99f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 184.9GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-22-generic
 184.9GB: boot/vmlinuz-2.6.35-22-generic
   1.0GB: initrd.img
 184.9GB: vmlinuz
```

---

### Post by Hedgehog1 on 2011-04-15
**[SIZE="3"]Good news! It is an easy fix...[/SIZE]**

Here is what is wrong:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**[COLOR="Red"]/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]**
# swap was on /dev/sda5 during installation
UUID=bf075a99-4eb5-4e01-bde6-14f6b9b3c99f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Your /etc/fstab (**F**ile **S**ystem **TAB**le) is referencing your '/' (root) partition by the (very changeable) /dev/sda1 reference, rather than by the reliable UUID reference for that partition (0dc730b5-a957-4afe-b8f5-93288a4a95ca)

Please do this from the terminal:

```
gksudo gedit /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**[COLOR="Red"]#[/COLOR]/dev/sda1       /               ext4    errors=remount-ro 0       1**
**[COLOR="Red"]UUID=0dc730b5-a957-4afe-b8f5-93288a4a95ca /               ext4    errors=remount-ro 0       1[/COLOR]**
# swap was on /dev/sda5 during installation
UUID=bf075a99-4eb5-4e01-bde6-14f6b9b3c99f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

The '#' sign make the old line a comment.  You can cut and paste the new line in - it is correct for your install based on the script output you gave me.

Then save the file, and reboot.  The annoying error messages should stop.

***The Hedge***

:KS

---

### Post by jsthrower on 2011-04-15
Thanks Hedge:  But it didn't work.  I first tried to just add the lines in red  to the file but it didn't help, so I copy and paste your entire code replacing the original and saved but it still boots the same errors.  
If you think of anything else let me know.

---

### Post by lmarmisa on 2011-04-15
Once you have modified the file fstab, you will need to reinstall GRUB2. This is not difficult.

Boot from a Ubuntu Live CD, open a terminal and type:

```

sudo fdisk -l

```

Verify that the Ubuntu and swap partitions are located on the drive /dev/sdb.

Then continue with these commands:

```

sudo mount /dev/sdb1 /mnt 
sudo mount --bind /dev /mnt/dev 
sudo mount --bind /dev/pts /mnt/dev/pts 
sudo mount --bind /proc /mnt/proc 
sudo mount --bind /sys /mnt/sys 
sudo chroot /mnt 
grub-install /dev/sdb
grub-install --recheck /dev/sdb 
exit 
sudo umount /mnt/dev/pts 
sudo umount /mnt/dev 
sudo umount /mnt/proc 
sudo umount /mnt/sys 
sudo umount /mnt 

```

Finally reboot your system from your external drive.

---

### Post by jsthrower on 2011-04-16
Before I go further ... a few questions.  First I'm clueless about this  code but studying it  I'm assuming when I put ubuntu on the usb external  hardrive with all other drives on my desktop unplugged ... the external  hard drive at that point was sda (because it was the only drive  present)

Then when I plugged it into my laptop where I am going to be booting it,  my win 7 internal hard drive becomes sda and the usb (ubuntu) external becomes sdb,  which is why you want me to reference UUID=0dc730xxxxxxxxxx in the fstab. Because that id is constant.

So as long as the usb external (Ubuntu) hard drive is plugged into my laptop it will always be seen as sdb whether I plug it in when I'm booted into win7 .... or whether it's plugged into the laptop and I boot it into ubuntu with the bios.  Meaning, in my laptop it will never be seen as sda as long as the internal harddrive is present no matter how I boot the laptop.

Sorry for the questions but I want to understand what I am doing so I don't mess up my win7 and it's bootloader.  

Now Imarmisa says to verify ubuntu and swap partitions are on sdb. and to reload grub on the sdb with the code supplied.  Didn't we remove grub in the first step to stop auto updates to prevent it from accidentally installing on my win7 drive.  or was that for some other reason.  Also is it going to reinstall the original version (I assume it's already residing on the hard drive... or do I need to download a version and install that.

---

### Post by jsthrower on 2011-04-16
One more question....What language is this so I can get a book and learn it.

---

### Post by jsthrower on 2011-04-16
I did everything requested to this point...Still get the error on boot but I am learning a lot as I go. I appreciate the help. Thanks.

---

### Post by jsthrower on 2011-04-17
I decided to pull the internal hard drive out of the laptop and download and install the 397MB  of updates listed to the ubuntu usb drive.  This installed 2.6.35.28 generic kernels in the process.  Now when I boot the ubuntu usb drive I actually get a boot loader window (first time I've seen that) with about eight choices to boot to, the top being the new 2.6.35.28 generic.      .22 is still a choice but I won't be going there.  The error has disappeared, the boot time is no faster but that may have something to do with the usb drive speeds.  It's still less than one minute.  Thanks for the help and the knowledge.  Now on to learning something new.  I spent a while last night tweaking the appearance and I'm really liking the look of this OS now.

---

### Post by Dutch70 on 2011-04-17
If you want to remove any of the old kernels, open synaptic & search for linux-image-2. It's best to keep at least 2 & Be careful not to remove the wrong ones.

---

### Post by jsthrower on 2011-04-20
Thanks for that info.  I'll need it one day.

---

### Post by Dutch70 on 2011-04-20
I'm not sure why I didn't mention this, but "Ubuntu Tweak" is a great program & will do it for you.
Sometimes kernel updates cause serious problems, and so it's best to keep 2 kernels. 

To install it either use software center, or...
```
sudo apt-get install ubuntu-tweak
```

---

