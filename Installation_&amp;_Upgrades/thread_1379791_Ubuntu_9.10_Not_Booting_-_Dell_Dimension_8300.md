---
title: "Ubuntu 9.10 Not Booting - Dell Dimension 8300"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by coplinator on 2010-01-12
Hello, 

I'm new to Linux, last 6 months, and am trying to install it on my tower, but for some reason after successfully going through the installation process, it will not boot. I'm using ubuntu in a virtual box on my laptop just fine, I've had not problems at all, this really has me stumped since it seemed so easy on my laptop.

I get this message after the installation has finished and the computer has to restart, the cd tray opens, I remove the ubuntu cd I burned, and I get this message: 

[COLOR="Red"]Strike F1 to retry, Strike F2 to enter setup[/COLOR]

I put the CD back in, and then selected "Boot from Hard Disc", and then get a "Booting from local disk..." and the cursor blinking below, but after 2 minutes or so, I get the following error: 

[COLOR="Red"]isolinux: Disk error 80, AX=0201, drive 80[/COLOR]

Before installing Ubuntu, I did the hard drive test just to be sure, and there were no problems, it said everything was good to go.



Some specs, if they might help: 

Dell Dimension 8300 
20GB Hard Drive (IDE, jumpers set to factory positions, and the IDE 1 cable plugged in) 
1 GB Ram
Pentium 4 w/ Hyper-Threading



Please let me know if more information will help, I just don't know what else I should be doing.

---

### Post by presence1960 on 2010-01-12
If you believe you installed ubuntu successfully we need way more info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by coplinator on 2010-01-13
Hello, 

Thanks for your quick reply. Here is the information you requested, please let me know if you need anything else. 

```
============================= Boot Info Summary: ==============================

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

Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders, total 40088160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2fc8e8cf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    38,315,024    38,314,962  83 Linux
/dev/sda2          38,315,025    40,082,174     1,767,150   5 Extended
/dev/sda5          38,315,088    40,082,174     1,767,087  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="62e30271-cbc3-42df-9c1f-1a33c9c8b7c7" TYPE="ext4" 
/dev/sda5: UUID="2380e1b4-5301-4b8d-b883-faefc798f8be" TYPE="swap" 

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
search --no-floppy --fs-uuid --set 62e30271-cbc3-42df-9c1f-1a33c9c8b7c7
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
    search --no-floppy --fs-uuid --set 62e30271-cbc3-42df-9c1f-1a33c9c8b7c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=62e30271-cbc3-42df-9c1f-1a33c9c8b7c7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 62e30271-cbc3-42df-9c1f-1a33c9c8b7c7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=62e30271-cbc3-42df-9c1f-1a33c9c8b7c7 ro single 
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
UUID=62e30271-cbc3-42df-9c1f-1a33c9c8b7c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2380e1b4-5301-4b8d-b883-faefc798f8be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by presence1960 on 2010-01-13
From a software perspective Ubuntu is indeed installed to the hard disk and looks good. I would hit F2 and go into BIOS and check all your hardware settings to see that everything is OK. 

GRUB is installed to MBR and points to sda1 as it should. By those messages I think it is a hardware issue. Check it out and report back.

---

### Post by coplinator on 2010-01-13
When I got into the BIOS and look, is there anything I should be looking to change or notice? 

For instance, the hard drive, or ram? 

Just want to be sure I'm looking in the right places...

---

### Post by coplinator on 2010-01-14
I'm not sure what all will be helpful from the BIOS settings, so I'm going to give as much information as possible, without giving everything.
 
Intel Pentium 4 Processor: 3.00GHz
Level 2 Cache: 512 KB Integrated
BIOS Version: A07
Service Tag: D815H41
 
**Drive Configuration**
Sata Primary Drive - OFF
Sata Secondary Drive - OFF
Primary Master Drive - Hard Drive (Model: WDC WD205BA)
Primary Slave Drive - OFF
Secondary Master Drive - CD-ROM Device
Secondary SLave Drive - OFF
 
IDE Drive UDMA - On
 
**Memory Information**
Installed System Memory - 1024 MB DDR SDRAM
System Memory Speed - 400 MHz
System Memory Channel Mode - Single
AGP Aperature - 128 MB
 
**CPU Information**
Hyper-Threading - Disabled
CPU Speed - Normal (only other option is compatible)
Bus Speed - 800 MHz
Processor 0 ID - F29
Clock Speed - 3.00 GHz
L2 Cache Size - 512 KB
 
A couple other things that might be helpful: 
 
Auto Power On - Disabled
Fast Boot - On
OS Install Mode - OFF
IDE Hard Drive Acoustics Mode - Bypass (other options are: Quiet, Suggested, Performance)
 
The only other things that I did not include are the time, date, boot sequence, and integrated devices...etc
 
If you need any other information, please let me know.
 
Thanks for everything.

---

### Post by presence1960 on 2010-01-14
That is really strange everything seems OK in BIOS & the ubuntu install. I am at a loss to explain why it won't boot.

---

