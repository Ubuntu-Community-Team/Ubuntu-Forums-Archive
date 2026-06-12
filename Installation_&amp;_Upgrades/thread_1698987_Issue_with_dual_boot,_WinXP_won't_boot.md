---
title: "Issue with dual boot, WinXP won't boot"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Rabblerouser on 2011-03-03
My issue is that I can't boot into my WinXP drive.

The master drive is Ubuntu.  The secondary drive is WinXP.

Within Ubuntu, I can access all the files off the WinXP drive, but that doesn't exactly help.

Grub isn't coming on to give me any choice of OS.

My tech level is rather high, but my Linux knowledge is limited.  I installed GrubEd to see if that'd help at all.  I set my Grub timeout to 30 in hopes of seeing the Grub, but it still didn't pop up.

Anyone that can solve my issue will get 10 internetz.  I'm pretty sure this is a n00b issue, so no more than 10!

---

### Post by swapnilnarendra on 2011-03-03
My friend you might want to provide the details of your system.
It would be helpful to know 'HOW' you installed Ubuntu?
Did you do it via 'wubi' ? 
Or did you install it via a USB or CD alongside your windows ? 
Or maybe you installed XP after Ubuntu ?

Also, please specify your system configuration. Your partitioning details and anything else you think might be creating the problem.

Because as far as I can understand, your windows partition might have shrunk and you need to provide a little more space to that partition using GParted.

---

### Post by Rabblerouser on 2011-03-03
Lessee.

My system has two hard drives.  A 40 GB and a 15 GB.  The 15 is the main.  The 40 is the secondary.

First I installed WinXP on the 40 with no problem.  Then I installed Ubuntu via a boot CD on the 15.

My Windows partition shouldn't have shrunk considering they're two entirely separate HDDs, right?  And I was very careful to make sure Linux only installed on the 15.

Edit:  And also, my BIOS reads both HDDs fine.  My 15 is set to boot before the 40.  Changing boot order has no effect.

---

### Post by Quackers on 2011-03-03
Have you run ```
sudo update-grub
``` in the terminal of your Ubuntu installation?

---

### Post by Rabblerouser on 2011-03-03
Just tried that and it didn't seem to help. =/

---

### Post by swapnilnarendra on 2011-03-03
well if you say that you have 2 different HDDs then I guess Ubuntu would not have affected your XP in anyway. Its rather strange why your XP is not booting up. It could be a totally new issue.

So even if it is an issue with the MBR, it should not affect the Grub of Ubuntu HDD... do you think that repairing your windows (using windows CD after making the CD ROAM priority to boot) might help ?

---

### Post by Quackers on 2011-03-03
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by weezyrider on 2011-03-03
I'm NOT an expert, but my system is similar to yours. I installed 10.10 over W2K on its own drive. Ubuntu acted a little weird - some things didn't work, and my messing around didn't help. So I reinstalled Ubuntu from a bootable CD. That time around the boot menu was in Grub, and made me think that Ubuntu had taken over the computer! A couple of nice people here straightened it out for me. 

The choice for XP was in grub on the second install. I didn't realize that and tried to boot from the bios as normal. Got an error message with a strange number in it. 
The post is titled bios.

The whole shebang is working as it should. 
W

---

### Post by Rabblerouser on 2011-03-04
> **swapnilnarendra said:**
> do you think that repairing your windows (using windows  CD after making the CD ROAM priority to boot) might help ?

Wouldn't that overwrite grub and leave me without access to Linux?

Quackers:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9082775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    29,993,354    10,458,315   5 Extended
/dev/sda5          19,535,103    29,993,354    10,458,252  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e7d5dbd0-b684-47cd-93fb-856389bdef29   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d9dc9905-2603-4c29-929b-5e80baac8a6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8A89F5EA89F19C8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9dc9905-2603-4c29-929b-5e80baac8a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   3.8GB: boot/initrd.img-2.6.31-14-generic
   4.3GB: boot/initrd.img-2.6.32-29-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-29-generic
   4.3GB: initrd.img
   3.8GB: initrd.img.old
   1.6GB: vmlinuz
   2.3GB: vmlinuz.old
```

---

### Post by Quackers on 2011-03-04
XP is now on sdb1, but none of its boot files are. Neither is a boot flag.
You will need to fix Windows boot with a Windows XP repair disc (by running fixmbr from the command prompt). That should replace the boot files.
A boot flag (which Windows likes to have) can be added with gparted.

---

### Post by Rabblerouser on 2011-03-04
Just to clarify, gparted is something I do within Linux?

---

### Post by Quackers on 2011-03-04
Yes, that's right. If you haven't installed gparted already go to System > Admin > Synaptic package manager and enter gparted in the search box. When it appears in the main window right-click it and select "mark for installation" then click the apply button in the toolbar.
After installation you will find the program in System > Admin > gparted

---

### Post by Rabblerouser on 2011-03-04
Good news and bad news.  Good news is that it is at least kinda seeing the boot now.  Bad news is that an error saying invalid partition comes up.

Maybe this new one will help:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9082775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    29,993,354    10,458,315   5 Extended
/dev/sda5          19,535,103    29,993,354    10,458,252  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e7d5dbd0-b684-47cd-93fb-856389bdef29   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d9dc9905-2603-4c29-929b-5e80baac8a6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8A89F5EA89F19C8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9dc9905-2603-4c29-929b-5e80baac8a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   3.8GB: boot/initrd.img-2.6.31-14-generic
   4.3GB: boot/initrd.img-2.6.32-29-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-29-generic
   4.3GB: initrd.img
   3.8GB: initrd.img.old
   1.6GB: vmlinuz
   2.3GB: vmlinuz.old
```

---

### Post by SkullTraill on 2011-03-04
> **Rabblerouser said:**
> Good news and bad news.  Good news is that it is at least kinda seeing the boot now.  Bad news is that an error saying invalid partition comes up.

Maybe this new one will help:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9082775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    29,993,354    10,458,315   5 Extended
/dev/sda5          19,535,103    29,993,354    10,458,252  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e7d5dbd0-b684-47cd-93fb-856389bdef29   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d9dc9905-2603-4c29-929b-5e80baac8a6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8A89F5EA89F19C8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9dc9905-2603-4c29-929b-5e80baac8a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   3.8GB: boot/initrd.img-2.6.31-14-generic
   4.3GB: boot/initrd.img-2.6.32-29-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-29-generic
   4.3GB: initrd.img
   3.8GB: initrd.img.old
   1.6GB: vmlinuz
   2.3GB: vmlinuz.old
```

I too have the invalid partition error. Hope I can get a fix by today :D

---

### Post by Quackers on 2011-03-04
I don't know what the invalid partition is.
You have Windows in the mbr of sda trying to boot Ubuntu and you have Grub2 in the mbr of sdb trying to boot Windows! Not ideal.
Do you have a Windows XP repair disc?

---

### Post by Rabblerouser on 2011-03-04
Er, it might also be worth noting that the invalid partition table error comes up when I try to boot into the 15 GB drive (sda) first.  I can only get into Linux (that is, bypassing the error) by setting the 40GB disk (sdb) to boot first in the BIOS.

And how the heck did I do that?  I thought I just fixed the mbr of sdb when I ran fixmbr.

Yes, I do.

---

### Post by SkullTraill on 2011-03-04
> **Rabblerouser said:**
> Er, it might also be worth noting that the invalid partition table error comes up when I try to boot into the 15 GB drive (sda) first.  I can only get into Linux (that is, bypassing the error) by setting the 40GB disk (sdb) to boot first in the BIOS.

And how the heck did I do that?  I thought I just fixed the mbr of sdb when I ran fixmbr.

Yes, I do.

Same here. Exactly.

---

### Post by Quackers on 2011-03-04
> **Rabblerouser said:**
> Er, it might also be worth noting that the invalid partition table error comes up when I try to boot into the 15 GB drive (sda) first.  I can only get into Linux (that is, bypassing the error) by setting the 40GB disk (sdb) to boot first in the BIOS.

And how the heck did I do that?  I thought I just fixed the mbr of sdb when I ran fixmbr.

Yes, I do.

Which hard drive was set to boot first when you ran fixmbr?

---

### Post by Rabblerouser on 2011-03-04
sdb was.

Good news and bad news once again!  So I rebooted and got a missing ntldr error.  The standard thing to do to fix that is from the WinXP cd, copy over the ntldr and ntdetect.com files over to the drive.

Guess what!  I can now boot into XP!

...But now because XP is working, I'm no longer able to access Linux as the XP failure was what was allowing me to bypass the invalid partition table error and get into Linux.

What should I do now, do you think?  If needed, I can just reinstall Linux no problem.

---

### Post by Quackers on 2011-03-04
Aha! That's good :-)
Please re-run the boot script and post the results. That should give us a clue.

---

### Post by Rabblerouser on 2011-03-04
But I can't get into Linux, remember? =/

Unless you want me to live cd it?

---

### Post by Quackers on 2011-03-04
Yes please.

---

### Post by Rabblerouser on 2011-03-04
I'll stay booted into the live cd in case of whatever. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9082775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdd0edd0e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    29,993,354    10,458,315   5 Extended
/dev/sda5          19,535,103    29,993,354    10,458,252  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        e7d5dbd0-b684-47cd-93fb-856389bdef29   ext4                                     
/dev/sda5        d9dc9905-2603-4c29-929b-5e80baac8a6f   swap                                     
/dev/sdb1        B8A89F5EA89F19C8                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
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
UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9dc9905-2603-4c29-929b-5e80baac8a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.6GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   3.8GB: boot/initrd.img-2.6.31-14-generic
   4.3GB: boot/initrd.img-2.6.32-29-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-29-generic
   4.3GB: initrd.img
   3.8GB: initrd.img.old
   1.6GB: vmlinuz
   2.3GB: vmlinuz.old
```

---

### Post by Quackers on 2011-03-04
You've got no boot.ini in XP boot files.

Regarding Ubuntu, we may get away with installing grub to the mbr of sda, from the live cd desktop. If it doesn't work we may have to purge/re-install grub.
Open up a terminal in the live desktop and copy/paste the following commands into it, one line at a time, pressing enter after each line.

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot, but go into your bios and make sda the first bootable HDD.
Hopefully Ubuntu should then boot directly.
If it does, open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run, to see if the Windows Loader is found. If it is, reboot and choose Windows from the new grub menu. If that boots you're good.

---

### Post by Rabblerouser on 2011-03-04
That worked perfectly!  Can boot from both linux and xp from grub!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9082775 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
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
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ntldr /ntdetect.com

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.4 GB, 15361597440 bytes
255 heads, 63 sectors/track, 1867 cylinders, total 30003120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,535,039    19,534,977  83 Linux
/dev/sda2          19,535,040    29,993,354    10,458,315   5 Extended
/dev/sda5          19,535,103    29,993,354    10,458,252  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,108,029    78,107,967   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e7d5dbd0-b684-47cd-93fb-856389bdef29   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d9dc9905-2603-4c29-929b-5e80baac8a6f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8A89F5EA89F19C8                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e7d5dbd0-b684-47cd-93fb-856389bdef29
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod ntfs
    set root='(/dev/sdb,1)'
    search --no-floppy --fs-uuid --set b8a89f5ea89f19c8
    drivemap -s (hd0) ${root}
    chainloader +1
}
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
UUID=e7d5dbd0-b684-47cd-93fb-856389bdef29 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d9dc9905-2603-4c29-929b-5e80baac8a6f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
   3.8GB: boot/initrd.img-2.6.31-14-generic
   4.3GB: boot/initrd.img-2.6.32-29-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.6GB: boot/vmlinuz-2.6.32-29-generic
   4.3GB: initrd.img
   3.8GB: initrd.img.old
   1.6GB: vmlinuz
   2.3GB: vmlinuz.old
```

---

### Post by Quackers on 2011-03-04
Excellent. I can go to sleep soon :-)

---

