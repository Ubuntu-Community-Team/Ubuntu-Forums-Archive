---
title: "Help just installed ubuntu"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Parachutee on 2009-12-23
I just installed Ubuntu. I erased the drive and deleted the Windows xp I had on it before. After I install the Ubuntu, I can't get it to boot up from the hard drive. I get a error message that says " loading Grub, error 57081d47-3977-4177-bced-d5e5a397a5a4.. Failed to boot default entries". So can someone help me, oh yeah I am doing the install with a cd.

---

### Post by oakgrove on 2009-12-23
How many physical hard drives are in the machine?  How many were in there when you installed Ubuntu?  Did you install Ubuntu then delete Windows?  Did you make any changes at all after installing Ubuntu as far as removing, adding, formatting or otherwise changing drives around in any way?

---

### Post by Parachutee on 2009-12-23
i only had onto phsyicall hard drive and when i installed it i did ubuntu over the windows and erased it. then the computer rebooted the disc popped out. and i had to change it to boot from hard disc then i got that error.

---

### Post by oakgrove on 2009-12-23
Set it to boot from the CD first then the harddrive.  Go on ahead and reinstall.  Then when it's finished and the CD pops out, remove it.  Then go on ahead and restart and don't reset the boot order, just let it look for the CD and when it doesn't find it, it should go on and boot off of the drive.

---

### Post by Parachutee on 2009-12-23
okay i will try that, hopefully it works

---

### Post by presence1960 on 2009-12-23
> **Parachutee said:**
> okay i will try that, hopefully it works

Before reinstalling do this so we can get more info: Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Parachutee on 2009-12-24
its not recognizing the command, shoud i just keep trying it?

---

### Post by presence1960 on 2009-12-24
> **Parachutee said:**
> its not recognizing the command, shoud i just keep trying it?

after downloading the script from the link in my signature line move it to the desktop. Then open a terminal and run the command.

---

### Post by Parachutee on 2009-12-24
[FONT=monospace]============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,270,344   114,270,282  83 Linux
/dev/sda2         114,270,345   117,210,239     2,939,895   5 Extended
/dev/sda5         114,270,408   117,210,239     2,939,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e9b4c9e4-747e-44ee-beac-499c9f91019a" TYPE="ext4" 
/dev/sda5: UUID="82479d37-fe66-4875-a973-e74136e962c1" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)


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
search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a ro single 
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
UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=82479d37-fe66-4875-a973-e74136e962c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz[/FONT]

---

### Post by presence1960 on 2009-12-24
> **Parachutee said:**
> [FONT=monospace]============================= ```
Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   114,270,344   114,270,282  83 Linux
/dev/sda2         114,270,345   117,210,239     2,939,895   5 Extended
/dev/sda5         114,270,408   117,210,239     2,939,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="e9b4c9e4-747e-44ee-beac-499c9f91019a" TYPE="ext4" 
/dev/sda5: UUID="82479d37-fe66-4875-a973-e74136e962c1" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
[COLOR="Red"]/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)
/dev on /target/dev type none (rw,bind)[/COLOR]


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
search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set e9b4c9e4-747e-44ee-beac-499c9f91019a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a ro single 
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
UUID=e9b4c9e4-747e-44ee-beac-499c9f91019a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=82479d37-fe66-4875-a973-e74136e962c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz[/FONT]
```

Never seen the red above in the output before. You can try reinstalling GRUB2. Boot the Live CD, choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sda1 /mnt
```

Then in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and see if you can boot into Ubuntu.

---

### Post by Parachutee on 2009-12-24
i tried that and it didn't work, but it did give me different option to boot in ubuntu or ubuntu recovery mode. but when you click on them it doesn't work either. should i try reinstalling it again?

---

### Post by presence1960 on 2009-12-24
> **Parachutee said:**
> i tried that and it didn't work, but it did give me different option to boot in ubuntu or ubuntu recovery mode. but when you click on them it doesn't work either. should i try reinstalling it again?

something is not right and those lines in red in the script I have never seen before. That long string of numbers that flash with the message are a UUID of the device trying to boot. But if you look in the script under  blkid -c you will not see that UUID listed. So something probably went wrong during the installation. I suspect those /dev/target in red are the culprits and that is the UUID associated with that. 

I would reinstall.

---

### Post by presence1960 on 2009-12-24
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb7 and 
                       looks at sector 46409591 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #7 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4c62

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   488,392,064   488,392,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   125,837,144   125,837,082   5 Extended
/dev/sdb5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sdb6           8,385,993    46,138,679    37,752,687  83 Linux
/dev/sdb7          46,138,743    88,084,394    41,945,652  83 Linux
/dev/sdb2         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sdc2         104,856,255   230,693,399   125,837,145   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00052075

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63     2,104,514     2,104,452   b W95 FAT32
/dev/sdd2           2,104,515    12,594,959    10,490,445  83 Linux
/dev/sdd3          12,594,960   127,925,594   115,330,635  83 Linux
/dev/sdd4         127,925,595   160,071,659    32,146,065   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
/dev/sdb2: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
/dev/sdb6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
/dev/sdb7: LABEL="Sabayon_5.0" UUID="b9e8a529-266d-4dd2-b892-914893cee3a2" TYPE="ext4" 
/dev/sdc1: UUID="5B8A70BC5646AB94" LABEL="xp" TYPE="ntfs" 
/dev/sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 
/dev/sdd1: LABEL="karmic_live" UUID="1D77-97EB" TYPE="vfat" 
/dev/sdd2: LABEL="home-backup" UUID="6276ec90-ab7f-489d-a59c-23d24e8a02be" TYPE="ext3" 
/dev/sdd3: LABEL="data-backup" UUID="b9075f26-d1df-449a-82d9-ba6788b2aec1" TYPE="ext3" 
/dev/sdd4: UUID="14A9FF3772BA9EA9" LABEL="win_data-backup" TYPE="ntfs" 
[COLOR="Red"]
=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdd1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd2 on /media/home-backup type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd3 on /media/data-backup type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd4 on /media/win_data-backup type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit[/COLOR])


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sdb5 real_resume=/dev/sdb5
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sdb7)" {
	insmod ext2
	set root=(hd1,7)
	search --no-floppy --fs-uuid --set b9e8a529-266d-4dd2-b892-914893cee3a2
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sdb5 real_resume=/dev/sdb5 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 5b8a70bc5646ab94
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sdb6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-16-generic
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-16-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

========================== sdb7/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,6)
#          kernel /boot/kernel-genkernel real_root=/dev/sdb7
#          initrd /boot/initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sdb7
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd1,6)/boot/grub/splash.xpm.gz


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd1,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sdb5 real_resume=/dev/sdb5
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd1,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sdb7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sdb5 real_resume=/dev/sdb5 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefault

=============================== sdb7/etc/fstab: ===============================

/dev/sdb7               /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sdb7: Location of files loaded by Grub: ===================


  23.6GB: boot/grub/grub.conf
  23.6GB: boot/grub/menu.lst
  23.6GB: boot/grub/stage2

================================ sdc1/boot.ini: ================================

[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdc2/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdd4/boot.ini: ================================

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh 
```

Just to double check I booted off my 9.10 Live USB which is on an external disk and ran the script. Results are posted above. Just as I suspected from the Live CD my mount output does not contain the /dev/target that yours does. I believe that is left over from the install and now when you boot it is trying to mount that instead of your sda1 partition. I would reinstall.

---

### Post by Parachutee on 2009-12-25
That didn't work! Reinstalling it doesn't help. It wont even let me install any OS on it not even to but windows back! Something is seriously wrong here!

---

### Post by presence1960 on 2009-12-25
> **Parachutee said:**
> That didn't work! Reinstalling it doesn't help. It wont even let me install any OS on it not even to but windows back! Something is seriously wrong here!

Boot from the Live CD again, choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
gksu gparted
```

Delete every partition on your hard disk and leave it as unallocated space. Click the Apply button (green check mark) on the tool bar at top. When finished check the graphic and verify the whole disk is unallocated. Try installing an OS next.

Note: On the extended partition you must first delete the logical partition(s) inside the extended partition. Once the extended partition is only unallocated space you may then delete the extended partition.

If that does not work then I would think the problem is with BIOS or your optical drive not letting you boot off an installation CD/DVD.

---

### Post by Parachutee on 2009-12-25
I will try that in a little while and get back to you.

---

