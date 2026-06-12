---
title: "Duplication of Bootup options"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-07-30
I am running a dual-boot (Windows Vista and Ubuntu 10.04) PC system which is working quite well. However, during the bootup sequence where I can choose between the different Linux versions and Windows Vista, I have duplication of all choices. That is, the following appears:

**Ubuntu, with Linux 2.6.32-24-generic**
[B]Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on/dev/sda1)
Windows Vista (loader) (on/dev/sda1)[/B]

How can I remove (safely) these duplications?

---

### Post by ajgreeny on 2010-07-30
I can't comment on the windows entries, but wonder if by chance you made two attempts to install ubuntu and now have two different ubuntu OSs on your machine.  Can you show the output of ```
sudo fdisk -l
``` and report back here.

If you do really have just the one version, I honestly can not think of anything other than running ```
sudo update-grub
``` that might fix this anomaly.

---

### Post by virsto on 2010-07-30
> **ajgreeny said:**
> I can't comment on the windows entries, but wonder if by chance you made two attempts to install ubuntu and now have two different ubuntu OSs on your machine.  Can you show the output of ```
sudo fdisk -l
``` and report back here.

Ok, here is what was returned from this command:

[HTML]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x011382f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0564b259

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       45610   366359548    7  HPFS/NTFS
/dev/sdb2           45610       71059   204419060    7  HPFS/NTFS
/dev/sdb3           71060       91201   161790615    5  Extended
/dev/sdb5           71060       90378   155179836   83  Linux
/dev/sdb6           90379       91201     6610716   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d16751d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdd: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x617523e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24791   199133676    c  W95 FAT32 (LBA)
[/HTML]


If you do really have just the one version, I honestly can not think of anything other than running ```
sudo update-grub
``` that might fix this anomaly.

And here is the result from running this command:

[HTML]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda1
done[/HTML]

---

### Post by virsto on 2010-07-30
And I rebooted --- no change!

---

### Post by virsto on 2010-07-30
I am quite sure that I have only one Ubuntu 10.04 and I know for certain that I have only one Windows Vista. 

What file contains the information that is being duplicated?

---

### Post by gabytf on 2010-07-30
Good News! You can get it solve here, mine same problem had just being solved. Look at the last part  [COLOR=MAROON][B][SIZE=4]
Removing Older Kernels:[/SIZE][/B][/COLOR]
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

Thanks to drs305!

---

### Post by virsto on 2010-07-30
I looked at the link suggested gabytf; but, I do not believe that this gives a solution to my original posting.

First, the following does not apply,

gksu **gedit** /boot/grub/menu.lst
since I do not have this file on my system! 

Second, the following information is given,

> Note: Grub 2 does not use /boot/grub/menu.lst for it's options. The Grub  2 files include /boot/grub/grub.cfg, /etc/default/grub, and the  configuration scripts in the /etc/grub.d/ folder. Changes should not be  made to /boot/grub/grub.cfg.

But, I could find no information on what file can be edited (changed to fix my problem).

Any more suggestions would be appreciated.

---

### Post by virsto on 2010-07-30
The first part of 

[B]/boot/grub/grub.cfg
[/B]
contains:

```
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=12
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set be2a66f32a66a85b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0c1c48121c47f4ec
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 2cc8e5edc8e5b56c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

It seems clear that the duplications I see on bootup (as shown in my original posting) is reflected in this code. But, it is not at all clear to me how to correct the problem since this file contains in the beginning

# [B]DO NOT EDIT THIS FILE

[/B]Again, what should be done to fix this problem?

---

### Post by virsto on 2010-07-30
Ooph! I sent the wrong cfg file ---- from my other Ubuntu system! However, the correct cfg file does show the duplicated entries and thus my question still applies --- sorry about this foolish error.

---

### Post by virsto on 2010-07-30
The following is the correct cfg file that I should have posted:

```
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/00_header.backup.20100723 ###
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header.backup.20100723 ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/05_debian_theme.backup.20100723 ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme.backup.20100723 ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux.backup.20100723 ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux.backup.20100723 ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/20_memtest86+.backup.20100723 ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+.backup.20100723 ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e45e9ef65e9ec12a
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_os-prober.backup.20100723 ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e45e9ef65e9ec12a
    chainloader +1
}
### END /etc/grub.d/30_os-prober.backup.20100723 ###
```

This from the system that has the duplication problem.

---

### Post by gabytf on 2010-07-30
Since you are using Grub 2, hope this might help.
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

I still believe that you need to find a way to edit that loader file.

---

### Post by ajgreeny on 2010-07-30
> **gabytf said:**
> Since you are using Grub 2, hope this might help.
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

I still believe that you need to find a way to edit that loader file.
NO NO NO!

There is no point editing that file as it will revert the next time you run "sudo update-grub" or when a new kernel is installed.  The file is also read-only, so even as root you can not edit it without changing its permissions/properties.  The only sensible way to change that grub.cfg file is to edit the various files in /etc/grub.d/ which are all executable scripts, then run ```
sudo update-grub

```
Unfortunately I can see nothing that points to a reason for your duplication of entries in either the linked webpage above, nor in the various grub2 pages available from a search of this form.

Very weird!!

---

### Post by gabytf on 2010-07-30
Thank you for the correction. Ajgreeny

---

### Post by virsto on 2010-07-31
First thanks to ajgreeny and gabytf for your friendly and useful postings. My problem with duplications in the bootup menu was solved as follows.

When I examined the **/etc/grub.d** folder I found that there were backup scripts (files) that corresponded to these duplicate entries (e.g. **00_header.backup.20100723**, **05_debian_theme.backup.20100723**, etc.). I only needed to remove these *.backup.* files and then give the command

```
update-grub
```

I then shut down my system and rebooted into Ubuntu 10.04 and things are as they should be. That is, I now see the following in my bootup menu:

**Ubuntu, with Linux 2.6.32-24-generic**
[B]Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
Ubuntu, with Linux 2.6.32-23-generic
Ubuntu, with Linux 2.6.32-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on/dev/sda1)[/B]

Have a good day!:D

---

### Post by ajgreeny on 2010-07-31
I am interested how this happened as the backups made by gedit automatically (if you have that set in gedit's preferences) are not executable by default.  I assume you did a manual backup, either by renaming the original file, or by using the "sudo cp" command, both of which retain the executable status of the files.

Worth remembering, however, as it is something I did not think about.

---

### Post by virsto on 2010-07-31
> **ajgreeny said:**
> I am interested how this happened as the backups made by gedit automatically (if you have that set in gedit's preferences) are not executable by default. I assume you did a manual backup, either by renaming the original file, or by using the "sudo cp" command, both of which retain the executable status of the files.
 
Worth remembering, however, as it is something I did not think about.
 
 
This could be another thread --- How does such a thing happen? I am 100% sure that I did not do a manual backup nor did I use **sudo cp**.

---

