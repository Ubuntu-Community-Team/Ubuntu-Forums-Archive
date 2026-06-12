---
title: "Dualing Booting, GRUB, issues"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by AndyC2D on 2010-02-09
Okay, let's start off with some background info. I've got two SATA HDDs currently in my machine. My "C" drive is a Seagate 320GB, and my "H" drive is a Seagate 500GB. The 500GB hard drive has Windows 7 installed on it, and it was first. I installed Ubuntu 9.1 on my 320GB today. Here's what I get when I run fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d7e5e07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488382464    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89338933

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37595   301981806   83  Linux
/dev/sdb2           37596       38913    10586835    5  Extended
/dev/sdb5           37596       38913    10586803+  82  Linux swap / Solaris
```As is, when I boot up my computer, it says "Grub loading." and proceeds to load Ubuntu directly without showing me a menu. When I hold shift while booting to force the menu to load, I get four options: ubuntu, ubuntu (recovery mode), memtest, and memtest (serial console). I'd like to add Windows 7 to my GRUB menu but when I run "sudo gedit /boot/grub/menu.lst" and add the following to menu.lst, Windows still doesn't show up on my menu.

```
title Windows 7
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
```

Also, when I hold shift to get to my GRUB menu, it indicates that I have grub2 at the top saying "1.97 beta 4".

---

### Post by presence1960 on 2010-02-09
I need to see more about your setup & boot process. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by AndyC2D on 2010-02-09
```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

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
Disk identifier: 0x7d7e5e07

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,766,975   976,764,928   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89338933

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   603,963,674   603,963,612  83 Linux
/dev/sdb2         603,963,675   625,137,344    21,173,670   5 Extended
/dev/sdb5         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        76BCEF2ABCEEE419                       ntfs                                     
/dev/sdb1        1fa2d51e-9066-4cff-a210-7c6e689f4e0f   ext4                                     
/dev/sdb5        d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=andy)


=========================== sdb1/boot/grub/menu.lst: ===========================

title Windows 7
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1fa2d51e-9066-4cff-a210-7c6e689f4e0f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false


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
search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
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
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
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
UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by presence1960 on 2010-02-10
> **AndyC2D said:**
> ```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

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
Disk identifier: 0x7d7e5e07

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,766,975   976,764,928   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89338933

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   603,963,674   603,963,612  83 Linux
/dev/sdb2         603,963,675   625,137,344    21,173,670   5 Extended
/dev/sdb5         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        76BCEF2ABCEEE419                       ntfs                                     
/dev/sdb1        1fa2d51e-9066-4cff-a210-7c6e689f4e0f   ext4                                     
/dev/sdb5        d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=andy)


=========================== sdb1/boot/grub/menu.lst: ===========================

title Windows 7
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1fa2d51e-9066-4cff-a210-7c6e689f4e0f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false


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
search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
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
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
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
UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I would put GRUB on sdb MBR. You can do this from the 9.10 Live CD. Boot the 9.10 Live CD, choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
``` This will mount your ubuntu / partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` That will put GRUB on MBR of sdb.

GRUB is now set. Reboot without the Live CD. Go into BIOS and set sdb (320 GB) as first hard disk to boot in the hard disk boot order. This will bring up GRUB when you boot. Save changes to CMOS and continue booting. 

FYI: here is a [link]("https://help.ubuntu.com/community/Grub2") to good info about GRUB2

P.S. Your windows 7 is missing some boot files. See here from the script:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]
```

You are missing bootmgr & /boot/BCD. I did some searching about your windows problem. Here is a [link ]("http://support.microsoft.com/kb/927392")to fix windows so it will boot. Please make sure that you put the windows disk to boot first in the hard disk boot order before attempting to repair windows. this is necessary because windows always writes to the first disk to boot. When repair is complete reboot and make sure you can boot into windows. If so then reboot and go back in BIOS and set sdb as first to boot. Continue booting into ubuntu. Run from terminal ```
sudo update-grub
``` Your windows should be detected now that your boot files are fixed and you should be good to go.

---

### Post by AndyC2D on 2010-02-10
> **presence1960 said:**
> I would put GRUB on sdb MBR. You can do this from the 9.10 Live CD. Boot the 9.10 Live CD, choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
``` This will mount your ubuntu / partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` That will put GRUB on MBR of sdb.

GRUB is now set. Reboot without the Live CD. Go into BIOS and set sdb (320 GB) as first hard disk to boot in the hard disk boot order. This will bring up GRUB when you boot. Save changes to CMOS and continue booting. 

FYI: here is a [link]("https://help.ubuntu.com/community/Grub2") to good info about GRUB2

P.S. Your windows 7 is missing some boot files. See here from the script:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR=Red]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]
```You are missing bootmgr & /boot/BCD. I did some searching about your windows problem. Here is a [link ]("http://support.microsoft.com/kb/927392")to fix windows so it will boot. Please make sure that you put the windows disk to boot first in the hard disk boot order before attempting to repair windows. this is necessary because windows always writes to the first disk to boot. When repair is complete reboot and make sure you can boot into windows. If so then reboot and go back in BIOS and set sdb as first to boot. Continue booting into ubuntu. Run from terminal ```
sudo update-grub
``` Your windows should be detected now that your boot files are fixed and you should be good to go.

Sorry for the delayed response. I ran the commands you specified on my LiveCD and repaired my MBR using my Windows DVD. I also updated grub in Ubuntu where I get this output:
```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-19-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```I made sure my 320GB drive is set to boot first. I still see "GRUB loading." and I still have to hold shift to see the GRUB menu. Windows still doesn't show up on my GRUB menu, also. It seems that I have GRUB 2, not GRUB legacy. Isn't the "sudo update-grub" command for GRUB legacy? Attempting to run "sudo update-grub2" yeilds the following output:

```
sudo: update-grub2: command not found
```

---

### Post by kansasnoob on 2010-02-10
Well at some point you must have installed the package 'grub":

> sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   **[COLOR="Red"]/boot/grub/menu.lst[/COLOR]** **[COLOR="Red"]/boot/grub/grub.cfg[/COLOR]** /etc/fstab 
                       /boot/grub/core.img

Having mixed grub and grub2 files messes things up, menu.lst is part of legacy grub and grub.cfg is part of grub2. So lets fix it, boot into Ubuntu and run the following:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove grub
```

```
sudo apt-get --purge remove grub-common
```

```
sudo apt-get install --reinstall grub-pc
```

```
sudo update-grub
```

Wait for it to say done!

```
sudo grub-install /dev/sda
```

---

### Post by AndyC2D on 2010-02-10
> **kansasnoob said:**
> Well at some point you must have installed the package 'grub":



Having mixed grub and grub2 files messes things up, menu.lst is part of legacy grub and grub.cfg is part of grub2. So lets fix it, boot into Ubuntu and run the following:

```
sudo mv /boot/grub /boot/grub_backup
``````
sudo mkdir /boot/grub
``````
sudo apt-get --purge remove grub
``````
sudo apt-get --purge remove grub-common
``````
sudo apt-get install --reinstall grub-pc
``````
sudo update-grub
```Wait for it to say done!

```
sudo grub-install /dev/sda
```
OK, now what. I ran the commands you suggested. Here's my new results.txt:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d7e5e07

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,766,975   976,764,928   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89338933

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   603,963,674   603,963,612  83 Linux
/dev/sdb2         603,963,675   625,137,344    21,173,670   5 Extended
/dev/sdb5         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        76BCEF2ABCEEE419                       ntfs                                     
/dev/sdb1        1fa2d51e-9066-4cff-a210-7c6e689f4e0f   ext4                                     
/dev/sdb5        d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=andy)


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
search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
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
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1fa2d51e-9066-4cff-a210-7c6e689f4e0f
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
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
UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=d4f5731b-51b1-43ad-8ae9-8e9e8caf6d13 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```I seems that even though I ran "bootrec.exe /fixmbr" when using the Windows DVD that my Windows boot files remain unchanged.

---

### Post by kansasnoob on 2010-02-10
**[COLOR="Red"]Just jump to the next post![/COLOR]**

OK run the command:

```
sudo os-prober
```

And see if it finds Windows.

If it does again run:

```
sudo update-grub
```

Wait for it to say done! If it still does NOT find Windows try this:

```
sudo grub-install /dev/sdb
```

And once again:

```
sudo update-grub
```

If it's still a no-go I'll need to do some more research.

---

### Post by kansasnoob on 2010-02-10
I was just looking and it appears that Win 7 may require the following boot files/dir:

/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You show only:

/Windows/System32/winload.exe

I can't be absolutely certain because I haven't bought any Win since XP, but it looks like you may be missing **/bootmgr & /Boot/BCD**.

Since you say:

"I seems that even though I ran "bootrec.exe /fixmbr" when using the Windows DVD that my Windows boot files remain unchanged."

And the results of the Boot Info script showed:

> => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=1fa2d51e-9066-4cff-a210-7c6e689f4e0f)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb


I think using the Windows disc to restore the Windows mbr didn't work right, like it installed the Win mbr on sdb instead of sda. And Windows is on sda1.

So to give sda a Windows "readable" mbr you could use your Ubuntu Live CD and from the Live Desktop run the following commands:

**[COLOR="Red"]Note: you will not be able to boot either Ubuntu or Windows once you do this so read on![/COLOR]**

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

That should make Windows try to boot but I think you're missing at least /bootmgr. I'm not sure about /Boot/BCD, it may only be required with easy BCD.

**Note**: It's also possible that due to BIOS settings you might need to repeat that using **sdb**! Like this:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sdb mbr
```

So then I think you can follow these basic steps to fix Win 7's boot files:

[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

I know that's for Vista but I think it's very similar. In Vista I sometimes found it necessary to run the repair 2 or 3 times to get-r-dun but it worked.

Once Win 7 is booting under it's own power you'll need to restore grub2 again like this using the Ubuntu Live CD:

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
grub-install /dev/sdb
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

I hope that helps :)

---

