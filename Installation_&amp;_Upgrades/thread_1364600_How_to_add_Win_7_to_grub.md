---
title: "How to add Win 7 to grub"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Hashimi on 2009-12-26
Hi

I recently download and compile the latest kernel (To learn how to), and unfortunately i lost the Windows 7 option from my grub. I can't enter win 7 now.

This is the result for : sudo fdisk -lu

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28da28da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   156512255    78255104    7  HPFS/NTFS
/dev/sda2       156521295   220845554    32162130    5  Extended
/dev/sda3   *   220846232   312576006    45864887+   7  HPFS/NTFS
/dev/sda5       156521358   212684534    28081588+  83  Linux
/dev/sda6       212684598   220845554     4080478+  82  Linux swap / Solaris


```

I search for this issue, and do the same steps expressed here: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

But still i have the error: "Bootmanager is missing. Please ctrl+alt+del to restart"

Not: I am not using Grub 2. it is something 1.x


Thanks for help

---

### Post by nerdtron on 2009-12-26
Try booting from your Windlose 7 CD and then choose Repair and the first option will be Repair Startup or Boot Process. This will restore your Win7 boot loader and you will be able to boot it up.

Now on Win7 desktop try installing GRUB.
Hmmm..I'm not 100% sure about this though... But give it a try and let's see

---

### Post by Hashimi on 2009-12-26
Thanks for the solution, but currently i don't have Win 7 CD or DVD. Is there any alternative ways to solve this problem through Ubuntu? 

Thanks

---

### Post by Hashimi on 2009-12-26
Any alternative Solutions?

---

### Post by nerdtron on 2009-12-26
0oops...sorry, again I'm not quite sure about this but you can go to Microsoft website and search if there are tools to recover the Win7 bootloader

---

### Post by Hashimi on 2009-12-26
I can't enter to windows to test any solutions microsoft provided to solve my problem. I need any solutions in Linux(Ubuntu).

---

### Post by erfahren on 2009-12-26
> **Hashimi said:**
> Thanks for the solution, but currently i don't have Win 7 CD or DVD. Is there any alternative ways to solve this problem through Ubuntu? 

Thanks
you can get a Win7 System Recovery Disc from here:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I have instructions somewhere on how to use it to repair the MBR but I have to find them - I'll post again here with them

---

### Post by erfahren on 2009-12-26
ok - try instructions here:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

good luck

---

### Post by Hashimi on 2009-12-26
I am still waiting for any solutions in Linux part.

Thanks

---

### Post by SecretCode on 2009-12-26
In your linux install (not a live cd), give the output of 
```
grub-install -v
```

If it's 1.97... then you do in fact have Grub2. If it's not, ignore the rest of this post!

When you boot the computer do you get a Grub menu, but without a Win7 entry? Or do you not get a boot menu at all?

If you don't get a menu:
```
sudo grub-install --recheck /dev/sda
```

Then, or if you already get a boot menu:
```
sudo update-grub
```
- This **should** scan your other partitions and detect the installation on sda1/sda3.

(What is on /dev/sda1 by the way? It's not marked as bootable.)

Post the output of all of these commands.

---

### Post by presence1960 on 2009-12-26
If SecretCode's advice does not work then...Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Hashimi on 2009-12-26
SecretCode; Yeah it is Grub2;

I did use that code: sudo update grub2; but no change. it automatically don't see any Win 7 and don't update it as i want (add win 7).

---

### Post by Hashimi on 2009-12-26
Presence1960; This the result.txt as you want:

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28da28da

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   156,512,255   156,510,208   7 HPFS/NTFS
/dev/sda2         156,521,295   220,845,554    64,324,260   5 Extended
/dev/sda5         156,521,358   212,684,534    56,163,177  83 Linux
/dev/sda6         212,684,598   220,845,554     8,160,957  82 Linux swap / Solaris
/dev/sda3    *    220,846,232   312,576,006    91,729,775   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A64461184460EC8D" TYPE="ntfs" 
/dev/sda3: UUID="01CA799C82FDA340" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda5: UUID="15afb7fe-e3d5-4789-88d2-37358b66a725" TYPE="ext4" 
/dev/sda6: UUID="f473e134-5f8b-4c8f-a06e-9e1e305ba5be" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hashimi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hashimi)


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
search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

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
UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f473e134-5f8b-4c8f-a06e-9e1e305ba5be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.1GB: boot/grub/grub.cfg
  80.1GB: boot/initrd.img-2.6.31-14-generic
  80.1GB: boot/initrd.img-2.6.31-16-generic
  80.1GB: boot/vmlinuz-2.6.31-14-generic
  80.1GB: boot/vmlinuz-2.6.31-16-generic
  80.1GB: initrd.img
  80.1GB: initrd.img.old
  80.1GB: vmlinuz
  80.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by presence1960 on 2009-12-26
> **Hashimi said:**
> Presence1960; This the result.txt as you want:

```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR="Red"]Boot files/dirs:   /Windows/System32/winload.exe[/COLOR]

sda2: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28da28da

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   156,512,255   156,510,208   7 HPFS/NTFS
/dev/sda2         156,521,295   220,845,554    64,324,260   5 Extended
/dev/sda5         156,521,358   212,684,534    56,163,177  83 Linux
/dev/sda6         212,684,598   220,845,554     8,160,957  82 Linux swap / Solaris
/dev/sda3    *    220,846,232   312,576,006    91,729,775   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="A64461184460EC8D" TYPE="ntfs" 
/dev/sda3: UUID="01CA799C82FDA340" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda5: UUID="15afb7fe-e3d5-4789-88d2-37358b66a725" TYPE="ext4" 
/dev/sda6: UUID="f473e134-5f8b-4c8f-a06e-9e1e305ba5be" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hashimi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hashimi)


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
search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 15afb7fe-e3d5-4789-88d2-37358b66a725
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

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
UUID=15afb7fe-e3d5-4789-88d2-37358b66a725 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f473e134-5f8b-4c8f-a06e-9e1e305ba5be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  80.1GB: boot/grub/grub.cfg
  80.1GB: boot/initrd.img-2.6.31-14-generic
  80.1GB: boot/initrd.img-2.6.31-16-generic
  80.1GB: boot/vmlinuz-2.6.31-14-generic
  80.1GB: boot/vmlinuz-2.6.31-16-generic
  80.1GB: initrd.img
  80.1GB: initrd.img.old
  80.1GB: vmlinuz
  80.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

You are missing boot files for windows 7, all are not present there. (See red above in your script results). Since they are missing GRUB will not recognize the installation, which is moot because without them windows 7 will not boot. You are going to have to download that windows 7 recovery iso from the link provided to neosmart. Burn the iso as an image to CD and boot from it. Follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for restoring windows 7 bootloader. Reboot and make sure windows boots. Then you will have to restore GRUB.

---

### Post by Hashimi on 2009-12-26
presence1960; Thanks. I will try those links and will write the result here.

I did not know the errors are from Win 7.

Thanks

---

### Post by kansasnoob on 2009-12-26
**Just thinking out loud here.** I'm curious what Presence1960 will think, so please be patient, but maybe you can provide a little info about your installation. 

Here I see a boot flag on sda3:

```
/dev/sda1               2,048   156,512,255   156,510,208   7 HPFS/NTFS
/dev/sda2         156,521,295   220,845,554    64,324,260   5 Extended
/dev/sda5         156,521,358   212,684,534    56,163,177  83 Linux
/dev/sda6         212,684,598   220,845,554     8,160,957  82 Linux swap / Solaris
/dev/sda3    *    220,846,232   312,576,006    91,729,775   7 HPFS/NTFS
```

But here no boot files:

```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```

OTOH sda1 is another story:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
```

And of course with the boot flag set on sda3 grub is trying to boot it:

```
### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###
```

So I'm just wondering **(just thinking out loud)** what would happen if the boot flag was removed from sda3 and a new boot flag placed on sda1 and then try to run "sudo update-grub" again :confused:

Edit: I see presence1960 beat me to the punch and I trust their judgment over my own.

---

### Post by meierfra. on 2009-12-26
> You are missing boot files for windows 7.
I agree.


> Follow the instructions here for restoring windows 7 bootloader. 
Those instructions are for fixing  the MBR and   the boot sector. But your MBR and bootsector are just fine. So this will not help you. To restore your boot files, see  Step 2 in this tutorial:

[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4]("http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4")

---

### Post by presence1960 on 2009-12-26
> **kansasnoob said:**
> **Just thinking out loud here.** I'm curious what Presence1960 will think, so please be patient, but maybe you can provide a little info about your installation. 

Here I see a boot flag on sda3:

```
/dev/sda1               2,048   156,512,255   156,510,208   7 HPFS/NTFS
/dev/sda2         156,521,295   220,845,554    64,324,260   5 Extended
/dev/sda5         156,521,358   212,684,534    56,163,177  83 Linux
/dev/sda6         212,684,598   220,845,554     8,160,957  82 Linux swap / Solaris
/dev/sda3    *    220,846,232   312,576,006    91,729,775   7 HPFS/NTFS
```

But here no boot files:

```
sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```

OTOH sda1 is another story:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe
```

And of course with the boot flag set on sda3 grub is trying to boot it:

```
### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###
```

So I'm just wondering **(just thinking out loud)** what would happen if the boot flag was removed from sda3 and a new boot flag placed on sda1 and then try to run "sudo update-grub" again :confused:

**_Edit: I see presence1960 beat me to the punch and I trust their judgment over my own._**

I am as fallible as the next person. I linked an incorrect procedure while someone else had the correct one linked earlier. I think sda1 was the win 7 install but is now missing BCD. I say that because it has some but not all boot files. If that is true the boot flag should be on sda1.
Neither sda1 nor sda3 is a "System Reserved" partition because they are both way too big for that. I would follow meierfra's advice as I am familiar with his expertise in windows as well as linux.

P.S. Thanks for the link meierfra, I bookmarked that one. When I get some free time this week I am going to install Vista OEM, then remove some boot files and try that how to so I can learn and become a little familiar with that procedure.

---

### Post by meierfra. on 2009-12-27
> what would happen if the boot flag was removed from sda3 
Would not make a difference. Grub ignores the boot flags, it only   looks for the boot files.

> I think sda1 was the win 7 install but is now missing BCD. I say that because it has some but not all boot files. 

winload.exe is always  on the same partition as the operating system. So /dev/sda1 is definitely the location of the OS. But  the other boot files (bootmgr and BCD/) can   be on a different partition.  And since the other boot files are missing, I would expect that they were on a now deleted partition. But that's just a guess.


> I am still waiting for any solutions in Linux part.

Downloading  a Vista/Win 7 recovery DVD and following the instruction linked by erfahren or (the essentially equivalent once) linked  by me, is really your best option. You could  get away with just downloading the boot files and copying them to your Windows partition, but I don't recommend that.

---

### Post by Hashimi on 2009-12-28
Thanks everyone;

I just burn the recovery cd it automatically fix errors and ask me for restart. I did that but the problem was still there, so in second time, i select the operating system and do the option (i think it was) Fix for errors . 

After the step above, i lost Ubuntu grub and i was automatically in to my Win 7.

At this part, i follow instructions written here: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) via my Bootable USB (Ubuntu Os inside).

I execute this command on conosle: sudo update-grub2  and win 7 was successfully added.

---

