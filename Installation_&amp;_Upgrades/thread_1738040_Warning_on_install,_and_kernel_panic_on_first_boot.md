---
title: "Warning on install, and kernel panic on first boot."
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by Lovegain on 2011-04-24
I am trying to install Ubuntu 10.10 from a USB flash memory stick. It works fine until around 95%, where I get the following warning/error:

> An error occurred while removing packages:         
E:Sub-process /usr/bin/dpkg returned an error code (1)
The following packages are in a broken state:
[but no packages listed]

I click OK and the installer seems to finish nicely, except the terminal throws several errors along these lines (see [photo]("http://ekologik.se/arild/bilder/files/valhaj139z.jpg")):

```
end_request: I/O error, dev sdg, sector 50542
SQUASHFS error: squashfs_read_data failed to read block 0xe1aa8b2
error: unexpectedly disconnected from boot status daemon
```

However at boot I get the following, whether I choose the recovery option or not in GRUB:
                                                    
```
VFS: Cannot open root device "sda6" or unknown-block(0,0)
Please append a correct "root=" boot option; Here are the available partitions:
0b00 1048575 sr0 driver: sr                                              
Kernel panic - not syncing: VFS: Unable to mount root fs on onknown-block(0,0)
...
```

My partition setup is:
/dev/sda2 swap
/dev/sda4 Ubuntu /boot
/dev/sda6 Ubuntu /
There is also a Gentoo system on the same disk, and Windows on another disk.

I tried also with 10.04 LTS, the difference being that the install warning appears two or three times instead of once.

Some results from googling ([Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1594289"), [Ubiquity bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659113")) suggest unchecking the initial update options. I am going to try this but I'm not sure if I'll be able to get the boot loader right (there seemed to be problems with this).

---

### Post by Lovegain on 2011-04-24
> **Lovegain said:**
> Some results from googling ([Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1594289"), [Ubiquity bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659113")) suggest unchecking the initial update options. I am going to try this but I'm not sure if I'll be able to get the boot loader right (there seemed to be problems with this).

Unfortunately this made no difference. I get the same errors as when the options are checked.

---

### Post by Dutch70 on 2011-04-24
Doesn't Gentoo use grub legacy? That may have something to do with it.

---

### Post by Lovegain on 2011-04-24
> **Dutch70 said:**
> Doesn't Gentoo use grub legacy? That may have something to do with it.
From what I can tell, I'm using GRUB 2. How can the boot loader interfere with the installation and booting of Ubuntu?

---

### Post by Dutch70 on 2011-04-24
> **Lovegain said:**
> From what I can tell, I'm using GRUB 2. How can the boot loader interfere with the installation and booting of Ubuntu?

Grub Legacy counts from (hd0,0) Grub2 counts from (hd0,1). For example, I have grub2, but I also run PCLinuxOS which uses legacy, so I have to go into the grub.cfg and on my system, change (hd0,5) to (hd0,6) or I get a kernel panic when trying to boot PCLinuxOS.

Lets have a look at your boot info script. If anyone can help you, they will need to see it.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step, or you will lose the formatting & I doubt anyone will look at it.

---

### Post by Lovegain on 2011-04-24
I ran the boot info script from the Gentoo system and then removed some bits that I'm sure have nothing to do with the problem. If you think otherwise please inform me and I'll do it properly along the instructions of Dutch70.

```
arla@ezekiel ~ $ cat RESULTS-r.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst 
                       /boot/grub/grub.conf /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

...

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500,1 GB, 500107862016 byte
255 huvuden, 63 sektorer/spår, 60801 cylindrar, totalt 976773168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63        32,129        32,067  83 Linux
/dev/sda2              64,260     1,124,549     1,060,290  82 Linux swap / Solaris
/dev/sda3           1,124,611   840,006,719   838,882,109   5 Extended
/dev/sda5           1,124,613   168,907,409   167,782,797  83 Linux
/dev/sda6         168,907,473   336,690,269   167,782,797  83 Linux
/dev/sda7         336,690,333   840,006,719   503,316,387  83 Linux
/dev/sda4    *         32,130        64,259        32,130  83 Linux


Drive: sdb ___________________ _____________________________________________________
...

Drive: sdd ___________________ _____________________________________________________
...

Drive: sde ___________________ _____________________________________________________
...

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

...
/dev/sda1        c46991e0-1a3f-4d07-b6fb-ad0f3f7a42c8   ext2                                     
/dev/sda2        d200d323-311b-4b8f-86b3-16e45328cbdd   swap                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        d09fafc2-2b67-48d0-a8e0-000e142e5d57   ext2                                     
/dev/sda5        88807df0-58bf-4578-a380-38eea39f3f0b   ext3                                     
/dev/sda6        854bb77f-e5ef-4c13-b2ac-262c4dd2242b   ext3                                     
/dev/sda7        252ab6c4-cdd8-4690-8216-a7aab7ff13e5   ext3                                     
/dev/sda: PTTYPE="dos" 
...

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,noatime)
/dev/sda1        /boot                    ext2       (rw,noatime)
/dev/sda7        /media                   ext3       (rw)


========================== sda1/boot/grub/grub.conf: ==========================
...

============================= sda1/grub/grub.conf: =============================
...

=================== sda1: Location of files loaded by Grub: ===================
...

=============================== sda5/etc/fstab: ===============================
...

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
UUID=854bb77f-e5ef-4c13-b2ac-262c4dd2242b /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda4 during installation
UUID=d09fafc2-2b67-48d0-a8e0-000e142e5d57 /boot           ext2    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=d200d323-311b-4b8f-86b3-16e45328cbdd none            swap    sw              0       0

============================= sda4/grub/grub.cfg: =============================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 854bb77f-e5ef-4c13-b2ac-262c4dd2242b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set d09fafc2-2b67-48d0-a8e0-000e142e5d57
set locale_dir=($root)/grub/locale
set lang=sv
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
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set d09fafc2-2b67-48d0-a8e0-000e142e5d57
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda6 ro   quiet splash
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set d09fafc2-2b67-48d0-a8e0-000e142e5d57
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=/dev/sda6 ro single 
    echo    'Loading initial ramdisk ...'
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set d09fafc2-2b67-48d0-a8e0-000e142e5d57
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set d09fafc2-2b67-48d0-a8e0-000e142e5d57
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Gentoo Base System release 1.12.14 (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c46991e0-1a3f-4d07-b6fb-ad0f3f7a42c8
    linux /kernel-2.6.36-gentoo-r5 root=/dev/sda5
}
menuentry "Dell Utility Partition (on /dev/sdb1)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 07d6-0201
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 985c46cc5c46a53a
    drivemap -s (hd0) ${root}
    chainloader +1
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

=================== sda4: Location of files loaded by Grub: ===================

    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: vmlinuz-2.6.35-22-generic

================================ sdb2/boot.ini: ================================
...

================================ sdb2/BOOT.INI: ================================
...

=========================== Unknown MBRs/Boot Sectors/etc =======================
...

=======Devices which don't seem to have a corresponding hard drive==============

hda sdc 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdd1: Filen eller katalogen finns inte
hexdump: stdin: Felaktig filidentifierare.
hexdump: /dev/sdd1: Filen eller katalogen finns inte
hexdump: /dev/sdd1: Felaktig filidentifierare
hexdump: /dev/sde1: Filen eller katalogen finns inte
hexdump: stdin: Felaktig filidentifierare.
hexdump: /dev/sde1: Filen eller katalogen finns inte
hexdump: /dev/sde1: Felaktig filidentifierare
  No volume groups found

```

---

### Post by Hedgehog1 on 2011-04-25
Based on these entries ([COLOR="red"]**in red**[/COLOR]) your system appears to be using the Grub2 partition numbering:

```
menuentry "Dell Utility Partition (on **[COLOR="Red"]/dev/sdb1[/COLOR]**)" {
    insmod part_msdos
    insmod fat
    set root='([COLOR="red"]**hd1,msdos1**[/COLOR])'
    search --no-floppy --fs-uuid --set 07d6-0201
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on **[COLOR="red"]/dev/sdb2[/COLOR]**)" {
    insmod part_msdos
    insmod ntfs
    set root='(**[COLOR="red"]hd1,msdos2[/COLOR]**)'
    search --no-floppy --fs-uuid --set 985c46cc5c46a53a
    drivemap -s (hd0) ${root}
    chainloader +1
}
```

I see the '/boot' partition has it's UUID referenced:

```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(**[COLOR="red"]hd0,msdos4[/COLOR]**)'
    search --no-floppy --fs-uuid --set **[COLOR="Red"]d09fafc2-2b67-48d0-a8e0-000e142e5d57[/COLOR]**
    linux    /vmlinuz-2.6.35-22-generic root=**[COLOR="red"]/dev/sda6[/COLOR]** ro   quiet splash
```

But no UUID reference to '/' (root) partition.

Right now I am thinking that the separate '/boot' partition might not be your friend in this particular case.

**Could you try installing Ubuntu with just the '/' and swap partitions only (no separate '/boot' partition), please?** 

I have seen a small number of installs where the separate '/boot' partition is causing more problems that it solves; yours may be one...


***The Hedge***

:KS

---

### Post by Lovegain on 2011-04-28
> **Hedgehog1 said:**
> Could you try installing Ubuntu with just the '/' and swap partitions only (no separate '/boot' partition), please?
This worked. It's a shame that the installer is unable to handle that type of setup, though.

Anyway I'm content in my case. Thanks!

---

