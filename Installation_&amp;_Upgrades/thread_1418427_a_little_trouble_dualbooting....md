---
title: "a little trouble dualbooting..."
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by timpletin on 2010-02-28
ok, so i did some research and tinkering for about 2 hours with no luck and i finally just decided to ask

so I'm trying to dualboot Windows 7 and Ubuntu both on a seperate hard drive (bios and cables are set to boot the w7 one first if that matters), but i can only get into ubuntu

i followed [this]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/") guide as a supposed fix, but with no luck

this is what fdisk -l gave me
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
135 heads, 14 sectors/track, 124043 cylinders
Units = cylinders of 1890 * 512 = 967680 bytes
Disk identifier: 0x950f950f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2         110      102400    7  HPFS/NTFS
/dev/sda2             110      124041   117114880    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084126

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9598    77095903+  83  Linux
/dev/sdb2            9599       10011     3317422+   5  Extended
/dev/sdb5            9599       10011     3317391   82  Linux swap / Solaris

```i then used that information to make the file 11_windows in grub.d which looks like this

```
#! /bin/sh -e
echo &#8220;Adding Windows&#8221; >&2
cat << EOF
menuentry &#8220;Windows 7&#8243; {
set root=(sda,1)
chainloader +1
}
EOF
```is there anything wrong with that? i think the set root= might be off, but im not sure, or are there any other solutions?

i also tried grub-update which gave me
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

i can see my windows 7 isnt listed, but i dont really know what to do beyond that

thanks alot for any help ;)

---

### Post by darkod on 2010-02-28
If you had the windows disk unplugged during ubuntu install, it's not aware of it. Delete (or just move out of the /etc/grub.d folder) your 11_windows file for the moment, and first try running:

sudo update-grub

Does that detect windows? If it did, you should be able to see it in the grub boot menu now.

---

### Post by timpletin on 2010-02-28
> **darkod said:**
> If you had the windows disk unplugged during ubuntu install, it's not aware of it. Delete (or just move out of the /etc/grub.d folder) your 11_windows file for the moment, and first try running:

sudo update-grub

Does that detect windows? If it did, you should be able to see it in the grub boot menu now.

tried that, still no luck :(

---

### Post by darkod on 2010-02-28
It's better to run the boot info script than guessing around. :) There are instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of your results file for more info.

---

### Post by Maintech on 2010-02-28
> **timpletin said:**
> tried that, still no luck :(

I am having the same issue. I have spent 6 hours trying to get Ubuntu 9.10 to dualboot with win7. It seems I have hosed my win7 now because grub won't recognize it and the win7 recovery disk tells me the mbr is an "unrecognizable filesystem". Nothing on the disk will repair it. So, it looks like I get to spend another several hours doing a reinstall of win7. I have tried several methods of getting Ubuntu to recognize win7 in grub and none have worked.  :mad:

---

### Post by timpletin on 2010-02-28
> **darkod said:**
> It's better to run the boot info script than guessing around. :) There are instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of your results file for more info.

ha was just in the process of doing that :P

heres the results:
i didnt run it on a liveCD tho, which seems to be MIA
 

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_feefdaec1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

nvidia_feefdaec2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
135 heads, 14 sectors/track, 124043 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x950f950f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   234,436,607   234,229,760   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00084126

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   154,191,869   154,191,807  83 Linux
/dev/sdb2         154,191,870   160,826,714     6,634,845   5 Extended
/dev/sdb5         154,191,933   160,826,714     6,634,782  82 Linux swap / Solaris


Drive: nvidia_feefdaec ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_feefdaec: 120.0 GB, 120034099200 bytes
135 heads, 14 sectors/track, 124043 cylinders, total 234441600 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x950f950f

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_feefdaec1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/nvidia_feefdaec2            206,848   234,436,607   234,229,760   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_feefdaec1 1C14FE4914FE2604                       ntfs       System Reserved               
/dev/mapper/nvidia_feefdaec2 8C4C0E8B4C0E6FEE                       ntfs                                     
/dev/sda1        1C14FE4914FE2604                       ntfs       System Reserved               
/dev/sda2        8C4C0E8B4C0E6FEE                       ntfs                                     
/dev/sda                                                nvidia_raid_member                               
/dev/sdb1        bd2904af-3341-4776-b27d-d5d0fc38f21b   ext4                                     
/dev/sdb5        0ec7dd61-f838-4695-b508-0182a1f92b17   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set bd2904af-3341-4776-b27d-d5d0fc38f21b
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bd2904af-3341-4776-b27d-d5d0fc38f21b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bd2904af-3341-4776-b27d-d5d0fc38f21b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set bd2904af-3341-4776-b27d-d5d0fc38f21b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bd2904af-3341-4776-b27d-d5d0fc38f21b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bd2904af-3341-4776-b27d-d5d0fc38f21b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=0ec7dd61-f838-4695-b508-0182a1f92b17 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.2GB: boot/grub/core.img
    .9GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: initrd.img
    .5GB: vmlinuz

---

### Post by codemaniac on 2010-02-28
> bios and cables are set to boot the w7 one first if that matters

How can the ubuntu grub be found by bios which is on the 2nd hard disk, when bios points to windows bootloader..

---

### Post by darkod on 2010-02-28
You see this:
nvidia_feefdaec1

and this:
/dev/mapper/nvidia_feefdaec1

Your win disk was member of raid array earlier and is carrying settings on it. Since 9.10 ubuntu can pick that up and ends up confused are you running raid or not.

Since it seems you are NOT running raid, execute:

sudo dmraid -E -r /dev/sda

Note: running that if you ARE running raid can destroy your array!

Then try again with

sudo update-grub

---

### Post by codemaniac on 2010-02-28
setting your second hard disk[where is UBUNTU] as first booting device may FIX this as your bios will now transfer the control to ubuntu's grub instead of windows..Boot into ubuntu then run 
"sudo update-grub" windows will be detected by the os_prober script.

---

### Post by darkod on 2010-02-28
> **Maintech said:**
> I am having the same issue. I have spent 6 hours trying to get Ubuntu 9.10 to dualboot with win7. It seems I have hosed my win7 now because grub won't recognize it and the win7 recovery disk tells me the mbr is an "unrecognizable filesystem". Nothing on the disk will repair it. So, it looks like I get to spend another several hours doing a reinstall of win7. I have tried several methods of getting Ubuntu to recognize win7 in grub and none have worked.  :mad:

I suggest you run the script too and open new thread with your results. Don't rush reinstalling win7, it might be repaired most often. Sometimes with ubuntu tools if windows tools fail. But you need to run the script and post the results.

---

### Post by darkod on 2010-02-28
> **codemaniac said:**
> How can the ubuntu grub be found by bios which is on the 2nd hard disk, when bios points to windows bootloader..

I didn't even go into this because the OP seems wrong about this. If this was correct he wouldn't be able to boot ubuntu, and he can. So it must be wrong.

This is not the issue right now. The raid meta data is.

---

### Post by timpletin on 2010-02-28
> **darkod said:**
> You see this:
nvidia_feefdaec1

and this:
/dev/mapper/nvidia_feefdaec1

Your win disk was member of raid array earlier and is carrying settings on it. Since 9.10 ubuntu can pick that up and ends up confused are you running raid or not.

Since it seems you are NOT running raid, execute:

sudo dmraid -E -r /dev/sda

Note: running that if you ARE running raid can destroy your array!

Then try again with

sudo update-grub

the previous owner must have had a raid setup :P
well update-grub located the win7 install! :D restarting now to see if it worked

edit!
it worked! thanks so much for the help <3

> **codemaniac said:**
> How can the ubuntu grub be found by bios which is on the 2nd hard disk, when bios points to windows bootloader..
I put grub on the windows disk

---

