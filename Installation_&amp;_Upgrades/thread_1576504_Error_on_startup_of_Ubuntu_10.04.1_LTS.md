---
title: "Error on startup of Ubuntu 10.04.1 LTS"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by wojcianiu on 2010-09-17
[FONT=Times New Roman][SIZE=3]Hello,
I've got a problem while startup of Ubuntu 10.04.1 LTS.[/SIZE][/FONT] [SIZE=3][FONT=Times New Roman]I got an error:
error: out of disk.
grub rescue>
I always get this error, even after reinstall. I tried a lot of methods.
There's any errors if I'll install Windows (XP) and then install Ubuntu. But this method works only for 1 startup. What can I do?
If I made a mistake, I'm from Poland and I don't know English a lot:).
Thanks
PS I want add that I'm new to Ubuntu and I don't know lots of things (I know where's Terminal and how to run system from Live CD)
[/FONT][/SIZE]

---

### Post by drs305 on 2010-09-17
If it's a grub problem, we can probably find out what it is if you run the following script and post the results here. It gives us the information about where grub is installed and how it works with your system.

You can download it and run it from the LiveCD.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

When copying the RESULTS.txt here, please highlight the text and then press the **#** icon in the post's menubar. That will place the text inside "code" tags, which makes it easier to read.

---

### Post by wojcianiu on 2010-09-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   387,737,599   387,735,552  83 Linux
/dev/sda2         387,739,646   390,721,535     2,981,890   5 Extended
/dev/sda5         387,739,648   390,721,535     2,981,888  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        4566ea00-499d-431b-86f6-2bab5e610106   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e40d6a97-ce2e-4b0c-b51a-d341c322d09d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        60BF-1061                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/60BF-1061         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
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
search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
set locale_dir=($root)/boot/grub/locale
set lang=pl
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4566ea00-499d-431b-86f6-2bab5e610106 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-24-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
    echo    'Wczytywanie systemu Linux 2.6.32-24-generic...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4566ea00-499d-431b-86f6-2bab5e610106 ro single 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4566ea00-499d-431b-86f6-2bab5e610106
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  73.1GB: boot/grub/core.img
 180.6GB: boot/grub/grub.cfg
  73.2GB: boot/initrd.img-2.6.32-24-generic
  73.1GB: boot/vmlinuz-2.6.32-24-generic
  73.2GB: initrd.img
  73.1GB: vmlinuz
```

---

### Post by drs305 on 2010-09-17
wojcianiu,

I can't see anything obviously wrong with your installation. In cases like this, I've had success by having the user completely remove and reinstall Grub2. Using the simpler "grub-install" command won't replace missing files, while removing everything and reinstalling will. Aside from the time it takes to boot the LiveCD, the process takes only a few minutes.

So if you have a reliable Internet connection and power source, I'd recommend purging and reinstalling Grub2 via 'chroot'. I've written instructions in another post. Just follow them to reinstall grub-pc (Grub2) and grub-common. If you have any questions you can ask them here.

[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5]("http://ubuntuforums.org/showpost.php?p=9836539&postcount=5")

---

### Post by wojcianiu on 2010-09-17
I used the way with Internet connection. Everything was OK, Terminal downloaded some files, but problem still continues.
If this problem won't solve I think I'll come back to Windows.

---

### Post by drs305 on 2010-09-17
I'm sorry this didn't work. The only thing I can think of regarding boot is to check the BIOS setup to make sure it is booting to the Ubuntu drive first, rather than the one that has syslinux on it.
 
The "out of disk" problem is one of the hard ones to analyze as it can be caused by many different problems, but normally the complete removal and reinstall of Grub2 fixes things.

Maybe someone else will come along with a solution for you. I will continue to watch the thread and add anything I think might help.

---

### Post by wojcianiu on 2010-09-17
Maybe I'll buy new computer. It has been made in Devil's Day (06.06.06) and soon it's 10.10.10. Now I must use Vista on my laptop.

---

### Post by Rubi1200 on 2010-09-17
You might want to take a look here and see if there is something that helps:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

---

### Post by wojcianiu on 2010-09-17
**Rubi1200**,

It still doesn't work.

---

### Post by rene8 on 2010-09-17
Hullo;

I've got a similar problem with a friend's HP mini laptop. I was able to boot from a Live-USB device (there's no CDROM unit) and run the boot-info script. Here I post the contents of the RESULTS.txt file:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD /grldr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
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

/dev/sda1    *          2,048   216,391,679   216,389,632   7 HPFS/NTFS
/dev/sda2         216,391,680   293,699,583    77,307,904   7 HPFS/NTFS
/dev/sda3         293,701,632   312,580,095    18,878,464   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1999 MB, 1999568384 bytes
62 heads, 62 sectors/track, 1015 cylinders, total 3905407 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,901,659     3,901,598   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1006 MB, 1006108672 bytes
24 heads, 23 sectors/track, 3559 cylinders, total 1965056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 248     1,965,055     1,964,808   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       86b4fa43-5f22-4fe1-8819-b904e9115817   ext3                                     
/dev/loop2       ea54055c-cd86-4ded-b283-244e39df635c   ext4                                     
/dev/sda1        036E54FD6072B503                       ntfs                                     
/dev/sda2        04A249AEA249A4D0                       ntfs       New Volume                    
/dev/sda3        10D6CA49D6CA2F32                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        318E-CA99                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        FC5E-7139                              vfat       CACHA_1GB                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/CACHA_1GB         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

```

I noticed it said one of the devices had errors and made a suggestion, so I ran dmesg, as it suggested. Here are the ten last lines:


```
[ 1032.193490] sd 8:0:0:0: [sdc] 1965056 512-byte logical blocks: (1.00 GB/959 MiB)
[ 1032.194072] sd 8:0:0:0: [sdc] Write Protect is off
[ 1032.194083] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1032.194092] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1032.198963] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1032.198982]  sdc: sdc1
[ 1032.275130] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1032.275157] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 1094.837380] EXT4-fs (loop2): INFO: recovery required on readonly filesystem
[ 1094.837392] EXT4-fs (loop2): write access unavailable, cannot proceed
```

I hope you can help me, so I can help my friend.

Thanks.

---

### Post by rene8 on 2010-09-17
Forgot to say that the error is not 'out of disk', but it says:
error: no such device: [and then a device tag]

Hope you can help.

BTW, Live-USB does not recognize the network so, so far, I haven't been able to do the reinstall of Grub2 as suggested previously.

---

### Post by rene8 on 2010-09-17
Another update: it seems that it isn't even recognizing the device (partition) where Linux is! :|

---

### Post by bcbc on 2010-09-18
@rene8, your problems is different. Your friend installed with wubi, and then allowed a grub-pc update to install the grub bootloader to the disk MBR. This doesn't work with wubi, you need the windows bootloader. Either repair with windows disc (on xp run 'fixmbr', on vista/7 run 'bootrec.exe /fixmbr') or boot a live CD and run 
```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```
Lilo can function the same way as the windows bootloader, and you can ignore the warnings you get when you install it.

---

### Post by rene8 on 2010-09-19
Thank you very much @bcbc !!

My friend honestly didn't have a clue about the way he had installed his OS - and I had no idea about the existence of Wubi, since I've always installed Ubuntu (done it several times) from the .iso image.

I've read about Wubi now, and so I'll be able to help my friend.
Thanks again!

---

