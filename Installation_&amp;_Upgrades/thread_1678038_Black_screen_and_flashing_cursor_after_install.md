---
title: "Black screen and flashing cursor after install"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by scarypajamas on 2011-01-29
After installing Ubuntu Server 10.04 LTS, I restarted my machine.  I removed the disk, but now when it starts, it never gets to GRUB.  Instead, it just takes me to a black screen with a blinking cursor.  I can't type in anything and holding shift doesn't take me to GRUB.

Any advice?

---

### Post by sikander3786 on 2011-01-29
I would recommend to try once again press and hold down Shift key from your Bios screen. You can try with both the Shift keys one by one and see if it takes you to Grub menu.

Or if not, I wonder if Grub was correctly installed. For diagnosing that, we need to you to boot an Ubuntu Live CD/USB (desktop edition) in Try mode and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by scarypajamas on 2011-01-29
Thanks for the quick reply.  Here is the contents of RESULTS.txt:

I'm wondering if I didn't install something right?  Under sda1 everything is blank :confused:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location.
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000101

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     33,488,920    67,108,918    33,619,999   0 Empty
/dev/sda2          35,651,584    85,983,231    50,331,648   0 Empty
/dev/sda3                   0     1,246,463     1,246,464  13 Unknown

/dev/sda1 overlaps with /dev/sda2

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45944593

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   542,225,879   542,225,817   7 HPFS/NTFS
/dev/sdb2         542,225,880   976,784,129   434,558,250   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00031f6a

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 2,918,221,823 2,918,219,776  83 Linux
/dev/sdc2       2,918,223,870 2,930,276,351    12,052,482   5 Extended
/dev/sdc5       2,918,223,872 2,930,276,351    12,052,480  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdc1        bddc7068-4170-477f-9c8f-f78cc94f84b5   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
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
menuentry 'Ubuntu, with Linux 2.6.32-24-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=bddc7068-4170-477f-9c8f-f78cc94f84b5 ro   quiet
    initrd    /boot/initrd.img-2.6.32-24-server
}
menuentry 'Ubuntu, with Linux 2.6.32-24-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
    echo    'Loading Linux 2.6.32-24-server ...'
    linux    /boot/vmlinuz-2.6.32-24-server root=UUID=bddc7068-4170-477f-9c8f-f78cc94f84b5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set bddc7068-4170-477f-9c8f-f78cc94f84b5
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=bddc7068-4170-477f-9c8f-f78cc94f84b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
#UUID=dc911eed-1eef-4321-9e14-f7f8c91419d0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sdc1: Location of files loaded by Grub: ===================


 558.4GB: boot/grub/core.img
1430.4GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.32-24-server
 558.4GB: boot/vmlinuz-2.6.32-24-server
    .2GB: initrd.img
 558.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2



=============================== StdErr Messages: ===============================

hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory

```

EDIT:  I forget to mention I was able to get this by using a Live CD.  Shift still doesn't launch GRUB...

---

### Post by sikander3786 on 2011-01-30
So you've got three hard disks and Ubuntu is on sdc whereas Grub is installed in the MBR of sda. You need to get it in the MBR of your sdc. But before you do that, make sure you've got an option in your Bios menu to make your sdc, the first boot device.

There are numerous mount errors in the output you posted above. If you plan to format both sda and sdb HDDs, that is not a problem.

So from the booted Live CD, follow the commands below.

```
sudo mount /dev/sdc1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sdc
```

Note, for the 2nd command it is just sdc without an integer and not sdc1. Reboot and make sdc first boot device. Lets hope it boots Ubuntu successfully this time.

---

### Post by LatinHacker on 2011-01-31
I have a similar problem, but my screen does not stay blank, is goes to de "Grub rescue>" but saying "Unknown filesystem"

My Boot info from the live CD says:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   731,006,975   730,800,128   7 HPFS/NTFS
/dev/sda3         731,021,821   976,768,064   245,746,244   5 Extended
/dev/sda5         731,021,823   764,453,024    33,431,202  82 Linux swap / Solaris
/dev/sda6         764,453,088   976,768,064   212,314,977  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   156,537,359   156,537,297   7 HPFS/NTFS
/dev/sdb2         156,537,360   976,768,064   820,230,705  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DE74E88F74E86BA9                       ntfs       System Reserved               
/dev/sda2        C8B4F5E6B4F5D742                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a5eea473-38c5-46dc-8249-515e0f31b59f   swap                                     
/dev/sda6        8ce055a2-ff5c-417d-82f7-43bdaffa3ed5   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        589BEA8471065D9C                       ntfs       LatinHacker_75                
/dev/sdb2        bfe89584-3960-407d-b53b-7ea07c3c28c8   ext2       LatinHacker_450               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        786cc81e-292d-4f6a-95ce-7ac16b4cb45f   ext2       LatinHacker_USB               
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/LatinHacker_USB   ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/LatinHacker_75    fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb2        /media/LatinHacker_450   ext2       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    echo    'Loading Linux 2.6.32-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=/dev/sda6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 8ce055a2-ff5c-417d-82f7-43bdaffa3ed5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set de74e88f74e86ba9
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=8ce055a2-ff5c-417d-82f7-43bdaffa3ed5 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a5eea473-38c5-46dc-8249-515e0f31b59f none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 480.6GB: boot/grub/core.img
 480.6GB: boot/grub/grub.cfg
 480.5GB: boot/initrd.img-2.6.32-28-generic-pae
 480.4GB: boot/vmlinuz-2.6.32-28-generic-pae
 480.5GB: initrd.img
 480.4GB: vmlinuz

```And when I tried your solution, it gave me this:

```

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /mnt/boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

My guess is that because it is loading from a SATA drive in the 4th position and this new computer (custom build) is more likerly to work with a HDD in the 1st or 3rd SSATA pusition, I most change something, but the CMOS/BIOS is set to start from sda... not sure what to do.

---

### Post by stereosteve on 2011-01-31
My problem is similar to scarypajamas except I am still stuck. I installed 10.10 x64 onto a virgin system. I started with the "try" option and selected "install" while there. The install seemed to go fine.

When I reboot there is a short series of cursor flashes and the screen goes black. A few seconds later, the drum sound from the login is heard. I hit enter and entered my password and the login song played. ---STILL BLACK SCREEN.

When I tried to boot again from the CD, it, too goes to black screen!

I finally got Puppy Linux to load (that's where I am now) and tried the bootscript thing.

The RESULTS.txt file is attached.

All help is appreciated.

---

### Post by stereosteve on 2011-01-31
Here is the RESULTS.txt from my previous post:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
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

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   954,511,359   954,509,312  83 Linux
/dev/sda2         954,513,406   976,771,071    22,257,666   5 Extended
/dev/sda5         954,513,408   976,771,071    22,257,664  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        773e1706-76e5-4dd8-b8c2-0fd161af35ea   ext4                                     
/dev/sda5        b1bcfe8d-8f71-4cc6-9a1c-d79479509ae0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
unionfs          /                        aufs       (rw,relatime,si=9e6bad53)
/dev/loop0       /initrd/pup_ro2          squashfs   (ro,noatime)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
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
	search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=773e1706-76e5-4dd8-b8c2-0fd161af35ea ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=773e1706-76e5-4dd8-b8c2-0fd161af35ea ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 773e1706-76e5-4dd8-b8c2-0fd161af35ea
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
# / was on /dev/sda1 during installation
UUID=773e1706-76e5-4dd8-b8c2-0fd161af35ea /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b1bcfe8d-8f71-4cc6-9a1c-d79479509ae0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 464.0GB: boot/grub/core.img
  86.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
 463.9GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
 463.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda hdb hdc hdd sdb sdc sdd sde sdf sdg sdh sdi 

```

---

### Post by stereosteve on 2011-01-31
After looking at the cchtml.com Ubuntu Maverick Installation Guide, I was able to shutdown my system correctly and reset xorg.conf through a series of Alt-PrtScr-? entries.

I then had a usable GUI. I loaded the restricted Radeon drivers, reset my screen res and was ready to go.

---

### Post by LatinHacker on 2011-02-01
> **stereosteve said:**
> After looking at the cchtml.com Ubuntu Maverick Installation Guide, I was able to shutdown my system correctly and reset xorg.conf through a series of Alt-PrtScr-? entries.

I then had a usable GUI. I loaded the restricted Radeon drivers, reset my screen res and was ready to go.


Mine is still not solved.  I am attempting to install the Grub on sda1 instead of sda6.  No video card issues here, Linux and Windows cannot read the HDD once I installed either.](*,)

---

### Post by scarypajamas on 2011-02-01
> **sikander3786 said:**
> So you've got three hard disks and Ubuntu is on sdc whereas Grub is installed in the MBR of sda. You need to get it in the MBR of your sdc. But before you do that, make sure you've got an option in your Bios menu to make your sdc, the first boot device.

Oh, how silly of me!  I was able to fix the problem as you said by using a recovery CD and installing grub to sdc.  Thanks for your help!

---

### Post by gzdskc on 2011-02-21
hi ubuntu users,

I have same kind of problem. I have two disks. I have installed 64-bit ubuntu 10.10 and now I am trying to install 32- bit Ubuntu 10.10. I took advice about installing grub. You can find my RESULTS.txt as an attachment. Although it seems grub 2 is installed on both disks, reboot is again unsuccessful. Thanks for your help.

---

### Post by sikander3786 on 2011-02-22
Welcome to the forums *gzdskc* :-)

Your Results.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 361007784 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Grub 2 is installed in the MBR of /dev/sdb and looks at sector 2048 of the 
    same hard drive for core.img, but core.img can not be found at this 
    location.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048         4,095         2,048 Linux or Data
/dev/sda2           4,096 3,810,553,855 3,810,549,760 Linux or Data
/dev/sda3   3,810,553,856 3,907,028,991    96,475,136 Linux Swap

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,804,121,087 3,804,116,992 Linux or Data
/dev/sdb3   3,804,121,088 3,907,028,991   102,907,904 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        79160955-d61f-40ae-b6ce-023e4889d4a8   ext4                                     
/dev/sda3        0111a46f-b31a-41a6-be99-9d015ddc6f4f   swap                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb2        59f99140-3589-4d20-ae73-915c18db3474   ext4                                     
/dev/sdb3        82787620-70b3-49f6-be7e-c3b8f1f8d6d3   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
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
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=79160955-d61f-40ae-b6ce-023e4889d4a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=79160955-d61f-40ae-b6ce-023e4889d4a8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdb2)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 5c4c0083-f945-4c90-bc48-02ffbf29d0bc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5c4c0083-f945-4c90-bc48-02ffbf29d0bc ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdb2)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 5c4c0083-f945-4c90-bc48-02ffbf29d0bc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=5c4c0083-f945-4c90-bc48-02ffbf29d0bc ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=79160955-d61f-40ae-b6ce-023e4889d4a8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=0111a46f-b31a-41a6-be99-9d015ddc6f4f none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


 917.1GB: boot/grub/core.img
 113.9GB: boot/grub/grub.cfg
 466.4GB: boot/initrd.img-2.6.35-22-generic
 917.1GB: boot/vmlinuz-2.6.35-22-generic
 466.4GB: initrd.img
 917.1GB: vmlinuz

=========================== sdb2/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd1,gpt2)'
search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd1,gpt2)'
search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=59f99140-3589-4d20-ae73-915c18db3474 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=59f99140-3589-4d20-ae73-915c18db3474 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd1,gpt2)'
	search --no-floppy --fs-uuid --set 59f99140-3589-4d20-ae73-915c18db3474
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda2)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=79160955-d61f-40ae-b6ce-023e4889d4a8 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda2)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 79160955-d61f-40ae-b6ce-023e4889d4a8
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=79160955-d61f-40ae-b6ce-023e4889d4a8 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
}
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

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=59f99140-3589-4d20-ae73-915c18db3474 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=82787620-70b3-49f6-be7e-c3b8f1f8d6d3 none            swap    sw              0       0

=================== sdb2: Location of files loaded by Grub: ===================


 184.8GB: boot/grub/core.img
1484.0GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-25-generic-pae
 184.8GB: boot/vmlinuz-2.6.35-25-generic-pae
    .5GB: initrd.img
 184.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2e 00 20 08  |.............. .|
00000200

Unknown BootLoader  on sdb1

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 01 08 00 00  00 00 00 00 2e 00 20 08  |.............. .|
00000200


```

---

### Post by sikander3786 on 2011-02-22
Grub is not installed properly. Boot an Ubuntu Live CD/USB and follow the commands below.

These 2 commands will install Grub in the MBR of your sda drive for the Ubuntu install present in sda2.

```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]a[/COLOR]
```

Note, for the 2nd command it is just sda without any integer.

And these will install Grub for sdb for the install present in sdb2.

```
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]b[/COLOR]
```

Reboot, select either of your HDD as the first boot device in Bios and then from Ubuntu' Terminal, run this command to add the other Ubuntu install to the Grub menu.

```
sudo update-grub
```

Good Luck!

---

