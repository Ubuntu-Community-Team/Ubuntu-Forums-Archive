---
title: "recover partitions?"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by lanzcc on 2010-08-15
Greets,
 
Does anyone out there know how to recover partitions? In installing 9.10 I checked the box that said "install side-by-side" but now I can't access the old OS. Using "mount" & "fdisk" have shown that the partitions are still there.
 
A complication is: there are two hard drives, and we know there's a raid involved because one of the displays says "Linux raid autodetect" on old partitions. How do you find out which raid protocol was used, and then how do you ask for access to the old partitions? And do I want to use the palindrome mdadm?
 
THANKS

---

### Post by MAFoElffen on 2010-08-15
Well... I see this unanswered so far.  Before you start doing things that are going to overwrite what's there currently... Let's take a look at what you have.  What was the "other" OS that won't start up now?

---

### Post by Rubi1200 on 2010-08-15
Do you have an Ubuntu CD?

If yes, boot the computer and choose to try not install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here.

This will give us a clearer picture of your setup and make offering solutions a lot easier.

Thanks.

:)

---

### Post by lanzcc on 2010-08-17
Hello again,

here are the results of boot_info_script

THANKS



```

```                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #11 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub/stage2 and /grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4c339c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       996,029       995,967  fd Linux raid autodetect
/dev/sda4             996,030   976,768,064   975,772,035   5 Extended
/dev/sda5             996,093    10,779,614     9,783,522  fd Linux raid autodetect
/dev/sda6          10,779,678    49,865,759    39,086,082  fd Linux raid autodetect
/dev/sda7          49,865,823    59,649,344     9,783,522  fd Linux raid autodetect
/dev/sda8          59,649,408    69,432,929     9,783,522  fd Linux raid autodetect
/dev/sda9          69,432,993    78,541,784     9,108,792  82 Linux swap / Solaris
/dev/sda10         92,887,893   976,768,064   883,880,172  fd Linux raid autodetect
/dev/sda11         78,541,848    92,164,904    13,623,057  83 Linux
/dev/sda12         92,164,968    92,887,829       722,862  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18a34c38

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       996,029       995,967  fd Linux raid autodetect
/dev/sdb4             996,030   976,768,064   975,772,035   5 Extended
/dev/sdb5             996,093    10,779,614     9,783,522  fd Linux raid autodetect
/dev/sdb6          10,779,678    49,865,759    39,086,082  fd Linux raid autodetect
/dev/sdb7          49,865,823    59,649,344     9,783,522  fd Linux raid autodetect
/dev/sdb8          59,649,408    69,432,929     9,783,522  fd Linux raid autodetect
/dev/sdb9          69,432,993    78,541,053     9,108,061  82 Linux swap / Solaris
/dev/sdb10         92,887,893   976,768,064   883,880,172  fd Linux raid autodetect
/dev/sdb11         78,542,848    92,166,143    13,623,296  83 Linux
/dev/sdb12         92,168,192    92,887,039       718,848  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       68e72387-438c-49f4-41de-df0008d68651   linux_raid_member                               
/dev/sda11       bfc2125c-0742-4e7e-b70e-b46d5d387653   ext4                                     
/dev/sda12       acae8bae-3666-42ee-9ec7-7d6e94f64290   swap                                     
/dev/sda1        ec69d9a4-0586-318b-4c3d-6cc0d02a2e33   linux_raid_member                               
/dev/sda5        ab05eb26-d512-b056-6438-696aa857a347   linux_raid_member                               
/dev/sda6        194d37c0-d072-eb34-4ca5-7fe9b269e413   linux_raid_member                               
/dev/sda7        c511370a-fa1d-c998-f127-edb1df6c7252   linux_raid_member                               
/dev/sda8        15d71d59-ac78-7579-84dc-f2beab63e6d8   linux_raid_member                               
/dev/sda9        8c7779d6-ea63-4611-943e-cffa86f357da   swap                                     
/dev/sdb10       68e72387-438c-49f4-41de-df0008d68651   linux_raid_member                               
/dev/sdb11       d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca   ext4                                     
/dev/sdb12       58dd760f-fbce-47f2-9034-1baf93981298   swap                                     
/dev/sdb1        ec69d9a4-0586-318b-4c3d-6cc0d02a2e33   linux_raid_member                               
/dev/sdb5        ab05eb26-d512-b056-6438-696aa857a347   linux_raid_member                               
/dev/sdb6        194d37c0-d072-eb34-4ca5-7fe9b269e413   linux_raid_member                               
/dev/sdb7        c511370a-fa1d-c998-f127-edb1df6c7252   linux_raid_member                               
/dev/sdb8        15d71d59-ac78-7579-84dc-f2beab63e6d8   linux_raid_member                               
/dev/sdb9        641b05d1-0b87-4e48-9c8a-2ab337aa3709   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


========================== sda11/boot/grub/grub.cfg: ==========================

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
set root=(hd0,11)
search --no-floppy --fs-uuid --set bfc2125c-0742-4e7e-b70e-b46d5d387653
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
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set bfc2125c-0742-4e7e-b70e-b46d5d387653
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bfc2125c-0742-4e7e-b70e-b46d5d387653 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set bfc2125c-0742-4e7e-b70e-b46d5d387653
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=bfc2125c-0742-4e7e-b70e-b46d5d387653 ro single 
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
menuentry "'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sdb11)" {
    insmod ext2
    set root=(hd1,11)
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=bfc2125c-0742-4e7e-b70e-b46d5d387653 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=acae8bae-3666-42ee-9ec7-7d6e94f64290 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda11: Location of files loaded by Grub: ===================


  42.9GB: boot/grub/core.img
  42.9GB: boot/grub/grub.cfg
  43.5GB: boot/initrd.img-2.6.31-14-generic
  42.7GB: boot/vmlinuz-2.6.31-14-generic
  43.5GB: initrd.img
  42.7GB: vmlinuz

========================== sdb11/boot/grub/grub.cfg: ==========================

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
set root='(hd1,11)'
search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
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
set root='(hd1,11)'
search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,11)'
    search --no-floppy --fs-uuid --set d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca
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

=============================== sdb11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb11 during installation
UUID=d0d984d0-67eb-4bd6-9c13-ee08c1e6dbca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb12 during installation
UUID=58dd760f-fbce-47f2-9034-1baf93981298 none            swap    sw              0       0

=================== sdb11: Location of files loaded by Grub: ===================


  42.6GB: boot/grub/core.img
  42.6GB: boot/grub/grub.cfg
  42.6GB: boot/initrd.img-2.6.32-21-generic
  42.6GB: boot/vmlinuz-2.6.32-21-generic
  42.6GB: initrd.img
  42.6GB: vmlinuz

---

### Post by presence1960 on 2010-08-17
To get rid of the raid arrays try this:

There is a bug in 9.10 that mounts raid arrays that you have deleted. To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type dmraid -E -r /dev/name_of_your_disk.  Note you want the disk name not the partition name.  You can see your disk names in gparted.  Mine was sda and sdb and my partition names were sda1 and sda5 and sdb1.  I had to do both sda and sdb.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Once you have verified the raid disk is gone reboot and your OS should boot.

Then I would reboot & go into BIOS and set sdb as first in the hard disk boot order. Save changes to CMOS & boot the 10.04 Live CD. Boot to the desktop, open a terminal and run ```
sudo mount /dev/sdb11 /mnt
```This will mount your 10.04 / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of sdb. Reboot without the Live CD and boot into 10.04. Open a terminal and run ```
sudo update-grub
```

Next open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```

When you get to the screen which allows you to choose which disk to keep grub on use the space bar to unselect sda and then use the space bar to select sdb. This will insure when GRUB 2 is updated that the updates go to the MBR of sdb.

---

### Post by lanzcc on 2010-08-21
OK, thanks for the excellent detailed advice, I'll try it ASAP.

Unfortunately, I can find no way to "turn off raid in my Bios". There is only one mention of "raid" in my BIOS and that's where I get options to enter "Legacy mode",  "Raid mode", or "disable", and disable is already selected by default.

I have looked around the forums, and read lots of posts on turning off raid, but none seem to apply to my system.

If I find good doc'n on my motherboard, is that likely to help?

THANKS

---

### Post by presence1960 on 2010-08-22
> **lanzcc said:**
> OK, thanks for the excellent detailed advice, I'll try it ASAP.

Unfortunately, I can find no way to "turn off raid in my Bios". There is only one mention of "raid" in my BIOS and that's where I get options to enter "Legacy mode",  "Raid mode", or "disable", and disable is already selected by default.

I have looked around the forums, and read lots of posts on turning off raid, but none seem to apply to my system.

If I find good doc'n on my motherboard, is that likely to help?

THANKS

if RAID is disabled in your BIOS then proceed with the instructions I posted.

dmraid -E -r /dev/name_of_your_disk = ```
dmraid -E -r /dev/sdX
```where X is the name of your disk a, b,c, etc

---

