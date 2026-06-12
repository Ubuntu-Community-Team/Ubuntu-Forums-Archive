---
title: "Ubuntu on External HDD partition - Grub rescue error"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by K1251 on 2011-05-05
Let me start by saying that I am completely new to Ubuntu and Linux as a whole. I have searched the forum and help guides but I haven't yet come across a solution to my problem.

Basically, my goal is for Ubuntu to be installed on an empty partition of an external USB hard drive that already has two other partitions full of stuff, so formatting isn't really an option. If that makes it impossible then just tell me and I dunno, I'll buy a new hard drive or something. So anyway, I had about 20GB of empty space created by shrinking an existing partition on the external drive in Windows. I gave 4GB to swap (I have 2GB RAM), and the remaining space I let the installer format to ext4 and mount to /. It asked where the bootloader should be, and having looked it up on the internet, I put it just on the drive itself, not any specific partition.

Installation finished, rebooted, and I get something like "not found, grub rescue>"

Like I said, I've never used Ubuntu so I probably made some really rookie error here, but any help in sorting this would be great. Oh, and I'll be starting from scratch, as I have already deleted the partition I created so I now once again have 20GB of unallocated space.

Thanks in advance,

- K.

---

### Post by chellrose on 2011-05-05
I'd recommend putting the bootloader on your Ubuntu partition.

---

### Post by drs305 on 2011-05-05
It sounds like you had a good plan. When you reinstall, if you have problems you can run and post the RESULTS.txt of the boot info script found here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
Just run the script (from the LiveCD if necessary) with your external plugged in.

Installing Grub2 to the external drive will allow your normal bootloader on your internal drive to boot when the external isn't connected, and from the external drive when it is. You just have to set up the BIOS to boot first from your external, then your internal drive if BIOS doesn't find the external one.

Normally you would install it to the MBR of the drive unless you have a reason to install it to a partition.

---

### Post by K1251 on 2011-05-05
OK, just did a fresh install and put the bootloader on Ubuntu partition as per Sissy13's advice, but I still get

```
error: no such partition.
grub rescue>
```

upon rebooting. I disconnected the computer's internal drives before installation, to ensure the boot on there would not be affected.

I will try the boot info scrips and get back to you.

- K.

---

### Post by K1251 on 2011-05-05
Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2can.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   616,321,342   616,321,280   7 HPFS/NTFS
/dev/sda2    *    657,283,410   976,768,064   319,484,655  af HFS
/dev/sda3         616,323,070   657,283,071    40,960,002   5 Extended
/dev/sda5         616,323,072   624,134,143     7,811,072  82 Linux swap / Solaris
/dev/sda6         624,136,192   657,283,071    33,146,880  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        54A465F9A465DDCC                       ntfs       Iomega HDD                    
/dev/sda2        fcb45008-8d99-3671-b5f1-045ef0147536   hfsplus    Time Machine                  
/dev/sda3: PTTYPE="dos" 
/dev/sda5        0889c1f1-cbb7-42e5-8ce1-fbd03aeb9dc4   swap                                     
/dev/sda6        08b2454a-4cb4-43d0-a3c0-af7252aa87bb   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=08b2454a-4cb4-43d0-a3c0-af7252aa87bb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=08b2454a-4cb4-43d0-a3c0-af7252aa87bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 08b2454a-4cb4-43d0-a3c0-af7252aa87bb
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
UUID=08b2454a-4cb4-43d0-a3c0-af7252aa87bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0889c1f1-cbb7-42e5-8ce1-fbd03aeb9dc4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 332.6GB: boot/grub/core.img
 332.6GB: boot/grub/grub.cfg
 329.2GB: boot/initrd.img-2.6.38-8-generic
 332.6GB: boot/vmlinuz-2.6.38-8-generic
 329.2GB: initrd.img
 332.6GB: vmlinuz
```

---

### Post by drs305 on 2011-05-05
Ok, I'll assume you still have your internal disconnected.

There is a bit of a glitch with the boot info script on Natty which doesn't allow us to see exactly which partition Grub2 is installed (it's on 'b2can' according to the script).

My advice would be to install it on the MBR. To do this, if you have the same setup (the internal disconnected and Ubuntu on sda for now):
```
sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Don't include the partition number in the second command, unless you have a specific need to have it on the partition instead of the MBR.

That may fix it, although it should have installed correctly in the first place.

As you reboot, we can check the second possibility. If your BIOS can only see the first 137GB of the drive, Grub is not going to be able to boot. All your G2 and boot files are well past this limit. You can check by entering BIOS setup during boot and checking the disk size. If it only reports a drive of approximately 137GB, there are several options to fix it that we can go over.

For now, after running the above commands, reboot, check the BIOS settings, then continue and see if it boots.

---

### Post by K1251 on 2011-05-05
Did both commands, it said it had installed grub successfully.

Rebooted, I still get the grub rescue error. Trying to see what BIOS says about drive size, but I can't find it anywhere. It recognises that there is a drive, but doesn't list a size. I'll keep looking.

---

### Post by drs305 on 2011-05-05
> **K1251 said:**
> Did both commands, it said it had installed grub successfully.

Rebooted, I still get the grub rescue error. Trying to see what BIOS says about drive size, but I can't find it anywhere. It recognises that there is a drive, but doesn't list a size. I'll keep looking.

Another way to check is to run some commands at the grub prompt:

```
ls # Does it see the partitions, especially sda6 (hd0,6). It should.
ls (hd0,6)/ # Does it see the 'vmlinuz' and 'initrd' files?
ls (hd0,6)/boot/grub # Does it see a lot of *.mod files?
ls (hd0,6)/boot/grub/grub.cfg  # Does it find this file?
```
Since you are getting the grub rescue prompt, I believe it is seeing the grub folder. If the answers to all the above are positive, and what I've added below doesn't work, then what I would recommend is purging and reinstalling Grub2 via the 'Chroot' link in my signature.

(While you are poking around the BIOS, you can also look for a setting that enables large drives, or a LBA option.)

Added: If you want to try to boot from the rescue prompt, run these commands if it found the files above:
```
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod (hd0,6)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda6 ro
initrd /initrd.img
boot
```

---

### Post by K1251 on 2011-05-05
Entering ls gives:

```
(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)
```

ls (hd0,6)/ gives "error: no such partition"

Oh, and there doesn't seem to be any option for large drives.

---

### Post by drs305 on 2011-05-05
> **K1251 said:**
> Entering ls gives:

```
(hd0) (hd0,msdos2) (hd0,msdos1) (fd0)
```

ls (hd0,6)/ gives "error: no such partition"

Oh, and there doesn't seem to be any option for large drives.

I can't guarantee it but strongly suspect your BIOS can't see that far into the disk. Your options are:

a. change a setting in BIOS to enable large drives (a setting you don't seem to have), 
b. update the BIOS from your motherboard manufacturer 
c. shrink the Ubuntu partition or move it so the /boot folder is within the first 137GB (there are smaller limitations, but those BIOS limits would be on very old systems),
d. Create a small /boot partition within the early sectors of the drive.

You might be able to put the /boot folder on your internal drive. I have no experience with this but expect it can be done without too much difficulty.

---

### Post by K1251 on 2011-05-05
Thanks for the help. I think what I'll have to do is temporarily take everything off the drive, format it, install Ubuntu in a partition at the beginning of the drive, and then recreate the previous partitions further on in the drive.

Unless there's an easier way to move the Ubuntu partition to the beginning of the drive without formatting the whole thing?)

Thanks again.

- K.

---

### Post by drs305 on 2011-05-05
> **K1251 said:**
> Thanks for the help. I think what I'll have to do is temporarily take everything off the drive, format it, install Ubuntu in a partition at the beginning of the drive, and then recreate the previous partitions further on in the drive.

Unless there's an easier way to move the Ubuntu partition to the beginning of the drive without formatting the whole thing?)

Thanks again.

- K.

If you have the ability to copy the contents of the other partitions, copying them, deleting everything, and reformatting is going to be your fastest (and safest) way of doing this.

I'd test the Ubuntu installation before putting the other two partitions back on, just in case there are problems...  ;-)

---

### Post by K1251 on 2011-05-06
> **drs305 said:**
> Another way to check is to run some commands at the grub prompt:

```
ls # Does it see the partitions, especially sda6 (hd0,6). It should.
ls (hd0,6)/ # Does it see the 'vmlinuz' and 'initrd' files?
ls (hd0,6)/boot/grub # Does it see a lot of *.mod files?
ls (hd0,6)/boot/grub/grub.cfg  # Does it find this file?
```



Ok. I wiped the entire external disk and did a clean install of Ubuntu to it. This time I didn't make the partitions myself, I just did "use entire drive" and let it do it all for me. I STILL get the grub rescue error, except this time it says "file not found" rather than "no such partition".

ls gives: (hd0) (hd0,msdos1) (fd0)

ls (hd0,msdos1)/ shows this:

```
./ ../ lost+found/ var/ etc/ media/ bin/ boot/ dev/ home/ lib/ mnt/ opt/ proc/ 
root/ sbin/ selinux/ srv/ sys/ tmp/ usr/ vmlinuz initrd.img cdrom/
```

I tried doing ```
ls (hd0,msdos1)/boot/grub
``` and ```
ls (hd0,msdos1)/boot/grub/grub.cfg
``` The first results in "unknown filesystem" and the second in "file not found."

I'm stumped. Any ideas?

---

### Post by Quackers on 2011-05-06
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by K1251 on 2011-05-06
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for b2d.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

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

/dev/sda1    *          2,048   972,580,863   972,578,816  83 Linux
/dev/sda2         972,582,910   976,771,071     4,188,162   5 Extended
/dev/sda5         972,582,912   976,771,071     4,188,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        30dde448-11ba-4d1a-9af8-fa6cb94c36cb   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        16c0fe76-11d2-42ef-85b2-504caea3883c   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=30dde448-11ba-4d1a-9af8-fa6cb94c36cb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=30dde448-11ba-4d1a-9af8-fa6cb94c36cb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 30dde448-11ba-4d1a-9af8-fa6cb94c36cb
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

=============================== sda1/etc/fstab: ===============================

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
UUID=16c0fe76-11d2-42ef-85b2-504caea3883c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 468.2GB: boot/grub/core.img
 468.2GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.38-8-generic
 468.2GB: boot/vmlinuz-2.6.38-8-generic
   1.2GB: initrd.img
 468.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  32 38 36 22 20 68 65 69  67 68 74 3d 33 44 22 31  |286" height=3D"1|
00000010  30 30 22 3e 3c 2f 74 64  3e 20 20 20 20 20 20 20  |00"></td>       |
00000020  20 20 20 20 20 20 20 20  20 20 3c 2f 74 72 3e 20  |          </tr> |
00000030  20 20 20 20 20 20 20 20  20 20 20 20 20 3d 0a 20  |             =. |
00000040  20 20 3c 74 72 3e 20 20  20 20 20 20 20 20 20 20  |  <tr>          |
00000050  20 20 20 20 20 20 20 20  20 20 20 3c 74 64 20 77  |           <td w|
00000060  69 64 74 68 3d 33 44 22  32 38 36 22 20 68 65 69  |idth=3D"286" hei|
00000070  67 68 74 3d 33 44 22 35  30 22 3e 3c 66 6f 6e 74  |ght=3D"50"><font|
00000080  20 66 61 63 65 3d 33 44  22 48 3d 0a 65 6c 76 65  | face=3D"H=.elve|
00000090  74 69 63 61 2c 20 47 65  6e 65 76 61 2c 20 41 72  |tica, Geneva, Ar|
000000a0  69 61 6c 2c 20 53 75 6e  53 61 6e 73 2d 52 65 67  |ial, SunSans-Reg|
000000b0  75 6c 61 72 2c 20 73 61  6e 73 2d 73 65 72 69 66  |ular, sans-serif|
000000c0  22 3e 3c 61 20 6e 61 6d  65 3d 33 44 22 77 77 77  |"><a name=3D"www|
000000d0  5f 6d 75 73 65 5f 6d 3d  0a 75 22 20 73 74 79 6c  |_muse_m=.u" styl|
000000e0  65 3d 33 44 22 74 65 78  74 2d 64 65 63 6f 72 61  |e=3D"text-decora|
000000f0  74 69 6f 6e 3a 20 6e 6f  6e 65 3b 22 20 20 74 61  |tion: none;"  ta|
00000100  72 67 65 74 3d 33 44 22  5f 62 6c 61 6e 6b 22 20  |rget=3D"_blank" |
00000110  68 72 65 66 3d 33 44 22  68 74 74 70 3a 2f 2f 6c  |href=3D"http://l|
00000120  69 6e 6b 73 3d 0a 2e 6d  6b 74 31 33 39 37 2e 63  |inks=..mkt1397.c|
00000130  6f 6d 2f 63 74 74 3f 6b  6e 3d 33 44 32 26 6d 3d  |om/ctt?kn=3D2&m=|
00000140  33 44 33 34 35 31 33 35  33 36 26 72 3d 33 44 4d  |3D34513536&r=3DM|
00000150  7a 63 77 4e 44 4d 32 4d  7a 41 33 4e 77 53 32 26  |zcwNDM2MzA3NwS2&|
00000160  62 3d 33 44 30 26 6a 3d  33 44 4e 6a 4d 77 4d 44  |b=3D0&j=3DNjMwMD|
00000170  63 3d 0a 35 4e 6a 55 53  31 26 6d 74 3d 33 44 31  |c=.5NjUS1&mt=3D1|
00000180  26 72 74 3d 33 44 30 22  3e 77 77 77 2e 6d 75 73  |&rt=3D0">www.mus|
00000190  65 2e 6d 75 3c 2f 61 3e  20 7c 20 3c 61 20 77 77  |e.mu</a> | <a ww|
000001a0  77 5f 6d 79 73 70 61 63  65 5f 63 6f 6d 5f 6d 75  |w_myspace_com_mu|
000001b0  73 65 3d 33 44 22 22 20  73 74 79 6c 65 3d 00 fe  |se=3D"" style=..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-05-06
Ok thanks.
From the live cd desktop please open up a terminal and copy/paste these commands in, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
which when run should report no errors. If that is the case please reboot and see if Ubuntu then boots.

---

### Post by K1251 on 2011-05-06
Ok.

No errors were reported. Rebooted, I still get grub rescue.

---

### Post by K1251 on 2011-05-06
Anything else I can try?

---

### Post by Quackers on 2011-05-06
Sorry for the delay. I've been looking over the boot script output.
It seems from the later part of the output (see below) that your grub files are still way up the disc, rather than near the beginning, as drs305 hoped.
```
=================== sda1: Location of files loaded by Grub: ===================


 468.2GB: boot/grub/core.img
 468.2GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.38-8-generic
 468.2GB: boot/vmlinuz-2.6.38-8-generic
   1.2GB: initrd.img
 468.2GB: vmlinuz
```

As you have installed Ubuntu on an empty disc this is puzzling to me (and could still explain the failure to boot, if the bios can't see that far up the disc).
See that /boot/grub/core.img and /boot/grub/grub.cfg and /boot/vmlinuz-2.6.38-8-generic and vmlinuz are all placed 468.2GB into the disc. I would expect those to be much nearer the beginning of the disc now.

---

### Post by K1251 on 2011-05-06
Right ok. Could it be that when I erased the disk, I didn't format to any thing I just deleted all partitions leaving unallocated space, so maybe the installer recognised the grub that was already on there and left it there?

Then again the installer should have formatted the whole disk while installing. Would it be worth using windows to format the disk to I dunno, NTFS or something, just to zero out what's already on there?

- K.

---

### Post by Quackers on 2011-05-06
No, I don't think so.
Can I ask what is your boot priority setting in bios?
What is set to boot first/second/third etc?

---

### Post by K1251 on 2011-05-06
Boot priority is normally:

Internal HDD (RAID)
External USB (The one I'm loading Ubuntu on)
CD
Floppy

But right now (and throughout the installation) I have the internal RAID unplugged so the External USB is 1st priority.

---

### Post by Quackers on 2011-05-06
Try swapping the first two around so that USB HDD is first and see if things improve.

---

### Post by K1251 on 2011-05-06
It is 1st though, internal disappears from the boot list when unplugged. Do you mean I should change the priority with the internal connected?

UPDATE: I did it, still get grub rescue.

---

### Post by Quackers on 2011-05-06
No, it's ok. I thought from what you said that the internal HDD was still listed first in the bios even though it was disconnected.
You could try purging and re-installing grub again using the chroot method in drs305's guide.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
I'm not sure what's going on really. Maybe drs305 will be back soon with some ideas :-)

---

### Post by K1251 on 2011-05-06
Ok, thanks for the help anyway. I will get Ubuntu to boot if it kills me!

---

### Post by Quackers on 2011-05-06
Yes, I'm sure we'll get there between us.
I'm still curious about the positioning of your /boot file. It's odd for a new installation on a clean disc.

---

### Post by oldfred on 2011-05-06
I am suspicious that it is a BIOS setting as drs305 mentioned before. Since you have RAID on the internal not sure how it sees external. 

I would try an install with a small system partition at the front of the drive and make the rest of the drive /home. You could reinstall or if you just want to test, you could try shrinking the system partition. It has to move all the data at the end of the drive to the front, so it may be faster just to reinstall.

If you make a 25GB / (root) partition as the first one on the drive and then have /home & swap later on the drive does it work?

---

### Post by K1251 on 2011-05-06
Interesting... The fact that it's 468GB into the drive must mean it's at the very end. I'm looking at the disk in Vista's Disk Management, and it has 2 partitions: 463GB, and 2GB (presumably swap)

So if it's 468GB into the disk it must be after both partitions.

Oh and when I get this all working, I'm assuming I can safely use gparted to shrink the Ubuntu partition down to about 30GB and free up the other 430GB for my other partitions? I really don't need 460GB of Ubuntu... :D

EDIT: oldfred, I'll try that, hold on.

---

### Post by K1251 on 2011-05-06
We have lift off. Thanks oldfred, that worked! (and thank you drs305 and Quackers too)

Given that I'm a massive noob, I'm sure I'll be back with more problems before too long :D

Until then...

- K.

---

### Post by Quackers on 2011-05-06
Good idea oldfred :-)  
It still seems curious to me that a fresh install on an empty disc would put the grub files at the end of the disc. Mine doesn't do that. I'm still a bit perplexed, but happy the problem has been sorted out :-)

---

### Post by K1251 on 2011-05-06
One more small problem, if anyone's still around. 

I am unable to shrink the home partition from gparted. Any easy way round this or 3rd party app I could use?

---

### Post by oldfred on 2011-05-06
Glad that worked. I still think it may be a BIOS setting, but I have seen similar issues with 1 & 2TB drives where boot script showed some files at the end of the drive. Not optimal from a drive speed issue either as drive heads then have to jump all over drive to run system. Best to have smaller system partition. But some recommend only 25% use of system partition after install.

You have to use a liveCD and usually click on swap partition and right click swapoff, so all partitions are unmounted. If running gparted from your install you cannot unmount the partition(s) you are in. (Little key symbols show mounted.)

---

### Post by drs305 on 2011-05-06
I'm glad you have finally sorted the installation problem out. As with others, I am puzzled that a clean install placed the /boot files that far into the disk. Having your separate /boot partition should keep you out of future trouble on this front.

Since it appears to have been a BIOS problem, when you have time you might want to see if there is an upgrade to your BIOS. I am of the school that you shouldn't update the BIOS unless you absolutely have to. Since it's working now, I probably wouldn't. But in the future if you have to reformat the drive again it might be worth looking into.

As *oldfred* suggested, if you boot the LiveCd and ensure all your partitions are unmounted, including the swap partition (in Gparted: Partition > Swapoff), you should be able to proceed with your resizing.

Happy Ubuntu-ing !

---

### Post by aimwin on 2012-01-09
I have the same issue, on my old ASUS and Think PAD and even MSI Net book they all cannot boot from
FreeAgent Gloflex seagate 1 TB
I have 3 Ntfs 300+GB partition, 
(on extended partition)
8GB swap 
and 50+GB EdUbuntu, "last" partition.
It will boot into Grub Rescue only.
type "ls" command
Grub Rescue> ls
produce
(hd0) (hd0,msdos2) (hd0,msdos1)

to show only 2 partitions, no Ubuntu partiontion not even the third Ntfs partition.

After reading this Thread,

I went to borrowed my daughter's computer, HP dv3-2139TX
without modifying any partition nor any thing as 
K1251 has done. 

And it boots into External USB hard disk with no problems.

I wish I saw this Thread 5 hours earlier.
What a waste of my time.

So anyone got the same Grub Rescue> issue 
try the "Newer Model of computer" which Bios should support large external hard disk.

Thanks everyone for the info

---

