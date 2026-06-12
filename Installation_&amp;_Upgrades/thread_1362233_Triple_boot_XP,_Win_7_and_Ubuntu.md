---
title: "Triple boot XP, Win 7 and Ubuntu"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Jello123 on 2009-12-22
I have XP and Win 7 installed on separate drives and thought I would try out linux again. I created a bootable USB stick with Ubuntu 9.10 on it and it boots fine. I have an external eSata drive that was formatted as NTFS (1 TB) that will be home to Ubuntu. Once booted from the stick and in Ubuntu, I installed it on the external drive, left everything as default, check marked to include the win 7 loader and it came up with the message that Ubuntu was installed sucessfully and I could continue testing or reboot. I reboot without the USB stick, set the external drive for first boot disk and no grub, just the Win 7 loader. Under windows I can see an unrecognized partition so I know it's there. I have an Asus P6T board and I'm sure it can boot from an eSata if it can boot from USB. Can anyone tell me what I'm missing from this jibberish?:lolflag:

---

### Post by presence1960 on 2009-12-22
> **Jello123 said:**
> I have XP and Win 7 installed on separate drives and thought I would try out linux again. I created a bootable USB stick with Ubuntu 9.10 on it and it boots fine. I have an external eSata drive that was formatted as NTFS (1 TB) that will be home to Ubuntu. Once booted from the stick and in Ubuntu, I installed it on the external drive, left everything as default, check marked to include the win 7 loader and it came up with the message that Ubuntu was installed sucessfully and I could continue testing or reboot. I reboot without the USB stick, set the external drive for first boot disk and no grub, just the Win 7 loader. Under windows I can see an unrecognized partition so I know it's there. I have an Asus P6T board and I'm sure it can boot from an eSata if it can boot from USB. Can anyone tell me what I'm missing from this jibberish?:lolflag:

You will have to check the mobo's documentation to see if you can boot from eSATA. In the meantime- Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jello123 on 2009-12-22
The bootable usb stick that I am using does not have that option   "try ubuntu without any changes", it just boots to the desktop with a Install icon and Examples folder.
Now when I click on install it says "This computer has Ubuntu 9.10 (9.10) on it." Before I installed it said there was no operating systems on it as I had set the external drive to the second boot device.
Your script just comes back with...
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

I have attached a screenshot.

Thank you in advance for your time.

---

### Post by presence1960 on 2009-12-22
> **Jello123 said:**
> The bootable usb stick that I am using does not have that option   "try ubuntu without any changes", it just boots to the desktop with a Install icon and Examples folder.
Now when I click on install it says "This computer has Ubuntu 9.10 (9.10) on it." Before I installed it said there was no operating systems on it as I had set the external drive to the second boot device.
Your script just comes back with...
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory

I have attached a screenshot.

Thank you in advance for your time.

move the boot info script file you downloaded to the desktop then run that command.

---

### Post by Jello123 on 2009-12-23
Sorry about that...
```

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 1.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sde
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

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

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4d49f150

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065 2,930,272,064 2,930,256,000   5 Extended
/dev/sda5              16,128   268,567,026   268,550,899   7 HPFS/NTFS
/dev/sda6         533,406,258 2,930,272,064 2,396,865,807  74 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf46bbff4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,930,272,064 2,930,272,002  74 Unknown


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07760775

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b1e03

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,024,529,309 1,024,529,247   7 HPFS/NTFS
/dev/sdd2       2,047,998,330 2,930,272,064   882,273,735   7 HPFS/NTFS
/dev/sdd3       1,024,529,310 2,047,998,329 1,023,469,020   5 Extended
/dev/sdd5       1,024,529,373 2,012,157,314   987,627,942  83 Linux
/dev/sdd6       2,012,157,378 2,047,998,329    35,840,952  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="1163F5E80CE679C0" TYPE="ntfs" 
/dev/sdd1: UUID="84B07375B0736C94" LABEL="New Volume" TYPE="ntfs" 
/dev/sdd2: UUID="322C802A2C7FE76F" LABEL="New Volume" TYPE="ntfs" 
/dev/sdd5: UUID="1d779c81-162a-4e20-bc06-1758d5ff8567" TYPE="ext4" 
/dev/sdd6: UUID="56e8a3af-ccb1-4988-87fa-ffb6481bfc06" TYPE="swap" 
/dev/sdc1: UUID="C600612300611C25" TYPE="ntfs" 
/dev/sde1: LABEL="COFEE" UUID="7ED3-548D" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sde1 on /cdrom type vfat (rw)
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


================================ sdc1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN 

=========================== sdd5/boot/grub/grub.cfg: ===========================

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
set root=(hd3,5)
search --no-floppy --fs-uuid --set 1d779c81-162a-4e20-bc06-1758d5ff8567
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
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set 1d779c81-162a-4e20-bc06-1758d5ff8567
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1d779c81-162a-4e20-bc06-1758d5ff8567 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set 1d779c81-162a-4e20-bc06-1758d5ff8567
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=1d779c81-162a-4e20-bc06-1758d5ff8567 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set c600612300611c25
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd5 during installation
UUID=1d779c81-162a-4e20-bc06-1758d5ff8567 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=56e8a3af-ccb1-4988-87fa-ffb6481bfc06 none            swap    sw              0       0

=================== sdd5: Location of files loaded by Grub: ===================


 524.5GB: boot/grub/grub.cfg
 524.5GB: boot/initrd.img-2.6.31-14-generic
 524.5GB: boot/vmlinuz-2.6.31-14-generic
 524.5GB: initrd.img
 524.5GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

sdf 
```

---

### Post by oldfred on 2009-12-23
Change your BIOS to boot from the 1500GB drive that is your current sdd drive that has grub installed in the MBR. Computers boot from the drive set as primary boot and jump to the MBR to continue to boot.

Both sda & sdb have no boot loaders. sdc has windows and your 8gb usb key has syslinux to boot.

If sdd is your esata it must not be set to boot first or the esata is not bootable? If you are booting windows then you have sdc set first.

---

### Post by Jello123 on 2009-12-23
> **oldfred said:**
> Change your BIOS to boot from the 1500GB drive that is your current sdd drive that has grub installed in the MBR.


  Ok got it to boot. The problem was too much beer I think :)

I have 3 identical hard drives with the same name and capacity and had them in the wrong order in the bios.

Thank you all for your time... and cheers

---

### Post by presence1960 on 2009-12-23
Pass a beer this way! Glad you got it working, everything in the script looked good to me. Enjoy Ubuntu.

---

