---
title: "blank screen fresh install on boot (not i915 problem)"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by jlintz on 2010-01-09
Hi,

So I currently have an install of Karmic running that has been upgraded over the years but I am repartitioning my drives so I did a fresh install on a new drive.

My first problem was the live cd would not boot and I had to use the alternate cd to do the install.  It would boot into a blank screen and the i915.modeset=0 kernel parameter did not help.

After the installation finished I went to try and boot and found that right when it went to initialize the graphics, my computer locked up hard.  Keyboard unresponsive and all.  I read the forums and I tried using the kernel parameter i915.modeset=0 and removed quiet and splash from the kernel line to see if I could spot any errors but nothing appeared.  

I am able to boot into recovery mode, and I tried even running an apt-get upgrade to get all my packages up to date and installed the latest nvidia driver but still have this issue.  

I'm at a loss as to what I should attempt next.

Any help would be appreciated

here is boot info, just to clarify sda and sdb are a fakeraid on my old setup, sdc is my new install

============================= Boot Info Summary: ==============================

 => Grub  is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #3 for /grub/stage2 and /grub/menu.lst.
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x146f146f

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   160,151,984    78,236,550   f W95 Ext d (LBA)
/dev/sda5          81,915,498   158,224,184    76,308,687  83 Linux
/dev/sda6         158,224,248   160,151,984     1,927,737  82 Linux swap / Solaris
/dev/sda3         160,156,250   160,351,562       195,313  83 Linux
/dev/sda4         160,360,830   625,137,344   464,776,515   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x146f146f

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   160,151,984    78,236,550   f W95 Ext d (LBA)
/dev/sdb5          81,915,498   158,224,184    76,308,687  83 Linux
/dev/sdb6         158,224,248   160,151,984     1,927,737  82 Linux swap / Solaris
/dev/sdb3         160,156,250   160,351,562       195,313  83 Linux
/dev/sdb4         160,360,830   625,137,344   464,776,515   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c8e40

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   163,846,934   163,846,872  83 Linux
/dev/sdc2         163,846,935   180,233,234    16,386,300  82 Linux swap / Solaris
/dev/sdc3         180,234,240   344,078,335   163,844,096   7 HPFS/NTFS
/dev/sdc4         344,080,170 1,953,520,064 1,609,439,895  83 Linux


blkid -c /dev/null: ____________________________________________________________

sdc1: UUID="05e0538c-8998-440c-a5a6-20851cdf38ce" TYPE="ext4" 
sdc3: UUID="B26453C0645385CF" TYPE="ntfs" 
sdc4: LABEL="linux-storage" UUID="cd93d1dd-735f-46b5-95cf-20a090798029" TYPE="ext4" 

=============================== "mount" output: ===============================

/dev/sdc1 on / type ext4 (rw,errors=remount-ro)
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
search --no-floppy --fs-uuid --set 05e0538c-8998-440c-a5a6-20851cdf38ce
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
	search --no-floppy --fs-uuid --set 05e0538c-8998-440c-a5a6-20851cdf38ce
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=05e0538c-8998-440c-a5a6-20851cdf38ce ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 05e0538c-8998-440c-a5a6-20851cdf38ce
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=05e0538c-8998-440c-a5a6-20851cdf38ce ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdc3)" {
	insmod ntfs
	set root=(hd2,3)
	search --no-floppy --fs-uuid --set b26453c0645385cf
	chainloader +1
}
menuentry "Windows XP Professional x64 Edition (on /dev/mapper/nvidia_ajafeffc1)" {
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.31-16-generic root=/dev/mapper/nvidia_ajafeffc5 ro quiet splash
	initrd /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.31-16-generic root=/dev/mapper/nvidia_ajafeffc5 ro single
	initrd /initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.31-14-generic root=/dev/mapper/nvidia_ajafeffc5 ro quiet splash
	initrd /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.31-14-generic root=/dev/mapper/nvidia_ajafeffc5 ro single
	initrd /initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.28-16-generic root=/dev/mapper/nvidia_ajafeffc5 ro quiet splash
	initrd /initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode) (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /vmlinuz-2.6.28-16-generic root=/dev/mapper/nvidia_ajafeffc5 ro single
	initrd /initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/mapper/nvidia_ajafeffc5)" {
	linux /memtest86+.bin 
}
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
UUID=05e0538c-8998-440c-a5a6-20851cdf38ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
#UUID=b2ef4754-7dcd-4c66-9897-f97b78830c75 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sda6


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb5


Unknown BootLoader  on sdb6


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory

---

### Post by jlintz on 2010-01-10
I was able to get this working, unfortunately  I'm not sure which fixed it as I didnt approach the problem with the scientific method....

In rescue mode I removed the nv driver, ati driver, and intel drivers from xorg, I also did a dpkg-reconfigure xserver-xorg.  One of those did the trick and I was then able to boot.  Hope this helps someone else with the problem.

---

