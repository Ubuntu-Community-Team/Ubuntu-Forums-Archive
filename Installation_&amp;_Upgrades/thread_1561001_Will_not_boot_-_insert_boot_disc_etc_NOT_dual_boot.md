---
title: "Will not boot - insert boot disc etc NOT dual boot"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by cpcpcp on 2010-08-25
my Acer  netbook with 10.4 installed will now only book from USB distro  stick Sometimes Grub rescue pops up sometimes it asks for a bootable device to be inserted  and this is what happened  today. Despite my best efforts all my data  is still in place:D. When it first failed to boot I thought I knew the solution so  I installed 9.10 followed by  10.4 netbook version. I confused myself and the install by having a 4Gb SD  disk inserted which ended up having the re-installation on it - but saved my data!;)  
I have now taken out the SD disk and have in place just the built in 7Gb flash drive (and the distro USb stick).

When it failed today I went here
[https://help.ubuntu.com/community/Gr...0from%20LiveCD](https://help.ubuntu.com/community/Gr...0from%20LiveCD)
and headed to the section reinstalling GRUB 2
Having no idea why I was doing what I did entered 
Sudo fdsk -l
and saw the 7Gb flask drive of the netbook was /dev/sa1 and yes it was marked as Linux but there was the message that the Partition did not end on the cylinder boundary.
I did not understand the message  but ploughed on 

I  entered 
sudo blkid
and saw /dev/sda1 was type ext4
and that /dev/sda5 was type swap

Thinking I was winning I entered 
sudo mount /dev/sda1 /mnt
and then
sudo grub-install --root-directory=/mnt/sda

after a lot of pondering by the netbook  I had the response from the terminal 

/usr/sbin/grub-probe: error: cannot read from '/dev/sda'.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly

So
Does this mean anything to you brains?
How do I fix things to get my netbook up and running again with 10.04 netbook distro? 
Should I just give up and try to reinstall it all again (which would be annoying but not the end of the world)?
Luckily I have this other machine to post on.
Chris

---

### Post by lechien73 on 2010-08-25
Could you download and run the boot info script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Follow the instructions to generate the results.txt file, and then please post the file here. Either as an attachment, or copy and paste the contents, highlight the text and click the # button on the toolbar to surround it in [CODE] tags.

Perhaps Grub is only installed on your USB disk, but the boot info script results will help with diagnosis.

---

### Post by cpcpcp on 2010-08-25
Here are the results. 
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        1b6747b0-3fdd-4bf8-a61c-c84731eb3bba   ext4                                     
/dev/sda5        409bf295-8888-4a4d-b477-25f9643d800d   swap                                     
/dev/sdb1        0C7D-1D30                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
ls: reading directory /mnt/: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

```

---

### Post by lechien73 on 2010-08-25
Ok, so as suspected, Grub is only installed in the MBR of your USB stick. Try the following:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Assuming no errors are reported, then reboot.

I am concerned, though, that your partition table appears to be fouled up. The "Invalid MBR Signature" and I/O errors on /dev/sda would seem to indicate that there are disk problems. You may be better off repartitioning, reformatting and re-installing Ubuntu!

---

### Post by cpcpcp on 2010-08-25
> **lechien73 said:**
> Could you download and run the boot info script 
Perhaps Grub is only installed on your USB disk, but the boot info script results will help with diagnosis.

Back at my "real machine"

As you will have seen now it is not even seeing from the USB distro anything on the 7GB built in netbook drive. Annoying is the netbook itself broken I wonder?
The novel thing is I get different results on different days :(

Having just rebooted the netbook's  built in hard drive is shown under files and folders so  give me a few moments and I will download and re-run the programme and repost the results.:D

---

### Post by cpcpcp on 2010-08-25
> **lechien73 said:**
> Could you download and run the boot info script from: [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

.

A different result :(
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    14,983,167    14,981,120  83 Linux
/dev/sda2          14,985,214    15,759,359       774,146   5 Extended
/dev/sda5          14,985,216    15,759,359       774,144  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        1b6747b0-3fdd-4bf8-a61c-c84731eb3bba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        409bf295-8888-4a4d-b477-25f9643d800d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0C7D-1D30                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
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
search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1b6747b0-3fdd-4bf8-a61c-c84731eb3bba
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
UUID=1b6747b0-3fdd-4bf8-a61c-c84731eb3bba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=409bf295-8888-4a4d-b477-25f9643d800d none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/grub.cfg
   5.9GB: boot/initrd.img-2.6.32-21-generic
   6.0GB: boot/initrd.img-2.6.32-24-generic
   5.6GB: boot/vmlinuz-2.6.32-21-generic
   5.8GB: boot/vmlinuz-2.6.32-24-generic
   6.0GB: initrd.img
   5.9GB: initrd.img.old
   5.8GB: vmlinuz
   5.6GB: vmlinuz.old
```

---

### Post by techxcell on 2010-08-25
One thing I learned the hard way in Linux.. one typo can kill the system. I am pretty sure, a typo spoiled it for you too! For instance, you mounted /dev/sda1 to /mnt and then gave the root-directory as /mnt/sda !!! Now maybe the mistake was only in writing this post... no way to know now LOL!

I suggest you take a breather, then start a fresh install. Keep a note of your selections of disks and partitions on a piece of paper.

---

### Post by lechien73 on 2010-08-25
That looks a bit healthier :)

Interestingly it's showing Lilo as being installed to the MBR of the internal disk. Is this installation replacing the default Linpus installation that comes with the Acer netbook?

Anyway, now that you're seeing the disk properly - and it doesn't seem to be giving errors at the moment, you could try the Grub installation again:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

This will replace the current Lilo installation in the MBR, and should work for booting Ubuntu from now on. I still wouldn't stake my life on the quality of the internal disk though....

---

### Post by cpcpcp on 2010-08-25
> **techxcell said:**
> One thing I learned the hard way in Linux.. one typo can kill the system. I am pretty sure, a typo spoiled it for you too! For instance, you mounted /dev/sda1 to /mnt and then gave the root-directory as /mnt/sda !!! Now maybe the mistake was only in writing this post... no way to know now LOL!

I suggest you take a breather, then start a fresh install. Keep a note of your selections of disks and partitions on a piece of paper.

Breather taken!

I just follow instruction but looking at the adjoining post I have been told "/mnt/sda"
again rather than your suggestion of "mnt/sda1"

and as I have not clue what the instruction means anyway would one of you brainy types confirm or re-confirm which one I should use as I sit here with my netbook by my side  waiting to press the enter key

Chris

---

### Post by lechien73 on 2010-08-25
It's ok - he was referring to your typo in the first post. The commands I gave are the correct commands for installing Grub to the MBR of /dev/sda :)

---

### Post by techxcell on 2010-08-25
LOL! I didn't see @lechien73's post. We must have been typing at the same time. cpcpcp you should do what he says.

And I don't know why, but I suspect you are overlooking the **SPACE** there:

grub-install --root-directory=/mnt/         **[SPACE]** /dev/sda

---

### Post by cpcpcp on 2010-08-25
> **lechien73 said:**
> It's ok - he was referring to your typo in the first post. The commands I gave are the correct commands for installing Grub to the MBR of /dev/sda :)

I don't know about that but after a lot of pondering by the netbook the result was:-

/usr/bin/grub-editenv: error: cannot open the file /mnt//boot/grub/grubenv.new.
/usr/srbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1. Check your device map.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules'  explicitly.

Which seems much like the output I posted originally.

??

Chris

---

### Post by cpcpcp on 2010-08-25
> **techxcell said:**
> LOL! I didn't see @lechien73's post. We must have been typing at the same time. cpcpcp you should do what he says.

And I don't know why, but I suspect you are overlooking the **SPACE** there:

grub-install --root-directory=/mnt/         **[SPACE]** /dev/sda

I promise you the **space** was there both times.

What is the file it is saying it cannot open (grubenv.new)? It has to be important but what can I do about it?

---

### Post by dagdeniz on 2010-08-25
> **cpcpcp said:**
> I don't know about that but after a lot of pondering by the netbook the result was:-

/usr/bin/grub-editenv: error: cannot open the file /mnt//boot/grub/grubenv.new.
/usr/srbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1. Check your device map.


Look at the double slash there "/mnt//boot"
The error is, root directory is not "/mnt/", it is "/mnt"
Try 
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
or sometimes "/dev/hda"

---

### Post by lechien73 on 2010-08-25
**dagdeniz** is absolutely correct - I was just in the middle of typing the same reply. My bad - the trailing / is the problem!!

---

### Post by techxcell on 2010-08-25
details.. details.. missed yet another one! How could you lechien? *sob* I'm messed up for life now!

---

### Post by cpcpcp on 2010-08-25
> **lechien73 said:**
> **dagdeniz** is absolutely correct - I was just in the middle of typing the same reply. My bad - the trailing / is the problem!!

Progress guys - and thanks.

The messages this time are

mount: /dev/sdal already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt

which I think is good (?)

but then 

rm: cannot remove '/mnt/boot/grub/915resolution.mod':Read-only file system

Once you, hopefully, confirm this is just an advisory I will restart the netbook

Exciting isn't it - but passed my bedtime

Chris

---

### Post by lechien73 on 2010-08-25
It's getting close to my bedtime too :) I've already messed up techxcell for life, I don't want to have any more blood on my hands tonight!!!

Anyway, could you re-run the boot info script? If it now says that Grub is installed in the MBR of /dev/sda then all should be well.

---

### Post by dagdeniz on 2010-08-25
no, I think. clearly a problem of permissions, it tells you that you don't have write permissions on /mnt. did you use sudo?

---

### Post by cpcpcp on 2010-08-25
> **lechien73 said:**
> It's getting close to my bedtime too :) I've already messed up techxcell for life, I don't want to have any more blood on my hands tonight!!!

Anyway, could you re-run the boot info script? If it now says that Grub is installed in the MBR of /dev/sda then all should be well.

Toothache so cannot sleep :(

here is the result. restart or not?
```
                  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda5        409bf295-8888-4a4d-b477-25f9643d800d   swap                                     
/dev/sdb1        0C7D-1D30                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================


=================== sda1: Location of files loaded by Grub: ===================


   5.0GB: boot/grub/grub.cfg
   5.9GB: boot/initrd.img-2.6.32-21-generic
   5.9GB: initrd.img.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: Input/output error
cat: /mnt/boot/grub/grub.cfg: Input/output error
hexdump: /mnt/initrd.img.old: Input/output error
hexdump: /mnt/initrd.img.old: Input/output error
hexdump: /mnt/initrd.img.old: Input/output error
hexdump: /dev/sda2: Input/output error
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

---

### Post by dagdeniz on 2010-08-25
As it says in the bootinfo summary,
```
No known boot loader is installed in the MBR of /dev/sda
```
that's Grub2 is not installed. 

You should recheck what you've done and retry, and find out the reason of the previous write-permissions error (asking again: missing sudo?)
Otherwise, you may try to chroot (=install grub2 from inside of the system) (omit the first step if it's already mounted):
```
$ sudo mount /dev/sda1 /mnt
$ sudo mount -o bind /dev /mnt/dev
$ sudo mount -o bind /sys /mnt/sys
$ sudo mount -t proc proc /mnt/proc
$ sudo chroot /mnt
$ sudo grub-install /dev/sda
$ exit

```
If everything goes right, unmount them all 

```
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt
```

or install grub from the grub shell, which is a bit easier (may need a "sudo apt-get install grub2" if it says command not found). 
Write "grub" in a terminal and press enter, and follow the manual instructions writtern here: 
[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_3.html#SEC9](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_3.html#SEC9)

---

### Post by lechien73 on 2010-08-26
> **cpcpcp said:**
> Toothache so cannot sleep :(


Sorry, I had to go to bed - otherwise my wife would have been citing Ubuntu in divorce papers!! Hope the tooth is a bit better this morning.

Anyway, the new results.txt file you posted has the same problem as the first. The partition table is not being properly recognised, and the drive appears messed up. Although it seems that the disk will work properly sometimes (reference the second results.txt file you posted), it's quite unstable.

At this stage, I would recommend a complete re-partition, re-format and re-install. If the errors persist, then I think the SD disk is faulty.

---

### Post by cpcpcp on 2010-08-27
> **lechien73 said:**
> Sorry, I had to go to bed - otherwise my wife would have been citing Ubuntu in divorce papers!! Hope the tooth is a bit better this morning.

At this stage, I would recommend a complete re-partition, re-format and re-install. If the errors persist, then I think the SD disk is faulty.

In order

Dagdeniz
I ventured the path you set out for me and after sudo mount -o bind /dev /mnt 
and I  gave up after getting the message back /dev: can't read superblock
That answer may or may not have been something trivial but as I have no idea what these commands mean and I am blindly following your kind instructions I simply gave up.

Still taking the pills for the tooth problem.

Looking this morning in Files and Folders the built in 8Gb disk of the netbook was no longer shown so either what I have been doing upset things or, as is suggested, the netbook's disk is faulty.
I shut down and restarted the machine booting from the USB stick  and the volume of  the  netbook's built in drive was still not shown.

I tried the install option showing in favourites
Trying to install from the USB no partitions are shown
I conclude that the netbook's solid state drive  has failed:(

I have neither the time not patience to try to put a new one in - even if it is possible - so it will go on ebay for parts or what have you. I will try to get another one on ebay (and put this failure down to my being just unlucky with my machine) as once having had such a neat small device I will miss it.

I will be back in while to mark the thread Solved 

:( **UBUNTU OK  -  ACER NETBOOK SOLID STATE DISK DRIVE DEFECTIVE** :( 

THANK YOU ALL EVER SO MUCH FOR YOU PATIENT HELP.

Chris

---

