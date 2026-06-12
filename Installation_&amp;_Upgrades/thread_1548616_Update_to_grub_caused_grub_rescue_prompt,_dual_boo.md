---
title: "Update to grub caused grub rescue prompt, dual boot vista laptop"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by jotto! on 2010-08-08
OK, all was working all be it differently to my main PC.

Installed 10.04 on my daughters laptop from within windows Vista. All went OK but I had two boot loaders, ie turn on laptop and I would get the Windows loader asking if I want to boot in to windows or Ubuntu. Upon selecting ubuntu I would get the standard grub loader that I have on my PC.

Did an update a few mins ago and it asked me to update grub which I did and as there was only one disk showing clicked forward.

Now on reboot I have grub rescue prompt, no such device.

Hard drive is a single 80 gig drive with windows on one partition and ubuntu in another.

Have the live cd so can boot from that I guess....
what do I do next? TIA.

---

### Post by KCormier on 2010-08-08
easiest thing to start with would probably just be to reinstall grub.  Usually when a grub update fails, a reinstall allows it to detect everything and reconfigure itself.  It has been a few years since I've done this though, so you may want to wait till someone can reconfirm this for you.

-Kevin

---

### Post by jotto! on 2010-08-08
Thanks Kevin, am new to this myself so will wait and see waht others say.
Hopefully havent ballsed it up completely! lol

---

### Post by wilee-nilee on 2010-08-08
Your not actually using grub (as usual) in a wubi environment so upgrading or installing is not done. It sounds like you now have grub in the mbr, post the bootscript in my signature in code tags if you can from a Ubuntu environment.

Do you have a Vista install disc? if not here is a recovery disc link for repairs.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Is this grub rescue prompt at boot or after choosing Ubuntu from the MS boot loader?

---

### Post by jotto! on 2010-08-08
OK, Managed to get back my windows bootloader by using
bootrec.exe /fixmbr

I now have my windows and ubuntu loader via windows, however, now when I try to select Ubuntu it stops and reboots.

I can see something like 
try (hd0,0) : NTFS5:  no wubldr  
try (hd0,1) : NTFS5: 
Then an error message that I cant see as it goes to quickly before it reboots.

I used to see the no wubldr message before the update but it always loaded.

Any ideas?
TIA.

---

### Post by jotto! on 2010-08-08
> **wilee-nilee said:**
> Your not actually using grub (as usual) in a wubi environment so upgrading or installing is not done. It sounds like you now have grub in the mbr, post the bootscript in my signature in code tags if you can from a Ubuntu environment.

Do you have a Vista install disc? if not here is a recovery disc link for repairs.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

I downloaded that very disc to fix the vista mbr.
Shall I try the bootscript?

---

### Post by jotto! on 2010-08-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf2be11c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS
/dev/sda2    *     24,563,712    90,652,671    66,088,960   7 HPFS/NTFS
/dev/sda3          90,652,672   156,299,263    65,646,592   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 65 MB, 65536000 bytes
8 heads, 32 sectors/track, 500 cylinders, total 128000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             55       127,999       127,945   1 FAT12


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bb6360e3-6fc0-4830-9be8-abaa13b0688b   ext4                                     
/dev/sda1        B204B696E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        1AA02B3DA02B1F2F                       ntfs       ACER                          
/dev/sda3        FCC6E621C6E5DC40                       ntfs       DATA                          
/dev/sdb1                                               vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set fcc6e621c6e5dc40
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b204b696e49bed2a
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1aa02b3da02b1f2f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   2.6GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.32-21-generic
   3.5GB: boot/initrd.img-2.6.32-22-generic
   3.8GB: boot/initrd.img-2.6.32-24-generic
   3.3GB: boot/vmlinuz-2.6.32-21-generic
   3.4GB: boot/vmlinuz-2.6.32-22-generic
   3.7GB: boot/vmlinuz-2.6.32-24-generic
   3.8GB: initrd.img
   3.5GB: initrd.img.old
   3.7GB: vmlinuz
   3.4GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-08-08
sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab **/boot/grub/core.img**

This highlighted area is not in a wubi install from my computer. Otherwise the bootscript seems to look fine to me, but I might be missing something. The mbr is correct no extra grub files other then the install to sda3 wubi.

A more knowledgeable user on wubi would be helpful here.
Here is the wubi wiki link for a start.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

If I might suggest here that a real dual boot would be easier to maintain and more stable, and a little faster in Ubuntu, and allow for recovery from Windows from Ubuntu easily.

---

### Post by jotto! on 2010-08-08
Will read through the link, thanks for that.

I may just do a complete fresh install from disc rather than from within windows.

---

### Post by jotto! on 2010-08-09
Any other ideas before I try to uninstall and reinstall? Thanks.

---

