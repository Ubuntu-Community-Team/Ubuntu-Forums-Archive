---
title: "GRUB List"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by jet-san on 2010-06-14
Hi there!

Few days ago I removed my Ubuntu 10.04 and replaced it with 9.10 (clean install).
I had few problems with installation in general, but now everything is fine.
Only one problem is my Grub List.
It doesn't look like always when I start PC (different font) - "GNU GRUB version 1.97~beta4".

When I type:
```
x@c-desktop:~$ sudo gedit /boot/grub/menu.lst
```
I can see only empty document.

I don't know is this useful, but I get that:
```
x@y-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```
There is also Win XP on the bottom of the list - don't know why it's not here.
What should I do to see and edit my list?

Regards
Jet

---

### Post by darkod on 2010-06-14
Since Karmic ubuntu comes with the new grub2, which doesn't use menu.lst so that's why it opened empty file.

But the update-grub command should have located XP if everything is fine with it and add it to the boot menu.

Since it didn't, run the boot info script from my signature and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

It will show us more details.

---

### Post by jet-san on 2010-06-14
Omfg, before posting my previous post I did "sudo update-grub" and Win XPis not listed now;(

Your script results:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9b4d9b4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   976,768,064   894,852,630   f W95 Ext d (LBA)
/dev/sda5          81,915,498   592,975,214   511,059,717   7 HPFS/NTFS
/dev/sda6         592,975,278   961,120,754   368,145,477  83 Linux
/dev/sda7         961,120,818   976,768,064    15,647,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B6A8E1A2A8E1617B                       ntfs                                     
/dev/sda5        E270766570763FF9                       ntfs                                     
/dev/sda6        c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2   ext4                                     
/dev/sda7        63874c9d-e966-4869-856d-97cbea3f9118   swap                                     
/dev/sda                                                jmicron_raid_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/E270766570763FF9  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro single 
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
UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=63874c9d-e966-4869-856d-97cbea3f9118 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 331.7GB: boot/grub/core.img
 306.1GB: boot/grub/grub.cfg
 304.2GB: boot/initrd.img-2.6.31-14-generic
 304.7GB: boot/initrd.img-2.6.31-22-generic
 304.1GB: boot/vmlinuz-2.6.31-14-generic
 304.3GB: boot/vmlinuz-2.6.31-22-generic
 304.7GB: initrd.img
 304.2GB: initrd.img.old
 304.3GB: vmlinuz
 304.1GB: vmlinuz.old

```

How can I add Win XP to my Grub list and make it default choice?

Regards
Jet

P.S.
What's the difference between ext3 and ext4?

---

### Post by oldfred on 2010-06-15
Are you running raid or was this drive ever part of raid set?

/dev/sda                     jmicron_raid_member

Usually that creates issues on gparted seeing the partitions or with the install.

Only if you are **not** running raid:
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by jet-san on 2010-06-15
I had a problem with clean installation.
Live CD couldn't see my partitions.
Someone recommended me to use this line:
```
sudo apt-get remove dmraid
```and it worked!

After that I was able to install Ubuntu once again.

```
sudo dmraid -E -r /dev/sda
Do you really want to erase "jmicron" ondisk metadata on /dev/sda ? [y/n] :
```

Yes? No?

---

### Post by dino99 on 2010-06-15
> **jet-san said:**
> I had a problem with clean installation.
Live CD couldn't see my partitions.
Someone recommended me to use this line:
```
sudo apt-get remove dmraid
```and it worked!

After that I was able to install Ubuntu once again.

```
sudo dmraid -E -r /dev/sda
Do you really want to erase "jmicron" ondisk metadata on /dev/sda ? [y/n] :
```

[COLOR="Red"]Yes[/COLOR]? No?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-06-15
> **jet-san said:**
> I had a problem with clean installation.
Live CD couldn't see my partitions.
Someone recommended me to use this line:
```
sudo apt-get remove dmraid
```and it worked!

After that I was able to install Ubuntu once again.

```
sudo dmraid -E -r /dev/sda
Do you really want to erase "jmicron" ondisk metadata on /dev/sda ? [y/n] :
```Yes? No?

Yes.

---

### Post by jet-san on 2010-06-15
Ok I have my Win XP option back:)

```
sudo grub-mkconfig
Generating grub.cfg ...
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
set root=(hd0,6)
search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
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
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c1ac4ff9-fa81-4c2d-96d9-d70678a8d9a2 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Microsoft Windows XP Home Edition on /dev/sda1
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set b6a8e1a2a8e1617b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
done
```

How can I edit my list to change default OS?

---

### Post by dino99 on 2010-06-15
use startup-manager and set your preference

---

### Post by jet-san on 2010-06-16
and... how can I do that?

<sry for noobish question:/>

---

### Post by oldfred on 2010-06-16
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

---

### Post by jet-san on 2010-06-17
> **oldfred said:**
> Download and install "StartUp-Manager from Synaptic package downloads(...)

Yatta!
It works, Thanks mate:)

Btw: can anyone explain me why do I have to use "StartUp-Manager" instead of simple "sudo gedit /boot/grub/menu.lst"?
Is it possible to remove some options from the list by StartUp-Manager?

Regards
Jet

---

### Post by darkod on 2010-06-17
> **jet-san said:**
> Yatta!
It works, Thanks mate:)

Btw: can anyone explain me why do I have to use "StartUp-Manager" instead of simple "sudo gedit /boot/grub/menu.lst"?
Is it possible to remove some options from the list by StartUp-Manager?

Regards
Jet

You don't have to use it. But for grub2 menu.lst doesn't exist any more. You control part of the settings in /etc/default/grub and you can edit default OS and timeout there.

You can remove Startup-Manager if you want. I prefer editing /etc/default/grub.

PS. For grub2 after editing settings you need to run:

sudo update-grub

---

