---
title: "repairing mbr on raid array"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by cppgent0@gmail.com on 2010-11-27
I need help in repairing the MBR on my raid array. 

I have three disks, each with three paritions:
[LIST]
[*]root (sda1 sdb1 sdc1)  59GB
[*]swap (sda2 sdb2 sdc2)  1.12GB
[*]grub/boot (sda3 sdb3 sdc3) 298MB
[/LIST]

I have been able to get this running and it has been working fine for several months. A few days ago, I installed 10.04 to a USB stick but did not disable the hard drives at that point and so the MBR was overwritten. If I leave the USB stick in, it boots fine from that stick.

However now I can't get the boot from the raid array to work correctly.

I can do the following:
[LIST]
[*]Load 10.04 from the Live CD
[*]install mdadm
[*]recreate the root partition using

```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1
```
[*]I can mount and view the files on md0 with no problems. It's not corrupted in any way.
[/LIST]

When I installed, I followed the directions to make each of the grub drives bootable. However I don't know for sure whether grub was installed on each partition separately or if it was installed on the assembled partition only.

I have tried using 
```
sudo grub-install /dev/sda3
```
and got warnings, something to the effect
```

  Cannot find a device for /boot/grub
  no path or device specified
  Auto-detection of a filesystem module failed
  Please specify the module with option '--module' explicitly

```

I have also been able to get to the grub rescue prompt but my keyboard (wireless USB) is not recognized and so I can't type anything in at that point.

TIA,
John

---

### Post by oldfred on 2010-11-27
I so not know RAID. But you do not install grub2 to a partition like /dev/sda3, you want to install to the MBR or sda without a number. What I do not know is whether the MBR is mounted like normal /dev/sda or as part of the RAID /mdadm....? and you install it that way. Someone else may know exact command.

Grub normally defaults to sda when you install to a device. If you use manual install you get a choice on where to install and then you can be sure not to overwrite your existing boot loader in sda.

Run this to see where things are, but I do not know how well it parses RAID setups.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

Edit
See post #18
[http://ubuntuforums.org/showthread.php?t=1469169](http://ubuntuforums.org/showthread.php?t=1469169)

---

### Post by mitchd123 on 2010-11-27
I'm not sure,  but what I would attempt would be to boot to the USB stick and manually mount the arrays.   I would switch to the root directory where the arrays were mounted,  and then use the chroot command.   After chroot, then try updating grub?  "update-grub"

---

### Post by cppgent0@gmail.com on 2010-11-27
oldfred, I had seen See post #18 [http://ubuntuforums.org/showthread.php?t=1469169](http://ubuntuforums.org/showthread.php?t=1469169) in my google travels before but didn't think it applied.

mitchd123, the chroot idea is in the thread above.

In any case, here's what I have tried:
```

 [boot from live CD]
 sudo apt-get update
 sudo apt-get install mdadm
 sudo mdadm --auto-detect
 cd /dev
 [checked the /devmd0, md1 and md2 exist]
 cd /media
 [there is a directory "d4..5". This is md0 and has all of my files on it]
 sudo mount --bind /dev  /media/d4.../dev
 sudo mount --bind /proc /media/d4.../proc
 sudo mount --bind /sys  /media/d4.../sys
 sudo chroot /media/d4...
 cd dev
 [checked sda, sdb and sdc are there]
 update-grub
 cat /boot/grub/grub.cfg
 [checked there is 'insmod raid' and 'insmod mdraid']
 [one odd thing  here is 'insmod ext2' instead of 'insmod ext4']
 grub-install /dev/sda
 grub-install /dev/sdb
 grub-install /dev/sdc
 [all three reported success]
 exit   
 [checked chroot session exited correctly]
 sudo umount /media/d4.../sys
 sudo umount /media/d4.../proc
 sudo umount /media/d4.../dev
 [remove the live CD]
 [reboot machine]

```

It came up, there was a quick flash of "error..." something or other, and then the grub prompt came up:
```

 Gnu Grub version 1.98-1 ubuntu-7
 grub>

```

So closer but not quite there. I thought the latest version of grub is grub2.

I'm working on getting the output from bootinfoscript...

John

---

### Post by cppgent0@gmail.com on 2010-11-27
Here's the output from the script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks for (md0)/boot/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

md2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

md1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1           2,955,960   125,033,894   122,077,935  fd Linux raid autodetect
/dev/sda2             610,470     2,955,959     2,345,490  fd Linux raid autodetect
/dev/sda3    *             63       610,469       610,407  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1           2,955,960   125,033,894   122,077,935  fd Linux raid autodetect
/dev/sdb2             610,470     2,955,959     2,345,490  fd Linux raid autodetect
/dev/sdb3    *             63       610,469       610,407  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1           2,955,960   125,033,894   122,077,935  fd Linux raid autodetect
/dev/sdc2             610,470     2,955,959     2,345,490  fd Linux raid autodetect
/dev/sdc3    *             63       610,469       610,407  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/md0         d424de6e-25f9-4606-88f5-15ca877696c0   ext4                                     
/dev/md2         7cf1262b-bdb9-485d-a379-d49b6361437d   ext4                                     
/dev/sda1        ab3b8a06-9ddd-652e-a700-5c5acbe67133   linux_raid_member                               
/dev/sda2        efb3b8f4-9415-c318-ab04-5a74911f575e   linux_raid_member                               
/dev/sda3        5b857bf2-837b-9148-d1b2-0f284c445967   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ab3b8a06-9ddd-652e-a700-5c5acbe67133   linux_raid_member                               
/dev/sdb2        efb3b8f4-9415-c318-ab04-5a74911f575e   linux_raid_member                               
/dev/sdb3        5b857bf2-837b-9148-d1b2-0f284c445967   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        ab3b8a06-9ddd-652e-a700-5c5acbe67133   linux_raid_member                               
/dev/sdc2        efb3b8f4-9415-c318-ab04-5a74911f575e   linux_raid_member                               
/dev/sdc3        5b857bf2-837b-9148-d1b2-0f284c445967   linux_raid_member                               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== md0/boot/grub/grub.cfg: ===========================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set d424de6e-25f9-4606-88f5-15ca877696c0
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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set d424de6e-25f9-4606-88f5-15ca877696c0
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

================================ md0/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=d424de6e-25f9-4606-88f5-15ca877696c0 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md2 during installation
UUID=7cf1262b-bdb9-485d-a379-d49b6361437d /boot           ext4    defaults        0       2
# swap was on /dev/md1 during installation
UUID=adb7abd6-2b35-497c-84dc-7689de5fb166 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

==================== md0: Location of files loaded by Grub: ====================


 137.5GB: boot/grub/core.img
 137.5GB: boot/grub/grub.cfg

============================== md2/grub/grub.cfg: ==============================

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
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set d424de6e-25f9-4606-88f5-15ca877696c0
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
insmod raid
insmod mdraid
insmod ext2
set root='(md2)'
search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    linux    /vmlinuz-2.6.32-25-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro   quiet splash
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /vmlinuz-2.6.32-25-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    linux    /vmlinuz-2.6.32-24-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro   quiet splash
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /vmlinuz-2.6.32-24-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    linux    /vmlinuz-2.6.32-21-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=d424de6e-25f9-4606-88f5-15ca877696c0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md2)'
    search --no-floppy --fs-uuid --set 7cf1262b-bdb9-485d-a379-d49b6361437d
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

==================== md2: Location of files loaded by Grub: ====================


    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .1GB: initrd.img-2.6.32-21-generic
    .2GB: initrd.img-2.6.32-24-generic
    .3GB: initrd.img-2.6.32-25-generic
    .1GB: vmlinuz-2.6.32-21-generic
    .1GB: vmlinuz-2.6.32-24-generic
    .1GB: vmlinuz-2.6.32-25-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc2

00000000  65 78 70 69 72 65 64 2c  20 6f 72 20 74 68 65 20  |expired, or the |
00000010  6e 65 74 77 6f 72 6b 20  63 6f 6e 6e 65 63 74 69  |network connecti|
00000020  6f 6e 20 77 61 73 20 62  72 6f 6b 65 6e 2e 00 00  |on was broken...|
00000030  00 00 00 00 00 00 00 00  90 01 00 00 78 00 00 00  |............x...|
00000040  00 00 00 00 e8 20 a6 21  50 00 00 00 a0 00 00 00  |..... .!P.......|
00000050  f7 ff ff 7f 04 00 00 00  ff ff ff ff ff ff ff ff  |................|
00000060  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000070  ff ff ff ff 41 00 00 00  28 b4 27 00 f8 32 a6 21  |....A...(.'..2.!|
00000080  90 21 a6 21 d7 00 00 00  df 00 00 00 f7 ff ff 7f  |.!.!............|
00000090  04 00 00 00 6c 00 00 00  00 00 00 00 00 00 00 00  |....l...........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 01 00 00 00  |................|
000000b0  38 02 00 00 30 00 00 00  b0 84 a7 21 b8 20 a6 21  |8...0......!. .!|
000000c0  c0 20 a6 21 c0 20 a6 21  ff ff ff ff 10 00 00 00  |. .!. .!........|
000000d0  60 a7 a5 21 00 00 00 00  8c f0 ce 00 00 00 00 00  |`..!............|
000000e0  f8 08 00 00 c8 01 00 00  d2 00 00 00 44 69 64 20  |............Did |
000000f0  6e 6f 74 20 72 65 63 65  69 76 65 20 61 20 72 65  |not receive a re|
00000100  70 6c 79 2e 20 50 6f 73  73 69 62 6c 65 20 63 61  |ply. Possible ca|
00000110  75 73 65 73 20 69 6e 63  6c 75 64 65 3a 20 74 68  |uses include: th|
00000120  65 20 72 65 6d 6f 74 65  20 61 70 70 6c 69 63 61  |e remote applica|
00000130  74 69 6f 6e 20 64 69 64  20 6e 6f 74 20 73 65 6e  |tion did not sen|
00000140  64 20 61 20 72 65 70 6c  79 2c 20 74 68 65 20 6d  |d a reply, the m|
00000150  65 73 73 61 67 65 20 62  75 73 20 73 65 63 75 72  |essage bus secur|
00000160  69 74 79 20 70 6f 6c 69  63 79 20 62 6c 6f 63 6b  |ity policy block|
00000170  65 64 20 74 68 65 20 72  65 70 6c 79 2c 20 74 68  |ed the reply, th|
00000180  65 20 72 65 70 6c 79 20  74 69 6d 65 6f 75 74 20  |e reply timeout |
00000190  65 78 70 69 72 65 64 2c  20 6f 72 20 74 68 65 20  |expired, or the |
000001a0  6e 65 74 77 6f 72 6b 20  63 6f 6e 6e 65 63 74 69  |network connecti|
000001b0  6f 6e 20 77 61 73 20 62  72 6f 6b 65 6e 2e 00 00  |on was broken...|
000001c0  00 00 00 00 00 2f 63 68  61 72 2f 37 3a 31 33 33  |...../char/7:133|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  04 01 73 00 22 00 00 00  6f 72 67 2e 66 72 65 65  |..s."...org.free|
000001f0  64 65 73 6b 74 6f 70 2e  44 42 75 73 2e 45 72 72  |desktop.DBus.Err|
00000200

Unknown BootLoader  on md1

```

---

### Post by oldfred on 2010-11-28
You have or had a /boot partition which I do not recommend for desktops unless you have a old system with the 137GB boot limit. See next paragraph on one reason why not to have a /boot.

With a separate /boot you have to also mount that partition everytime you chroot or reinstall grub. Many instructions on the web do not mention that or just have a footnote that is easily missed.

It looks like you have added a grub.cfg to md0, but it is incomplete as the kernels are still in the /boot. You need to reinstall grub2 but make sure it also sees the /boot.

Generic instructions but I do not know how to adjust for md0 or md1 and/or sda.

to reinstall grub2 with the livecd:
$sudo mount /dev/sdXY /mnt
$sudo mount /dev/sdXZ /mnt/boot  ##only if you have a seperate /boot partition which could of course be on another drive as well
sudo grub-install --root-directory=/mnt/sdXY /dev/sda
$sudo grub-install --recheck --root-directory=/mnt /dev/sda

Edit
See also this thread on installing kpartx
[http://ubuntuforums.org/showthread.php?t=1631336](http://ubuntuforums.org/showthread.php?t=1631336)

---

### Post by cppgent0@gmail.com on 2010-11-30
I tried your instructions after I had chrooted and tried again after resetting up without chrooting. Both times grub came up but I just get the rescue prompt only. One change is there is now a /grub directory in the md0 partition, so one of these sequences created it.

Perhaps I misunderstood your instructions? Where exactly should I do them in the overall series of steps?

I looked into kpartx and tried a couple of invocations of it but it didn't seem to have an effect.

I have a general idea of how the whole boot sequence works, but there doesn't seem to be a site or doc for the exact steps that actually occur. My understanding is the MBR is a simple piece of code placed in sector 0 of the hard drive. When the machine comes up, the BIOS runs bit of code to get that sector's contents and then executes it. 

The MBR code turns around and reads more of the hard drive, in this case the rest of grub, which should get the system ready for starting the kernel and then actually start the kernel which finishes the rest of the boot sequence.

It seems then that the basic problem here is not in installing grub since it is clearly coming up. The MBR then is set up correctly and it is able to find and start grub. So far so good.

However, for some reason it's not able to finish it's set up and then start the kernel. This implies to me the problem is one of :

[LIST]
[*] grub can't mount the raid partition md0 and so can't find the rest of the files it needs
[*] it can mount it, but it can't find how to start the kernel or can't find the kernel itself
[*] there something wrong in the cfg file and grub stops during parsing or during validation of the cfg file content
[/LIST]

Is there any way to narrow down which one of these it is? or to find out if it's another problem outside of this list?


Thanks for all your help btw!
John

---

### Post by oldfred on 2010-11-30
I still do not know RAID but found they fixed some RAID issues with grub 1.99 just released.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/681535](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/681535)

---

### Post by cppgent0@gmail.com on 2010-12-07
Sorry for the long delay in replying.

I have since tried a few things:

[INDENT]
[LIST]
[*] loading the Alternate Live CD, following the installation steps until the partioning step. Did the re-partioning which according to the prompts, wrote the partition information to disk. Pop the CD out and reboot. Still got the grub rescue prompt.

[*] loading the Alternate Live CD, click on the "re-install grub bootloader" option. Followed all the steps. Still got the grub rescue prompt.

[*] loading the Alternate Live CD, click on the "repair" option. Followed all the steps. Still got the grub rescue prompt.
[/LIST][/INDENT]

I even tried hooking up my old PS/2 keyboard and tried to get some useful information from the grub prompt. No joy there.

Anyway, thanks for everyone's help, but I've given up and just re-installed Ubuntu. So no solution to publish...

I guess the lesson learned is that grub works great but when there is a problem, it does not display enough error information and doesn't persist enough log information in a retrievable way to help diagnose what went wrong. To be fair, there is an error message that is flashed on the screen just before the grub rescue prompt, but it is overwritten by the text of the prompt itself and so was not visible to me.

One relatively simple solution would be to have a command GetLastError on the rescue prompt that returns an error code, a ram log, or something similar. Not sure if that already exists. I looked through the grub help when it was up but none of the commands looked like it would do this.


John

---

