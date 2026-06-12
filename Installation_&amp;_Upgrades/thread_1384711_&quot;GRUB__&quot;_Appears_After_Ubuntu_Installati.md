---
title: "&quot;GRUB _&quot; Appears After Ubuntu Installation"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by curtissthompson on 2010-01-18
I just did installed Ubuntu 9.10 (AMD 64-bit) on a new computer I built. (It was installed to a brand new Velociraptor hard drive, that had not been used prior to this.)  Upon completing the installation process, I was prompted to restart my PC to start using Ubuntu.  After doing so, I was met with a black screen displaying "GRUB _"

I've seen threads for this problem on this forum among others, but they were all from users who were dealing with dual boot setups and on hard drives which already had an OS installed to it.  Also, those threads didn't seem to have any clear solution to the problem.

Any help would be greatly appreciated!

---

### Post by phillw on 2010-01-18
Hi, and welcome to the forums.

Hmm, well, the thread is --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Start with #11 to see if you can get to recovery mode, if so go to #15

If not, head to #13 and do a re-install of grub.

Should sort you, either way.

Regards,

Phill.

---

### Post by presence1960 on 2010-01-18
Need a little more info please. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by curtissthompson on 2010-01-19
I tried that to no avail. However, in talking with a friend I've come to think I may have the issue mentioned in this post:
[http://ubuntuforums.org/showpost.php?p=2144471&postcount=10](http://ubuntuforums.org/showpost.php?p=2144471&postcount=10)
Where the bootloader was put on a different hard drive than the installation, as I have 3 SATA hard drives hooked up in this PC.

The hard drive I want to be my OS hard drive is listed as SCSI3 when I selected the hard drive to install Ubuntu to in the installation setup process.  SCSI1 and SCSI2 are hard drives I'm using for storage.  When I go to Advanced Options for bootloader setting at the end of the installation setup process, I've been using the default "(hd0)" which has resulted in the above mentioned problem.

My other options, besides (hd0), in the drop down menu are:
/dev/sda     ATA ST31500341AS (1.4 TB)
/dev/sda-1
/dev/sdb    ATA ST3320620AS (298.1 GB)
/dev/sdb1
/dev/sdc    ATA WDC WD1500HLFS-0 (139.7 GB)
/dev/sdc1

The 139.7 GB hard drive is my Velociraptor Hard Drive that I want to install the bootloader and operating system to.  I have no intentions of installing windows on this machine, or any other operating system for that matter.

Am I correct in my assumption? Also, what does (hd0) represent, and should I select /dev/sdc or /dev/sdc1 for the bootloader instead?

---

### Post by curtissthompson on 2010-01-19
Also here's the results of the sudo fdisk -l command if it helps:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08a4e506

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e62ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       17495   140528556   83  Linux
/dev/sdc2           17496       18241     5992245    5  Extended
/dev/sdc5           17496       18241     5992213+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by presence1960 on 2010-01-19
Run the script I asked in post #3 and post the results so we can see where your bootloader(s) is. 

If you can't figure out how to run it then do this: 
1. Download the script from the link in my signature line.
2. Once downloaded move the script file to Desktop
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
4. This will create a RESULTS.txt file on the Desktop
5. Open that file and copy/paste the entire contents back here

If you do this we will definitely see what you have and what the problem is rather than guessing or thinking in relation to your bootloader(s). Your choice: have something definitive or continue to guess.

The output from fdisk by itself does not show us the info necesaary to troubleshoot your issue.

---

### Post by curtissthompson on 2010-01-19
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks at sector 1110695 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sdc and looks for 
    (UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08a4e506

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e62ed

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   281,057,174   281,057,112  83 Linux
/dev/sdc2         281,057,175   293,041,664    11,984,490   5 Extended
/dev/sdc5         281,057,238   293,041,664    11,984,427  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="A49474D89474AE84" LABEL="Numero Dos" TYPE="ntfs" 
/dev/sdc1: UUID="6f2b1ef3-87c8-47c0-aeb5-d122d769c94b" TYPE="ext4" 
/dev/sdc5: UUID="40151307-dd8b-4f1c-b62b-c0bad8fb331c" TYPE="swap" 

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


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
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
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=40151307-dd8b-4f1c-b62b-c0bad8fb331c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by presence1960 on 2010-01-19
You want to do a few things. You want to put sdc (150 GB) disk as first in the hard disk boot order in BIOS, save changes to CMOS and continue booting the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdc1 /mnt
```
This will mount your root partition. 

Next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```
This will put GRUB on the MBR of the sdc (150 GB) disk. reboot without the Live CD and boot into Ubuntu.

You now have one more step to do so any grub-pc updates go to MBR of sdc and not sda. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```

In the last window choose sdc. This will insure all your GRUB2 (grub-pc) updates get installed to MBR of sdc.

---

### Post by curtissthompson on 2010-01-21
Sorry forgot to respond, got distracted by some ATI driver issues. Thanks a lot for all the help, it worked perfectly!

---

### Post by presence1960 on 2010-01-21
> **curtissthompson said:**
> Sorry forgot to respond, got distracted by some ATI driver issues. Thanks a lot for all the help, it worked perfectly!

Glad you got it working, enjoy Ubuntu!

---

### Post by curtissthompson on 2010-03-19
I was recently trying to fix a Hyper Transport Sync Flood error as described [here]("http://forums.amd.com/forum/messageview.cfm?FTVAR_FORUMVIEWTMP=Threaded&catid=22&threadid=88140"), only difference being I encountered the issue at each startup after installing some Ubuntu updates, including linux kernel 2.6.31-20 which required a reboot.  It prevented me from successfully booting into the OS.

Anyway, I tried several recommendations such as manually setting voltage and frequency settings for my memory, and eventually decided to try resetting the BIOS to default settings to try and resolve the issue.  Upon rebooting I came across the same "GRUB _" issue at boot that I had months before, which you helped me resolve.

I used the same script you had me use last time to generate a RESULTS.txt file about the boot process.  I not yet familiar enough with Ubuntu Linux to be able to understand everything in the text file and was wondering if you could help explain how to fix this?  I wasn't aware BIOS settings could affect the OS in this way (other than say boot order).

```
RESULTS.txt is posted below:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 1110695 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08a4e506

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e62ed

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   281,057,174   281,057,112  83 Linux
/dev/sdc2         281,057,175   293,041,664    11,984,490   5 Extended
/dev/sdc5         281,057,238   293,041,664    11,984,427  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        A49474D89474AE84                       ntfs       Numero Dos                    
/dev/sdc1        6f2b1ef3-87c8-47c0-aeb5-d122d769c94b   ext4                                     
/dev/sdc5        40151307-dd8b-4f1c-b62b-c0bad8fb331c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=40151307-dd8b-4f1c-b62b-c0bad8fb331c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
   7.7GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.3GB: boot/initrd.img-2.6.31-17-generic
   5.9GB: boot/initrd.img-2.6.31-19-generic
   8.6GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-17-generic
   4.1GB: boot/vmlinuz-2.6.31-19-generic
   2.2GB: boot/vmlinuz-2.6.31-20-generic
   8.6GB: initrd.img
   5.9GB: initrd.img.old
   2.2GB: vmlinuz
   4.1GB: vmlinuz.old

```

---

