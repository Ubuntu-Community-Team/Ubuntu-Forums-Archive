---
title: "Clean install fails to reboot"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by KLStringer on 2010-05-18
I'm installing  10.4 x64 on a Dell PowerEdge R610 in a RAID 1 configuration and the install goes fine until  I have to reboot the server to finish the install. On reboot after about a minute it gives  the error

 ```
    
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline/
     -check rootdelay= (did the system wait long enough?)
     -check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mysql1-root does not exist. Dropping to shell! 
```And then it drops to a (initramfs) at which point I have no idea  what to do and my co-worker who knows a little more about Linux can't  get it to let him check any of the above common problems. From the (initramfs) I can cd to /dev/mapper/ and mysql1-root does exist  why it can't be found during boot I have no idea or any idea how to  make it find it.

We've tried letting GRUB manually configure itself at the end of the  install before we reboot and we've also pointed it to /dev/sba partition  which is what should be the boot partition.
  
In the code tag it's ALERT! /dev/mapper/mysql(one)-root....  the L  and 1 look the same.

I've got 3 of these server to get setup and running as part of our back end and network restructuring and have been stuck at this point on the first one since Friday.

:confused:

---

### Post by KLStringer on 2010-05-18
After reading page after page of these forums I tried the holding down shift while booting to configure GRUB and I can get to the GRUB menu but have no idea what to do from there. The menu gives me 3 options:

```
Ubuntu, with Linux 2.6.32-21-server
Ubuntu, with Linux 2.6.32-21-server (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
```Trying the first option gives me the same results as just rebooting in the OP.
Trying the second option the same gave up error happens then there's a bunch of screen spam and I'm back to the same (initramfs) prompt.

Any help getting this sorted is greatly appreciated, I've been trying to learn Linux over the last year and still know next to nothing about how to do things like troubleshoot problems with it.

---

### Post by KLStringer on 2010-05-18
Pressing e while the first option is highlighted gives me the following:

```
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9\a54
linux /boot/vmlinux-2.6.32.31-server root=UUID=77e9b156-7d83-476a-b930-4475f04a9\a54 ro     quite    
initrd /boot/initrd.img-2.6.32.21-server
```
If I go to a cmd line I get a grub> prompt, doing ls shows (hd0) (hd0,5) (hd0,1)

---

### Post by KLStringer on 2010-05-18
Ok following suggestions I've read in another thread I've made a Live CD and booted in it and ran the boot info script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)


And the results are:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 72.7 GB, 72746008576 bytes
255 heads, 63 sectors/track, 8844 cylinders, total 142082048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   136,198,143   136,196,096  83 Linux
/dev/sda2         136,200,190   142,079,999     5,879,810   5 Extended
/dev/sda5         136,200,192   142,079,999     5,879,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        77e9b156-7d83-476a-b930-4475f04a9a54   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b048d478-e6ea-4bb6-9642-d7cd4f9beb35   swap                                     
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
search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
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
search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=77e9b156-7d83-476a-b930-4475f04a9a54 ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
    echo    'Loading Linux 2.6.32-21-server ...'
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=77e9b156-7d83-476a-b930-4475f04a9a54 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9a54
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=77e9b156-7d83-476a-b930-4475f04a9a54 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b048d478-e6ea-4bb6-9642-d7cd4f9beb35 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
   2.5GB: boot/grub/grub.cfg
  64.5GB: boot/initrd.img-2.6.32-21-server
    .2GB: boot/vmlinuz-2.6.32-21-server
  64.5GB: initrd.img
    .2GB: vmlinuz

```I kinda understand everything up to the "mount | grep ^/dev  output:" part after that its all gibberish to me.

---

### Post by KLStringer on 2010-05-19
Morning Ubuntu land hopefully today will bring more insight to my on going issue, but for now its time for coffee.

---

### Post by KLStringer on 2010-05-19
Well I tried changing the set root entry to '(/dev/sda1)' instead of '(hd0,1)' and still got the same error.

Seams like a pretty basic function for an OS to be able to do 'out of the box' and yet it doesn't work, I'm going to have to look into using a different OS soon because I don't have time to read page after page of various forums trying to get basic functionality working.

---

### Post by KLStringer on 2010-05-19
Used the server disk to boot into recovery mode and reinstalled GRUB to /dev/sda rebooting now to see if anything works

---

### Post by KLStringer on 2010-05-20
Installing GRUB to /dev/sda/ didn't help still getting the same error message. ](*,)

I could really use some insight into what could be causing this and how to fix it. Thanks in advance for any suggestions.

---

### Post by darkod on 2010-05-20
I haven't worked with the server version unfortunately, so I might totally miss the point, but...

Why does the script report only one disk, /dev/sda? And why is the partition reported as Linux instead of RAID member?

You mentioned in the first post it's RAID1. Hardware controller? Willing to try ubuntu's software raid function?

During the install, was the raid detected at all and were you asked whether you want to use it?

---

### Post by KLStringer on 2010-05-20
[FONT=Verdana]It's a   [/FONT][COLOR=#003366][FONT=&quot][FONT=Arial][FONT=Verdana]SAS 6/iR Integrated hardware RAID controller, during the install it was detected as  "Dell Virtual Disk" which is the name of the array and afaik should only be seen by the OS as a single "disk" with the controller managing the 2 separate HDD's.

[http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555](http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555)[/FONT]
[/FONT]   

[/FONT][/COLOR]

---

### Post by darkod on 2010-05-20
Yes, that's logical for proper hardware raid. But I was still under the impression the partitions would be marked as RAID members. Maybe it only does it for the software raid on the other hand.

One idea: have you tried with small 200MB partition outside the array for separate /boot? I know it sucks not having the /boot raided and protected too, but since it seems there isn't much progress with the issue, you might check how it acts with /boot outside the array.

The controller software should allow you to leave space outside the array I guess.

---

### Post by darkod on 2010-05-20
I know, this is for installing desktop version on fakeraid, but it might give you some idea:
[https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.10%20%28%20Karmic%20Koala%29](https://help.ubuntu.com/community/FakeRaidHowto#Ubuntu%209.10%20%28%20Karmic%20Koala%29)

There are instructions how to add grub later, etc... It might simply point to wrong partition.

---

### Post by KLStringer on 2010-05-20
The controller only allows the full disk to be used, I had to destroy the array and install that I had to find out but its no biggie. I've read the fakeRAID page but don't really see anything that would help, but of course I could be missing something obvious because of my newb glasses. I have tried pointing root= to all the different partitions and I still get the same ALERT! error.

---

### Post by KLStringer on 2010-05-21
I found this [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/29858](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/29858) bug report but I don't know how to change the kernel to see if it will work for me.

---

### Post by KLStringer on 2010-05-21
I tried 10.4 alt last night with no luck since I can't make any headway in getting 10.4 to work I decided to start over and see if 9.10 works. I will post back once install finishes.

---

### Post by KLStringer on 2010-05-21
I was able to install 9.10 but on reboot it doesn't even see a HDD the only options to boot are from the CDROM drive or over NIC. Going to reinstall and see if its because I used LVM,  it looks like there's a bug in booting from a LVM boot partition.

---

### Post by darkod on 2010-05-21
> **KLStringer said:**
> I was able to install 9.10 but on reboot it doesn't even see a HDD the only options to boot are from the CDROM drive or over NIC. Going to reinstall and see if its because I used LVM,  it looks like there's a bug in booting from a LVM boot partition.

Not sure if it's a bug, as far as I know for LVM you need separate /boot partition outside the LVM. I was interested in installing LVM and read few articles, they all said to create small /boot partition which should be left outside the LVM.

---

### Post by KLStringer on 2010-05-21
9.10 doesn't see the HDD after install regardless of whether its LVM or not. The bug report that I linked above talks about not being able top boot from a LVM partition, seams to be an on going issue for the last 4 years or so.

EDIT: I changed the array boot option in the RAID controllers set up, there's 4 options BIOS, OS, BIOS & OS, or disabled. OS doesn't see the drive, BIOS & OS gives the same ALERT! error. Going to try just BIOS now to see if anything changes.

---

### Post by KLStringer on 2010-05-21
With boot support in the controller set to BIOS it boots to the GRUB menu, after selecting the install I get the same ALERT! error. I guess I could try and DL 8.04 to see if it has the old GRUB, and see if thats the problem. From what I've read it seams like GRUB2 is shaky at best the 9.10 I DL'd has GRUB 1.97beta4

Set it to disabled and the HDD isn't detected tries to boot from NIC.

---

### Post by darkod on 2010-05-21
> **KLStringer said:**
> With boot support in the controller set to BIOS it boots to the GRUB menu, after selecting the install I get the same ALERT! error. I guess I could try and DL 8.04 to see if it has the old GRUB, and see if thats the problem. From what I've read it seams like GRUB2 is shaky at best the 9.10 I DL'd has GRUB 1.97beta4

Now that you have sorted out the BIOS options, you might give 9.10 alternate cd another go. Or even better, 10.04 alternate cd.

Not sure what's the pain here, but few months ago I did test raid install of 9.10 in virtual box, and grub2 worked just fine. Basically nothing special was needed, it installed fine.

However, I did use the alternate cd, software raid and can't remember if I created separate /boot partition outside the array, but I think it worked both ways, with or without separate /boot outside the array.

This is only an assumption, but could grub2 during the install be misled by the 'wrong' option in BIOS?

PS. You are using the server version right? Not desktop, so forget the remarks about the alternate cd. Give the 10.04 server cd another go. :)

---

### Post by KLStringer on 2010-05-24
Left Friday with 10.4 server installing and finished up a bit ago and the problem still persists even with boot support in the controller set to BIOS, though the error now reads ALERT! /dev/disk/by-uuid/7c94cee6-6d23-480a-89c2-3e61ed08e416 does not exist.  Dropping to a shell!

---

### Post by darkod on 2010-05-24
> **KLStringer said:**
> Left Friday with 10.4 server installing and finished up a bit ago and the problem still persists even with boot support in the controller set to BIOS, though the error now reads ALERT! /dev/disk/by-uuid/7c94cee6-6d23-480a-89c2-3e61ed08e416 does not exist.  Dropping to a shell!

Can you run the boot info script to show you the UUIDs and more info about the process?

I'm not 100% sure, but if you reinstalled this can happen because the formatted root has different UUID now, and grub2 on the MBR somehow keeps looking for the old UUID.

---

### Post by KLStringer on 2010-05-24
Ok will that that now

---

### Post by KLStringer on 2010-05-24
New boot info report

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 73.3 GB, 73282879488 bytes
255 heads, 63 sectors/track, 8909 cylinders, total 143130624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   137,205,759   137,203,712  83 Linux
/dev/sda2         137,207,806   143,128,575     5,920,770   5 Extended
/dev/sda5         137,207,808   143,128,575     5,920,768  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7c94cee6-6d23-480a-89c2-3e61ed08e416   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        b6184876-ce13-46a8-affd-3108f66dede3   swap                                     
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
search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
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
search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=7c94cee6-6d23-480a-89c2-3e61ed08e416 ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
    echo    'Loading Linux 2.6.32-21-server ...'
    linux    /boot/vmlinuz-2.6.32-21-server root=UUID=7c94cee6-6d23-480a-89c2-3e61ed08e416 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7c94cee6-6d23-480a-89c2-3e61ed08e416
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=7c94cee6-6d23-480a-89c2-3e61ed08e416 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b6184876-ce13-46a8-affd-3108f66dede3 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/core.img
  66.9GB: boot/grub/grub.cfg
  36.6GB: boot/initrd.img-2.6.32-21-server
    .2GB: boot/vmlinuz-2.6.32-21-server
  36.6GB: initrd.img
    .2GB: vmlinuz

```

---

### Post by darkod on 2010-05-24
This fix is for a desktop I guess, but it's worth a try:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

See if step 1 can help you boot into the server. After that whether step 4 can help you make the fix permanent.

You don't need steps 2 and 3, we can see from the script the UUID is correct.

---

### Post by KLStringer on 2010-05-24
Finally got a chance to try that and still gave the ALERT! /dev/disk/by-uuid/7c94cee6-6d23-480a-89c2-3e61ed08e416 does not  exist.  Dropping to a shell! error when I tried to boot.

---

### Post by KLStringer on 2010-05-25
](*,)

I'm all out of ideas

---

### Post by darkod on 2010-05-25
> **KLStringer said:**
> Finally got a chance to try that and still gave the ALERT! /dev/disk/by-uuid/7c94cee6-6d23-480a-89c2-3e61ed08e416 does not  exist.  Dropping to a shell! error when I tried to boot.

With a similar problem on a netbook, they changed in BIOS the SATA controller option from AHCI to compatible.
Makes any sense? :(

---

### Post by KLStringer on 2010-05-25
Makes sense but there's no option in the BIOS for AHCI the only option would be to reinstall with it set to off.

---

### Post by KLStringer on 2010-05-25
Any suggestions on an OS other than MS that RAID would work on? I need to move on and get these servers configured and deployed.

---

### Post by darkod on 2010-05-25
> **KLStringer said:**
> Any suggestions on an OS other than MS that RAID would work on? I need to move on and get these servers configured and deployed.

I think Fedora has a good track record, but I haven't touched it since Fedora Core 4 and that was while ago.

---

### Post by KLStringer on 2010-05-25
I've looked into Fedora but all I can find are desktop versions. I know there's a server version but where would I download it from?

---

### Post by darkod on 2010-05-25
Yeah, it seems they officially have only desktop versions although you can add what you like for a server.

Take a look how you like this too:
[http://www.centos.org/](http://www.centos.org/)

I haven't tried it but it seems popular for servers. And on one page it's mentioned it has 7yrs support!

---

### Post by KLStringer on 2010-05-25
Yeah thats what I saw after looking into Fedora, I think I'm going to pass this back up the hill and let the director make a decision on what to do. I now very little about Linux itself and nothing about the differences between this flavor, that flavor, or the other flavor.

---

### Post by ronparent on 2010-06-09
I haven't read this entire post but I'll get right to the crux. Have you tried 'sudo grub-install /dev/mapper/<YourRootRaidArray>'

This works like a charm for me with a raid0. There may be other factors - ie for me the raid array appears in bios as a boot choice.

---

### Post by KLStringer on 2010-06-09
The only thing that's in the /dev/mapper/  is a file named control

---

### Post by KLStringer on 2010-06-09
I used the LiveCD and mounted the boot partition /dev/sda1 to /mnt, when  I look in it for /dev/mapper there isn't a mapper folder at all. On 1  of the other 3 R610's that we have here (all configured with the exact  same hardware) that we put CentOS on to test it out which didn't have  any problems with installing or running there is a dev/mapper/ folder  with 3 files in it named control, VolGroup00-LogVol00, and  VolGroup00-LogVol01.

---

### Post by ronparent on 2010-06-09
Are you using software raid?

---

### Post by KLStringer on 2010-06-09
[FONT=Verdana]No it has a   [/FONT][COLOR=#003366][FONT=&quot][FONT=Arial][FONT=Verdana]SAS 6/iR  Integrated hardware RAID controller, during the install it was detected  as  "Dell Virtual Disk" which is the name of the array.

[http://www.dell.com/content/topics/t...us&l=en&cs=555]("http://www.dell.com/content/topics/topic.aspx/global/products/pvaul/topics/en/us/raid_controller?c=us&l=en&cs=555")

[http://www.dell.com/downloads/global/power/ps2q08-20080312-Dixit.pdf](http://www.dell.com/downloads/global/power/ps2q08-20080312-Dixit.pdf)
[/FONT] [/FONT]   [/FONT][/COLOR]

---

### Post by ronparent on 2010-06-09
This is a different matter altogether. You are actually dealing with a hardware raid as opposed to a hybrid MB based so called 'fakeraid'. In principle I'm sure you have to install the grub2 to the MBR of the root designation for your array (probably a symbolic link) as opposed to the drive designation (ie sda). Your documentation should tell you where this is located and how named. I regret that I don't know the specifics I would need to advise you.

Your most knowledgeable  advise should be obtainable from the Ubuntu servers forum (also under Main Support Categories). I would address your request with your raid hardware in the title. Good luck.

---

### Post by KLStringer on 2010-06-10
> In principle I'm sure you have to install the grub2 to the MBR of the  root designation for your array (probably a symbolic link) as opposed to  the drive designation (ie sda). Your documentation should tell you  where this is located and how named. I regret that I don't know the  specifics I would need to advise you

What information would you need? If I can provide it I surely will or conversely where would I find the information that I'd need to figure it out myself?

---

### Post by ronparent on 2010-06-10
For a fakeraid you would look for the raid symbolic link for the root in /dev/mapper/. The links I see in that location on your file system look unfamiliar to me. Your documentation should tell you what to look for. Or the question could be posed in the server forum for some expert advise.

---

### Post by KLStringer on 2010-06-10
I've posted regarding this issue in the server forum a few weeks ago, before I started this thread, but it didn't get much attention. This documentation that you keep referring to, is it the server hardware spec sheet, some log file for Ubuntu, or something else entirely? Your statements about it aren't all that clear. I've RTFM'ed and more forum threads/websites than I can remember backwards, forwards, sideways, and upside down. 

For all I don't know the answer could be staring me in the face but I wouldn't know because my knowledge of Ubuntu is limited at best. Anyway thanks for taking the time to try and help me out, its very much appreciated.

---

### Post by Brachus12 on 2010-06-11
This thread might help you:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000)

I am new to Ubuntu as well and the rootdelay command worked for me.

Brachus

---

### Post by KLStringer on 2010-06-11
Oh nice, I will try this later tonight when I'm back in the office.

---

### Post by KLStringer on 2010-06-11
Adding in the rootdelay=90 from that thread worked.=D>\\:D/:guitar: 

We're now up and running on one server and I'll be getting the other two going tonight. I guess we just never set the delay long enough for it to come up.

Thanks everyone for all the help, I couldn't have done it without it.

---

