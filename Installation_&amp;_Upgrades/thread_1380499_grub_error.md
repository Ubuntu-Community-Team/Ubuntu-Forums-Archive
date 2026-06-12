---
title: "grub error"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2010-01-13
sorry i know you see these a ton, but im not good enought to apply it to my situatuion.

Linux is successfully installed, but i do not get an option to pick vista.

Also i would like vista to be the default system. Thought it pains me it is necessary...


```


============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
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
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    31,569,919    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,569,920 1,254,201,344 1,222,631,425   7 HPFS/NTFS
/dev/sda4       1,254,210,615 1,465,144,064   210,933,450   5 Extended
/dev/sda5       1,254,210,678 1,296,381,239    42,170,562  83 Linux
/dev/sda6       1,296,381,303 1,454,589,359   158,208,057  83 Linux
/dev/sda7       1,454,589,423 1,465,144,064    10,554,642  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-021D" TYPE="vfat" 
/dev/sda2: UUID="F8C23922C238E712" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="D8FA3C07FA3BE104" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="76c58240-4834-4499-b222-c53717a842a0" TYPE="ext4" 
/dev/sda6: UUID="5b94d663-cf6a-4508-a145-ac1c7c013613" TYPE="ext3" 
/dev/sda7: UUID="a6501fdb-6896-48d2-9aa1-b2b92fd8a399" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/luke/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luke)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda3: Location of files loaded by Grub: ===================


  16.1GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=76c58240-4834-4499-b222-c53717a842a0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5b94d663-cf6a-4508-a145-ac1c7c013613 /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=a6501fdb-6896-48d2-9aa1-b2b92fd8a399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 642.1GB: boot/grub/core.img
 642.1GB: boot/grub/grub.cfg
 642.1GB: boot/initrd.img-2.6.31-14-generic
 642.1GB: boot/initrd.img-2.6.31-17-generic
 642.1GB: boot/vmlinuz-2.6.31-14-generic
 642.1GB: boot/vmlinuz-2.6.31-17-generic
 642.1GB: initrd.img
 642.1GB: initrd.img.old
 642.1GB: vmlinuz
 642.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 


```

---

### Post by Leppie on 2010-01-13
it looks like your os-prober script is either inactive or missing. was this a clean install?

---

### Post by darkod on 2010-01-13
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]

I don't know how it got there but this file is part of ubuntu boot, not vista boot files. Maybe because of this ubuntu can't "see" correctly the vista boot files.
Try simple test. Boot ubuntu, open this /dev/sda3 partition (in Places you can recognize it by the partition size) and move this file in your home folder for example.
Then in terminal execute:
sudo update-grub

Reboot and see if you have vista entry in the grub menu and whether you can boot it.

IMPORTANT: Not sure if the removal of this file can break your grub and make the machine unbootable. If it does, have the 9.10 cd at hand, boot with it and the Try Ubuntu option, find in Places your home folder (it won't be called home, find it by partition size) and put that file you moved back to the vista partition. The files on /dev/sda5 look normal and ubuntu should boot fine even with the mentioned file removed from /dev/sda3, but I can't know for sure because I don't know how it got there.
Anyway, using the live desktop you can always put the file back.

---

### Post by wlraider70 on 2010-01-13
I had formerly used wubi, and deleted it.
Today i shrunk my vista partition and add Ubuntu from a live CD.

---

### Post by darkod on 2010-01-13
> **wlraider70 said:**
> I had formerly used wubi, and deleted it.
Today i shrunk my vista partition and add Ubuntu from a live CD.

That might explain it, I'm not familiar with wubi. If you are willing to move that file you'll see if it's working without that file mixed with the vista boot files.

---

### Post by wlraider70 on 2010-01-13
i've tried a lot of changes and updates, but still nothing.

here is an updated results.

```
 ============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
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
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    31,569,919    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,569,920 1,254,201,344 1,222,631,425   7 HPFS/NTFS
/dev/sda4       1,254,210,615 1,465,144,064   210,933,450   5 Extended
/dev/sda5       1,254,210,678 1,296,381,239    42,170,562  83 Linux
/dev/sda6       1,296,381,303 1,454,589,359   158,208,057  83 Linux
/dev/sda7       1,454,589,423 1,465,144,064    10,554,642  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-021D" TYPE="vfat" 
/dev/sda2: UUID="F8C23922C238E712" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="D8FA3C07FA3BE104" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="76c58240-4834-4499-b222-c53717a842a0" TYPE="ext4" 
/dev/sda6: UUID="5b94d663-cf6a-4508-a145-ac1c7c013613" TYPE="ext3" 
/dev/sda7: UUID="a6501fdb-6896-48d2-9aa1-b2b92fd8a399" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/luke/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luke)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 76c58240-4834-4499-b222-c53717a842a0
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=76c58240-4834-4499-b222-c53717a842a0 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=76c58240-4834-4499-b222-c53717a842a0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5b94d663-cf6a-4508-a145-ac1c7c013613 /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=a6501fdb-6896-48d2-9aa1-b2b92fd8a399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 642.1GB: boot/grub/grub.cfg
 642.1GB: boot/initrd.img-2.6.31-14-generic
 642.1GB: boot/initrd.img-2.6.31-17-generic
 642.1GB: boot/vmlinuz-2.6.31-14-generic
 642.1GB: boot/vmlinuz-2.6.31-17-generic
 642.1GB: initrd.img
 642.1GB: initrd.img.old
 642.1GB: vmlinuz
 642.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 


```

there are some changed on this results.
i belive i removed the boot data that came from wubi.

Grub does load, it just seems to have clue about vista on part 3.

---

### Post by darkod on 2010-01-13
OK, this definitely won't work. Under sda3 boot files now you have only /bootmgr. vista needs also /boot/bcd and /windows/system32/winload.exe.

Grab a vista repair cd image from here:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Then read here about restoring vista boot process:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

That should repair the vista boot. Check if it's working fine. Vista should be booting directly.

After that you only need to repair the grub on the MBR, the instructions are on the same link. Just make sure you use 9.10 cd and instructions to repair grub2 if you are using 9.10, or instructions and cd for 9.04 if using grub1.

---

### Post by presence1960 on 2010-01-13
Just got your PM. Sorry but I was at my daughter's Tae Kwon Do. After seeing that you removed the Windows bootfiles if you can put them back if you didn't delete them. The only one to NOT replace is /boot/grub/core.img

If you deleted them I am not sure how to replace them from the Windows DVD but if meierfra is around he will know how to do it.

---

### Post by wlraider70 on 2010-01-14
i got it.

i took out a few too many windows boot files.
I had too c:/boot one with a cap B and 1 lower case. i combined them removed the core.img.
mounted the windows part and ran grub update.

ta da.


only remaining question is how do i make vista the default?


THANKS ALL

---

