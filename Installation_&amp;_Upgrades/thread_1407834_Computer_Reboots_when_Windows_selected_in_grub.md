---
title: "Computer Reboots when Windows selected in grub"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by jscarnahan on 2010-02-15
Just installed Ubuntu 9.10 and had windows 7 ultimate installed prior to installing Ubuntu. When I installed Ubuntu I partitioned off a section of the HDD that windows is installed on and installed to that new partition. Ubuntu boots and works great but ever since installed if I select windows to boot it just reboot PC all together. Tried making windows default and it booted windows once then went back to normal. I tried to follow suggestions on different post about running "sudo grub" but it is not a command according to my terminal. 
Please Help.

---

### Post by zvacet on 2010-02-16
```
sudo update-grub
```

---

### Post by Mark Phelps on 2010-02-16
How did you "partition off" the drive? Did you do it the right way, using the Win7 Disk Management tool to shrink the Win7 OS partition? Or did you use the Ubuntu installer to resize?

If you were able to boot into Win7 before, and you used the first resizing method, it's likely you corrupted your Win7 OS in the process of resizing it.

Did you go to the trouble to create and burn a Win7 Repair CD before you did this?

If not, do you have a Win7 DVD?

Asking because you will need one of these to boot into and run Startup Repair three times to repair your Win7 boot.

---

### Post by kansasnoob on 2010-02-16
Really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jscarnahan on 2010-02-16
> **Mark Phelps said:**
> How did you "partition off" the drive? Did you do it the right way, using the Win7 Disk Management tool to shrink the Win7 OS partition? Or did you use the Ubuntu installer to resize?

If you were able to boot into Win7 before, and you used the first resizing method, it's likely you corrupted your Win7 OS in the process of resizing it.

Did you go to the trouble to create and burn a Win7 Repair CD before you did this?

If not, do you have a Win7 DVD?

Asking because you will need one of these to boot into and run Startup Repair three times to repair your Win7 boot.

I used the Ubuntu software to partition off the HDD, however, I have booted into Windows twice when it actually worked. 

Yes I have my Windows DVD and have run the startup repair and it says there are no issues. Why would I have to run this three times. 

And to the other poster, I will do what you asked and post soon.

---

### Post by jscarnahan on 2010-02-16
> **zvacet said:**
> ```
sudo update-grub
```
 
 
This fixed it thanks, I had my syntax wrong. Kinda new to Ubuntu so sorry if this was an easy one.

---

### Post by Mark Phelps on 2010-02-16
> **jscarnahan said:**
>  ... Why would I have to run this three times...
Because, there are three kinds of repairs that might need to be made to restore Win7/Vista boot, and MS configured their repair utility to only repair one type at a time.

So generally, it takes three passes to make all the repairs.

---

### Post by jscarnahan on 2010-03-10
OK so 
"sudo update-grub"

Fixes Windows 7 boot for one and only one boot, then reverts back to not booting.
I ran boot info script and will post below......

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc9a7f38

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   403,295,759   403,295,697   7 HPFS/NTFS
/dev/sda2         403,295,760   488,392,064    85,096,305   5 Extended
/dev/sda5         403,295,823   484,809,569    81,513,747  83 Linux
/dev/sda6         484,809,633   488,392,064     3,582,432  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d550f69

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1EBC5A46BC5A191B                       ntfs                                     
/dev/sda5        534bcc52-3526-48a5-970d-f5da3b697026   ext4                                     
/dev/sda6        ddffb740-0c6c-4705-acd5-738296dcec91   swap                                     
/dev/sdb1        E000991A0098F92C                       ntfs       Local Disk 2                  

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/1EBC5A46BC5A191B  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="6"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 534bcc52-3526-48a5-970d-f5da3b697026
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
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 534bcc52-3526-48a5-970d-f5da3b697026
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=534bcc52-3526-48a5-970d-f5da3b697026 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 534bcc52-3526-48a5-970d-f5da3b697026
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=534bcc52-3526-48a5-970d-f5da3b697026 ro single  splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 534bcc52-3526-48a5-970d-f5da3b697026
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=534bcc52-3526-48a5-970d-f5da3b697026 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 534bcc52-3526-48a5-970d-f5da3b697026
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=534bcc52-3526-48a5-970d-f5da3b697026 ro single  splash
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 1ebc5a46bc5a191b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=534bcc52-3526-48a5-970d-f5da3b697026 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ddffb740-0c6c-4705-acd5-738296dcec91 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 210.1GB: boot/grub/core.img
 207.5GB: boot/grub/grub.cfg
 207.0GB: boot/initrd.img-2.6.31-14-generic
 207.3GB: boot/initrd.img-2.6.31-19-generic
 207.0GB: boot/vmlinuz-2.6.31-14-generic
 207.1GB: boot/vmlinuz-2.6.31-19-generic
 207.3GB: initrd.img
 207.0GB: initrd.img.old
 207.1GB: vmlinuz
 207.0GB: vmlinuz.old

---

