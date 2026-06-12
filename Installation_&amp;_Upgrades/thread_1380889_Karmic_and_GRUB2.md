---
title: "Karmic and GRUB2"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by Geffers on 2010-01-14
I posted this about 3 weeks ago in the 'Desktop' forum and with no replies feel this may be a better area ;)

I've got Karmic installed on my netbook which I understand uses Grub2 which is still a BETA version.

I still seem to have the original GRUB (legacy) within the file system, still have a menu.lst file but is appears to be showing the contents of grub.cfg at boot time.

What is happening at boot time, is GRUB Legacy handing over to GRUB2 at boot or is the an option for GRUB2 to hand over to Grub Legacy.

Geffers

---

### Post by darkod on 2010-01-14
If this was a clean install, grub legacy should be nowhere near. :)

When the boot menu shows, notice at the top whether it says 1.97, that's grub2. Also, if confused by the menu.lst file (which if it was clean install I have no idea how it got there), just temporarily move it to your home folder for example.
If your system is still working fine, that file was not needed. But keep it in home for a while still.

If this was an upgrade from earlier version, then even if grub1 was also upgraded to grub2 (separate procedure than the ubuntu version upgrade), that would explain why menu.lst is still present there even if it's unused.

Don't forget, only clean install of Karmic installs grub2. An upgrade leaves grub1 on your system and continues to work with grub1.

---

### Post by chkl on 2010-01-14
I have a similar problem: I made a new, clean install of 9.10 Karmic on a DELL laptop with Win7. DualBoot is working (Boot menu says ver. 1.97 beta ...) but I cannot configure timeout and which OS to boot first.
I too have a menu.lst file (!?) which I've tried to edit without any effects at all.
Is this GRUB 2 ? and how do I configure Boot timeout / Boot order settings ?

/chkl

---

### Post by darkod on 2010-01-14
> **chkl said:**
> I have a similar problem: I made a new, clean install of 9.10 Karmic on a DELL laptop with Win7. DualBoot is working (Boot menu says ver. 1.97 beta ...) but I cannot configure timeout and which OS to boot first.
I too have a menu.lst file (!?) which I've tried to edit without any effects at all.
Is this GRUB 2 ? and how do I configure Boot timeout / Boot order settings ?

/chkl

Again, I have no idea what menu.lst would be doing there unless you played around and you created it yourself or copied it from somewhere.
For adjusting timeout in grub2, open:
sudo gedit /etc/default/grub

Change the timeout value. You can also change the default OS either by position (position in the list minus 1, so the first is 0, the second is 1, etc) or by name. By name is preferred because if any new kernel is added windows will still be default without any need to change the file again.
It should be something like:
GRUB_DEFAULT = "Windows 7 loader on /dev/sda1", the full name as shown in grub boot menu.

Save and close the file after the changes. Do sudo update-grub for new grub.cfg to be created after your changes.

---

### Post by running_rabbit07 on 2010-01-14
> **chkl said:**
> I have a similar problem: I made a new, clean install of 9.10 Karmic on a DELL laptop with Win7. DualBoot is working (Boot menu says ver. 1.97 beta ...) but I cannot configure timeout and which OS to boot first.
I too have a menu.lst file (!?) which I've tried to edit without any effects at all.
Is this GRUB 2 ? and how do I configure Boot timeout / Boot order settings ?

/chkl

Yes, you have Grub2. If you run a google search for Grub2, you will find a few HowTo threads and blogs that will show how to edit Grub2.

---

### Post by drs305 on 2010-01-14
chkl:

Welcome to Ubuntu and the Ubuntu forums.  :-)

[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by Leppie on 2010-01-14
> **chkl said:**
> I have a similar problem: I made a new, clean install of 9.10 Karmic on a DELL laptop with Win7. DualBoot is working (Boot menu says ver. 1.97 beta ...) but I cannot configure timeout and which OS to boot first.
I too have a menu.lst file (!?) which I've tried to edit without any effects at all.
Is this GRUB 2 ? and how do I configure Boot timeout / Boot order settings ?

/chkl
kramic sometimes apparently installs a mix of grub legacy and grub2 when doing a clean install.
to edit the boot timeout and default boot option you need to edit the grub defaults file. open it with and editor:
```
gksudo gedit /etc/default/grub
```
the following lines determine the 2 options you wanted to change:
```
GRUB_TIMEOUT="10"
GRUB_DEFAULT=0
```
if you want to boot 7 as default, then change to something like this:
```
GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)"
```
but the value has to match exactly the entry in grub.cfg. if you do not know exactly what it looks like, you can get it like this:
```
cat /boot/grub/grub.cfg | grep Windows
```
then use copy and paste and don't forget to use the quotes ;)

---

### Post by chkl on 2010-01-14
Something strange is going on ... I have tried all suggestions, edited /etc/default/grub, tried grub-set..., checked that GRUB_DEFAULT line in grub & grub.cfg matches, done update-grub ...
Still default = 0, no timeout.
Is it possible that multiple copies of the .cfg file exists (as my install seems to be a legacy/GRUB2 mix of some sort) ?

---

### Post by drs305 on 2010-01-14
Follow this thread to run the boot info script and post the results here (use the # symbol as explained in the link):
[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

This will let us see exactly what is on your system.

---

### Post by chkl on 2010-01-14
OK - here it comes:
(As you may notice, this machine is actually triple-boot with a 2008WinSrv on sdb3, however, this works OK and the "grub" default-boot problem was exactly the same before installation of the server OS)

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23f68a3b

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   912,730,856   881,928,937   7 HPFS/NTFS
/dev/sda4         912,732,160   976,771,071    64,038,912   5 Extended
/dev/sda5         912,734,208   976,771,071    64,036,864   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d4b3eb9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   417,665,023   417,662,976   7 HPFS/NTFS
/dev/sdb2         417,673,935   494,818,064    77,144,130   f W95 Ext d (LBA)
/dev/sdb5         417,673,998   480,166,784    62,492,787  83 Linux
/dev/sdb6         480,166,848   494,818,064    14,651,217  82 Linux swap / Solaris
/dev/sdb3         494,818,065   573,733,064    78,915,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: UUID="F4D44968D4492E64" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="DAC84D3FC84D1AE1" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="6E0CA4B80CA47D29" LABEL="Data" TYPE="ntfs" 
/dev/sdb1: UUID="2298F50498F4D76F" LABEL="DATAPART1" TYPE="ntfs" 
/dev/sdb3: UUID="01CA922AEE4017E0" LABEL="WinServer2008" TYPE="ntfs" 
/dev/sdb5: UUID="c49f8dd1-2cc9-4ae4-ade5-a655bb72801b" TYPE="ext4" 
/dev/sdb6: UUID="e16b1611-f8ec-4f8b-ab68-d42d27737435" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/christer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=christer)
/dev/sr1 on /media/MOBILE_CONNECT   type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sdb5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b

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

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Chainload into GRUB 2
root        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
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
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro single  vga=771
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro  vga=771  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set c49f8dd1-2cc9-4ae4-ade5-a655bb72801b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b ro single  vga=771
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set f4d44968d4492e64
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=c49f8dd1-2cc9-4ae4-ade5-a655bb72801b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=e16b1611-f8ec-4f8b-ab68-d42d27737435 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 213.8GB: boot/grub/core.img
 213.8GB: boot/grub/grub.cfg
 213.8GB: boot/grub/menu.lst
 213.8GB: boot/initrd.img-2.6.31-14-generic
 213.8GB: boot/initrd.img-2.6.31-15-generic
 213.8GB: boot/initrd.img-2.6.31-16-generic
 213.8GB: boot/initrd.img-2.6.31-17-generic
 213.8GB: boot/initrd.img-2.6.31-18-generic
 213.8GB: boot/vmlinuz-2.6.31-14-generic
 213.8GB: boot/vmlinuz-2.6.31-15-generic
 213.8GB: boot/vmlinuz-2.6.31-16-generic
 213.8GB: boot/vmlinuz-2.6.31-17-generic
 213.8GB: boot/vmlinuz-2.6.31-18-generic
 213.8GB: initrd.img
 213.8GB: initrd.img.old
 213.8GB: vmlinuz
 213.8GB: vmlinuz.old
```

---

