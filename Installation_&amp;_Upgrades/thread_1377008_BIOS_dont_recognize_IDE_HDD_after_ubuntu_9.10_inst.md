---
title: "BIOS dont recognize IDE HDD after ubuntu 9.10 install"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by chrinux on 2010-01-09
First my english is no perfect but is like 90% good.

Hi, I am an average user of linux, ubuntu is the only distro i have tried and i loved it a lot, its so cool that I decided my sister to try it (she was using a Windows XP with viruses and that stuff, so she want me to help her). 

Initially her pc had only a 80 GB SATA HDD, then I installed a 80GB IDE HDD from a useless machine.

this IDE 80GB is an: ATA HDS728080PLAT20, configured as Slave (I have a DVD IDE Drive as Master).

The installation of the HDD was ok, since BIOS recognized as HDS728080PLAT20, the jumper configuration was also ok. Before Erasing all data, this IDE HDD had windows XP installed, and it was working alright; I could acess its data from my sister's windows xp.

Ok so I proceed to install ubuntu in the entire IDE Drive, and the installation was ok, rebooted and ubuntu 9.10 worked. But then i turned off completely the machine, then  waited 30 secs (is that a right word? jeje past of wait?) and turned on; and surprise!, not grub boot loader, just windows xp (yes, I have my BIOS configured so that it boots the IDE HDD first then the SATA HDD).

I checked in the BIOS and the IDE HDD was detected but not anymore as:

<ATA HDS728080PLAT20>

but as:

<>

I booted from ubuntu live CD, and ubuntu and gparted recognized well, as it should be, even the installation data on the IDE HDD was there.

Then I tried installing Windows 7 on that IDE HDD, just for see what happens, but windows did not recognize the IDE HDD (after the first install of ubuntu I erased everything again and leave the entire IDE HDD with unalocated memory, that is how i tried the windows installation). 

Also i disconected the SATA HDD, and when turned on the machine, BIOS loaded, but no GRUB boot loader. 

I have made two installations of ubuntu on that HDD and no results, even I updated my BIOS and no results. What could be?

Please help me, I don't know what to do, i suspect that gparted or the ubuntu installation erased some data that would make the HDD recognized by the BIOS and Windows.

---

### Post by chrinux on 2010-01-09
I forgot to mention that the motherboard is an Intel D946GZIS.

---

### Post by presence1960 on 2010-01-09
> **chrinux said:**
> I forgot to mention that the motherboard is an Intel D946GZIS.

If you installed Ubuntu on the 80 GB slave you may need to make it Master for GRUB to take over at boot.

Why don't you do this so we can see what exactly you have on that rig:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chrinux on 2010-01-11
I already tried setting the IDE HDD as Master, same results, BIOS identified it as <> rather than <ATA HDS728080PLAT20>.

thanks for the tool, here is the info i got from it

```


============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01340134

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   154,882,664   154,882,602  83 Linux
/dev/sda2         154,882,665   160,826,714     5,944,050   5 Extended
/dev/sda5         154,882,728   160,826,714     5,943,987  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d3c0d3b

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="8b8c58c6-d391-46de-9871-cc7cd7053ef6" TYPE="ext4" 
sda5: UUID="a1a60e60-2228-4321-9e30-5970f174c6b4" TYPE="swap" 
sdb1: UUID="18F04B27F04B0A88" TYPE="ntfs" 

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
search --no-floppy --fs-uuid --set 8b8c58c6-d391-46de-9871-cc7cd7053ef6
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
    search --no-floppy --fs-uuid --set 8b8c58c6-d391-46de-9871-cc7cd7053ef6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8b8c58c6-d391-46de-9871-cc7cd7053ef6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8b8c58c6-d391-46de-9871-cc7cd7053ef6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=8b8c58c6-d391-46de-9871-cc7cd7053ef6 ro single 
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
UUID=8b8c58c6-d391-46de-9871-cc7cd7053ef6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a1a60e60-2228-4321-9e30-5970f174c6b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

---

### Post by chrinux on 2010-01-11
what could be the problem?

:(

---

### Post by presence1960 on 2010-01-11
> **chrinux said:**
> what could be the problem?

:(

It sounds like a hardware problem or a BIOS problem. Here is a [link]("http://www.intel.com/support/motherboards/desktop/d946gzis/sb/CS-022973.htm") for the manual for that mobo.

This caught my eye in the manual:
```

Serial ATA and IDE Auto Configuration
If you install a Serial ATA or IDE device (such as a hard drive) in your computer, the
auto-configuration utility in the BIOS automatically detects and configures the device
for your computer. You do not need to run the BIOS Setup program after installing a
Serial ATA or IDE device. You can override the auto-configuration options by
specifying manual configuration in the BIOS Setup program.
```

Try that (manual config) from BIOS, or maybe updating the BIOS. It is definitely a hardware/BIOS issue not a software (ubuntu/windows) issue

---

### Post by chrinux on 2010-01-12
Sorry, I didn't realize about other jumper Master config. apparently there are 2 Master jumper options on the IDE HDD, and only tested one. Tried the other one and finally it worked. 

Thanks for everything! :)

---

### Post by presence1960 on 2010-01-12
> **chrinux said:**
> Sorry, I didn't realize about other jumper Master config. apparently there are 2 Master jumper options on the IDE HDD, and only tested one. Tried the other one and finally it worked. 

Thanks for everything! :)
Glad you got it working. Enjoy ubuntu!

---

