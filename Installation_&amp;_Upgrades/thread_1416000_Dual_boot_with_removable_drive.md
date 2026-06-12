---
title: "Dual boot with removable drive"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by jmcgee on 2010-02-25
So I got this little Acer Revo running Windows XP. My idea is to install Ubuntu on an external drive, and be able to boot to that if it is connected, or XP if not.

So I boot from Ubuntu 9.10 CD, install to the connected external drive, format as ext 4.

When I reboot, I get grub menu and can successfully boot into either XP or Ubuntu.  That is good.  What bad is grub hangs if external drive is not connected.

How can I fix this so it works like I want. (grub works without that drive connected?)

---

### Post by presence1960 on 2010-02-25
You need to put GRUB on the MBR of the external disk & repair the MBR of the internal disk to a windows MBR. before giving precise commands to run to accomplish both of those I need to see more info. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by darkod on 2010-02-25
grub2 ended up on the int hdd MBR. With the ext disconnected it can't find its config files and stops. You want windows mbr on your int hdd, and grub2 on your ext hdd.

If you post the results of

sudo fdisk -l

with the ext connected, I can give you exact commands to run.

---

### Post by jmcgee on 2010-02-25
> **presence1960 said:**
> You need to put GRUB on the MBR of the external disk & repair the MBR of the internal disk to a windows MBR. before giving precise commands to run to accomplish both of those I need to see more info. ...

Thanks much, this is what it returned:
```

             Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5996bd7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,722,047    30,720,000  12 Compaq diagnostics
/dev/sda2    *     30,722,048   171,700,223   140,978,176   7 HPFS/NTFS
/dev/sda3         171,700,224   312,578,047   140,877,824   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00093ce1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   614,582,639   614,582,577  83 Linux
/dev/sdb2         614,582,640   625,137,344    10,554,705   5 Extended
/dev/sdb5         614,582,703   625,137,344    10,554,642  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        307835637835294C                       ntfs       PQSERVICE                     
/dev/sda2        7A46F03E46EFF8B1                       ntfs       ACER                          
/dev/sda3        820C6C480C6C3975                       ntfs       DATA                          
/dev/sdb1        d76181fe-62b1-4f4c-a16a-044888d2ce38   ext4                                     
/dev/sdb5        afca7ed6-94e4-495d-8c97-9c2f51e0a119   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/d76181fe-62b1-4f4c-a16a-044888d2ce38 ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="5"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
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
  set timeout=5
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 307835637835294c
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 7a46f03e46eff8b1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=afca7ed6-94e4-495d-8c97-9c2f51e0a119 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: initrd.img
    .6GB: vmlinuz


```

---

### Post by presence1960 on 2010-02-26
OK you can do both tasks from the Ubuntu 9.10 Live CD. Boot the Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```This will install lilo to the live CD session only. Then from terminal run ```
sudo lilo -M /dev/sda mbr
```This will make the MBR of the internal disk a windows MBR.

next from terminal run ```
sudo mount /dev/sdb1 /mnt
```This will mount your ubuntu / partition. Next run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of the external disk. Reboot without the Live CD, go into BIOS and set the external to boot before the internal disk. Save changes to CMOS and boot into Ubuntu. Open a terminal and run ```
sudo update-grub
```

You should now be set. When you boot without the external plugged in windows will boot, when you boot with the external plugged in GRUB will take over and you can choose to boot ubuntu or windows.

---

### Post by jmcgee on 2010-02-26
OK, I did as you said.  Now XP boots from internal hard drive when set to boot first and that is good, but if I set external hard drive to boot first, I get command prompt to reboot and use a bootable drive, or something very much like that. Only option is to reboot.

Here is output of the script now:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc5996bd7

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,722,047    30,720,000  12 Compaq diagnostics
/dev/sda2    *     30,722,048   171,700,223   140,978,176   7 HPFS/NTFS
/dev/sda3         171,700,224   312,578,047   140,877,824   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00093ce1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   614,582,639   614,582,577  83 Linux
/dev/sdb2         614,582,640   625,137,344    10,554,705   5 Extended
/dev/sdb5         614,582,703   625,137,344    10,554,642  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        307835637835294C                       ntfs       PQSERVICE                     
/dev/sda2        7A46F03E46EFF8B1                       ntfs       ACER                          
/dev/sda3        820C6C480C6C3975                       ntfs       DATA                          
/dev/sdb1        d76181fe-62b1-4f4c-a16a-044888d2ce38   ext4                                     
/dev/sdb5        afca7ed6-94e4-495d-8c97-9c2f51e0a119   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/d76181fe-62b1-4f4c-a16a-044888d2ce38 ext4       (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set default="5"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
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
  set timeout=5
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set d76181fe-62b1-4f4c-a16a-044888d2ce38
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 307835637835294c
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 7a46f03e46eff8b1
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d76181fe-62b1-4f4c-a16a-044888d2ce38 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=afca7ed6-94e4-495d-8c97-9c2f51e0a119 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .7GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: initrd.img
    .6GB: vmlinuz
```

---

### Post by presence1960 on 2010-02-26
Make sure your BIOS is capable of booting from a USB/removable disk. if it isn't then you won't be able to boot from the external.

---

### Post by jmcgee on 2010-02-26
> **presence1960 said:**
> Make sure your BIOS is capable of booting from a USB/removable disk. if it isn't then you won't be able to boot from the external.

Indeed, it was a bios setting I had missed.  Thanks a bunch for your help, working just fine now.  

Was there an option during install to make it come out like this that I missed?

---

### Post by jessytsmith on 2010-02-26
Perfect, thanks for posting this.

Jess

---

### Post by oldfred on 2010-02-26
It seems a fair number of people end up like you did. I think it is that you still have the internal set to boot first during the install to the external. Grub knows that you want to boot Ubuntu so it installs to the default boot drive (the internal). You probably could have set the external first in BIOS before the install. There is an advanced button during the install (after you decide on partitioning) that lets you choose an alternative location for grub that also would have worked. Most do not think of the advance button.

---

### Post by presence1960 on 2010-02-26
Here is a pic of the Advanced button on the Ready to install window of the ubuntu installer. OP should have clicked it and chose /dev/sdb to put GRUB on the MBR of the external disk.

---

### Post by darkod on 2010-02-26
> **presence1960 said:**
> Here is a pic of the Advanced button on the Ready to install window of the ubuntu installer. OP should have clicked it and chose /dev/sdb to put GRUB on the MBR of the external disk.

I don't know if you took the pic from somewhere or took it yourself, but just a friendly reminder that a picture where the cursor is actually over the Advanced button, not the Install button, is much clearer. :)
I'm being a pain now, but I automatically look at the cursor when I see it. :)

---

### Post by presence1960 on 2010-02-26
Taken from the graphical install community documentation.

---

