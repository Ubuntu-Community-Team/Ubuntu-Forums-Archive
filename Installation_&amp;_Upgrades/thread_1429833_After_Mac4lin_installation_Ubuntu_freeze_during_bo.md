---
title: "After Mac4lin installation Ubuntu freeze during boot up"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by Dr-a on 2010-03-14
I didn't do the whole steps during the installation , some of them were unable to be downloaded !

anyway I restarted my laptop (ubuntu logo appears) then the screen turned black and the touch pad works fine then nothing happens !
the screen is still black (user and password panel ) don't show up !:frown:

help me please :confused: I want my ubuntu back I don't want mac theme any more :-( 


**this might help ....**


   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008bd95

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   606,999,959   606,999,897  83 Linux
/dev/sda2         606,999,960   625,137,344    18,137,385   5 Extended
/dev/sda5         607,000,023   625,137,344    18,137,322  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
128 heads, 63 sectors/track, 60565 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x63de5376

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   470,253,567   470,251,520   7 HPFS/NTFS
/dev/sdb2         470,254,680   488,392,064    18,137,385   5 Extended
Empty Partition


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe93a112c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   781,401,599   781,401,537   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        efaceb66-ce9a-4604-8385-7566e606c5dd   ext4                                     
/dev/sda5        a6d978f2-1a08-4c6b-b101-9e76ac323ffc   swap                                     
/dev/sdb1        A6E27C6DE27C4419                       ntfs                                     
/dev/sdc1        DCE8-9522                              vfat       My Passport                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/My Passport       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set efaceb66-ce9a-4604-8385-7566e606c5dd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=efaceb66-ce9a-4604-8385-7566e606c5dd ro single 
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=efaceb66-ce9a-4604-8385-7566e606c5dd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a6d978f2-1a08-4c6b-b101-9e76ac323ffc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
  11.4GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .7GB: boot/initrd.img-2.6.31-19-generic
   1.1GB: boot/initrd.img-2.6.31-20-generic
   2.0GB: boot/initrd.img-2.6.31-20-generic-pae
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   1.1GB: boot/vmlinuz-2.6.31-20-generic
   2.0GB: boot/vmlinuz-2.6.31-20-generic-pae
   2.0GB: initrd.img
   1.1GB: initrd.img.old
   2.0GB: vmlinuz
   1.1GB: vmlinuz.old

---

### Post by Dr-a on 2010-03-14
Help me please :sad:

---

### Post by Dr-a on 2010-03-15
Please HELP !:popcorn:

---

### Post by Dr-a on 2010-03-15
anyone can help ?><

---

### Post by Dr-a on 2010-03-15
:confused::frown:

---

### Post by bcbc on 2010-03-15
press 'e' on your selected entry from the grub menu, use cursor and delete key to remove 'quiet splash', then hit ctrl-x to boot.
You should see terminal output as it boots and where it is hanging up.

---

### Post by Dr-a on 2010-03-15
> **bcbc said:**
> press 'e' on your selected entry from the grub menu, use cursor and delete key to remove 'quiet splash', then hit ctrl-x to boot.
You should see terminal output as it boots and where it is hanging up.

thanks, I'll try that but how can I save the changes after I remove 'quiet splash' ?

---

### Post by bcbc on 2010-03-15
> **Dr-a said:**
> thanks, I'll try that but how can I save the changes after I remove 'quiet splash' ?

Once you hit Ctrl-X it will boot without the quiet splash options. But it won't permanently save the changes nor do you want it to. This is just to try and see what the problem is, not a fix.

---

### Post by Dr-a on 2010-03-15
> **bcbc said:**
> Once you hit Ctrl-X it will boot without the quiet splash options. But it won't permanently save the changes nor do you want it to. This is just to try and see what the problem is, not a fix.

it didn't work :sad: the login panel didn't show up only touch pad works with blank black screen :-k

---

### Post by bcbc on 2010-03-15
Most likely you've broken gnome. One way to undo the changes is to do what's in this link, however note that it also removes other application settings that are stored in the folders mentioned.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I saw another thread on ubuntuforums that wasn't as destructive, but can't find it now.

edit: here's a similar guide [http://ubuntuforums.org/showthread.php?t=1423386&highlight=.gconf+fix+gnome](http://ubuntuforums.org/showthread.php?t=1423386&highlight=.gconf+fix+gnome) - not the one I was looking for - I recommend searching yourself first. (and backing up the folders before you delete).

another edit: there's a command to undo changes to gnome but (my understanding) is you need to know the area (<xxx>)that needs to be fixed.
```
gconftool-2 --recursive-unset <xxx> 
```

---

### Post by Atilana on 2010-03-15
Hi, that`s very weird try again hit Ctrl-X Remember that this is only to see the problem is not a solution. (it will boot without the quiet splash option).

---

### Post by Dr-a on 2010-03-15
> **bcbc said:**
> Most likely you've broken gnome. One way to undo the changes is to do what's in this link, however note that it also removes other application settings that are stored in the folders mentioned.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

I saw another thread on ubuntuforums that wasn't as destructive, but can't find it now.

edit: here's a similar guide [http://ubuntuforums.org/showthread.php?t=1423386&highlight=.gconf+fix+gnome](http://ubuntuforums.org/showthread.php?t=1423386&highlight=.gconf+fix+gnome) - not the one I was looking for - I recommend searching yourself first. (and backing up the folders before you delete).

another edit: there's a command to undo changes to gnome but (my understanding) is you need to know the area (<xxx>)that needs to be fixed.
```
gconftool-2 --recursive-unset <xxx> 
```

the first one didn't work I'll try the others :-k

---

### Post by Dr-a on 2010-03-15
> **Atilana said:**
> Hi, that`s very weird try again hit Ctrl-X Remember that this is only to see the problem is not a solution. (it will boot without the quiet splash option).

same problem when I hit Ctrl-X 
also the other solutions didn't work 
 
is it possible to be fixed  using live CD ?:confused:

---

### Post by bcbc on 2010-03-15
> **Dr-a said:**
> the first one didn't work I'll try the others :-k

Here's a post on completely removing ubuntu-desktop (i.e. gnome-desktop and all the applications that come with it) and then reinstalling: [http://ubuntuforums.org/showpost.php?p=8502689&postcount=2](http://ubuntuforums.org/showpost.php?p=8502689&postcount=2)

It seems pretty drastic - if you decide to go this route I'd recommend booting from liveCD and backing up first.

---

