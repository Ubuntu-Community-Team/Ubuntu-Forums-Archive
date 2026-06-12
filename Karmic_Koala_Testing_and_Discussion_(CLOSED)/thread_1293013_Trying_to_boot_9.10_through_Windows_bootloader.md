---
title: "Trying to boot 9.10 through Windows bootloader"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by the.lost.one on 2009-10-16
Can anyone check this output? Karmic doesnt boot.

```
============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file /NST/nst_grub.mbr is trying to 
                       chain load sector #131122593 on boot drive #1
    Operating System:  Windows Vista
    Boot files/dirs:   /NST/menu.lst /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48350995

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    81,922,047    81,920,000   7 HPFS/NTFS
/dev/sda2          81,924,095   172,072,214    90,148,120   f W95 Ext d (LBA)
/dev/sda5          81,924,096   131,121,151    49,197,056   7 HPFS/NTFS
/dev/sda6         131,122,593   172,072,214    40,949,622  83 Linux
/dev/sda3         172,081,152   223,029,247    50,948,096   7 HPFS/NTFS
/dev/sda4         223,030,395   234,438,586    11,408,192   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="E6DA16DDDA16A9B7" TYPE="ntfs" 
/dev/sda3: UUID="783A18D13A188DEE" TYPE="ntfs" 
/dev/sda4: UUID="2C88743C8874071C" LABEL="HP_RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="965AD4A85AD48681" LABEL="Data" TYPE="ntfs" 
/dev/sda6: UUID="412e4042-a500-4ad1-b06d-2a4f34a111aa" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/kernel/debug type debugfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


============================== sda1/NST/menu.lst: ==============================

# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD/ 
 
default 0 
timeout 0 
 
title Chainload into GRUB 2 
412e4042-a500-4ad1-b06d-2a4f34a111aa 
kernel /boot/grub/core.img 
 
 
# All your boot are belong to NeoSmart!

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,6)
search --no-floppy --fs-uuid --set 412e4042-a500-4ad1-b06d-2a4f34a111aa
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
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 412e4042-a500-4ad1-b06d-2a4f34a111aa
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=412e4042-a500-4ad1-b06d-2a4f34a111aa ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 412e4042-a500-4ad1-b06d-2a4f34a111aa
    linux    /boot/vmlinuz-2.6.31-11-generic root=UUID=412e4042-a500-4ad1-b06d-2a4f34a111aa ro single 
    initrd    /boot/initrd.img-2.6.31-11-generic
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
    search --no-floppy --fs-uuid --set e6da16ddda16a9b7
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set 2c88743c8874071c
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=412e4042-a500-4ad1-b06d-2a4f34a111aa /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  67.1GB: boot/grub/grub.cfg
  67.1GB: boot/initrd.img-2.6.31-11-generic
  67.1GB: boot/vmlinuz-2.6.31-11-generic
  67.1GB: initrd.img
  67.1GB: vmlinuz
```

---

### Post by bodhi.zazen on 2009-10-16
Since you are asking a questino about how to configure Windows, I suggest you try asking this question on a Windows forum or submitting the question to Microsoft.

If you want support here I suggest you install grub or grub2, both of which will support booting windows and Ubuntu.

Last, since this is 9.10, moving to the karmic sub forum =)

---

### Post by kansasnoob on 2009-10-16
AFAIK it's not possible.

Please explain what you've done. Did you install Windows after installing Ubuntu? Be totally descriptive!

---

### Post by VMC on 2009-10-16
I noticed one of your outputs list EasyBCD. There is already a topic on this. Apparently EasyBCD has a beta that might work with grub2. Someone reported it didn't work.

It's easier to use grub2 to boot both Windows and Linux.

---

### Post by kansasnoob on 2009-10-16
> **VMC said:**
> I noticed one of your outputs list EasyBCD. There is already a topic on this. Apparently EasyBCD has a beta that might work with grub2. Someone reported it didn't work.

It's easier to use grub2 to boot both Windows and Linux.

+1!

If it's a simple dual boot it should be simple to do. I'm thinking just boot into Karmic and run from terminal:

```
sudo grub-install /dev/[COLOR="Red"]sdX[/COLOR]
``` [COLOR="Red"](of course **sdX** needs to be replaced with the proper destination)[/COLOR]

Then simply run:

```
sudo update-grub
```

---

### Post by louieb on 2009-10-16
Can't think of any reason easyBCD would not boot GRUB2 just like it does legacy GRUB. It just chainloads it. the trick is to get the GRUB2 stage1 code in the boot sector of of your Linux root partition. 

example 
```
grub-setup --force /dev/sda6
```take a look at [Herman's GRUB2 page]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html").

---

### Post by VMC on 2009-10-16
> **louieb said:**
> Can't think of any reason easyBCD would not boot GRUB2 just like it does legacy GRUB. It just chainloads it. the trick is to get the GRUB2 stage1 code in the boot sector of of your Linux root partition. 

example 
```
grub-setup --force /dev/sda6
```take a look at [Herman's GRUB2 page]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html").

Read [this]("http://ubuntuforums.org/showthread.php?t=1284914") reason on regression issues.

---

### Post by louieb on 2009-10-16
I have GRUB2 in the boot sector (VBR) of my Karmic install and I chainload it from Grub legacy.  I did have to use the --force option of grub-setup to get it there.  Maybe it is broken again now,  haven't tried again it since installing Karmic beta.   

Anyway thanks for the heads up. Hope I don't have to find out the hard way if grub-setup is broken again or not. Lou. 

BTW: to the OP I don't have Vista and I chainload Win 7 from Grub - so don't have any need to use easyBCB.  Guess you on your own with easyBCB - let us know how it worked out.

---

### Post by the.lost.one on 2009-10-17
> **bodhi.zazen said:**
> Since you are asking a questino about how to configure Windows, I suggest you try asking this question on a Windows forum or submitting the question to Microsoft.


Technically you are right but the Windows users  switch to / dual boot Ubuntu and no one was born an Ubuntu user.

> **kansasnoob said:**
> AFAIK it's not possible.

Please explain what you've done. Did you install Windows after installing Ubuntu? Be totally descriptive!

I had Vista. Then I installed Windows 7 on another partition. Then I installed Karmic (fresh install) on another partition with ext4 and grub on the same partition where Karmic was installed, hoping EasyBCD would let me boot it through windows bootloader.

Because before I installed Karmic, I had Jaunty which dual booted perfectly through windows bootloader using EasyBCD. I upgraded it to 9.10 which was a partial upgrade. Apparently, things looked ok except 1) it seemed to boot slightly slower even tho shutdown was astonishingly fast 2) the software sources links or deb urls (whatever u call em) were gone / disabled 3) it showed some error message like couldnt load xyz, although everything was apparently ok.

I can stick to Jaunty, even live without a ricoh webcam driver, but the way it makes the youtube videos jerky on full screen is a deal breaker. Karmic has solved the intel graphics issue BEAUTIFULLY.


VMC, I have checked other similar topics and googled using EasyBCD and editing windows bootloader. But I don't know how to add an entry to the win bootloader that points to a certain file that would boot ubuntu

---

