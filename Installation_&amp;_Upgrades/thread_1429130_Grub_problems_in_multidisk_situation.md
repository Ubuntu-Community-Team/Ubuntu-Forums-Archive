---
title: "Grub problems in multidisk situation"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by grepgav on 2010-03-13
So the issue I am having is installing ubuntu on a seperate drive from my Windows installation.

I have a 160GB drive that is my Windows drive and is the first SATA device. It is recognized as /dev/sda and is the device I have been using for a while.

I just bought a 1TB SATA drive and created a partition to install Ubuntu, which went fine.

The problem is when I try and boot I get a grub error:

```
No such disk
```

And I am dumped to a rescue console. By using the live cd I was able to install grub onto the MBR of the terabyte drive (/dev/sdb) but in order to boot to that device I have to bring up the boot menu every time I start up. However, it does boot correctly into both operating systems. My motherboard doesn't allow me to specify the boot order between hard drives, so is there any way for me to get grub installed on /dev/sda working correctly?

Thanks!

---

### Post by presence1960 on 2010-03-13
Need to see more info about your setup.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by grepgav on 2010-03-14
Thanks for helping out - the outputs of the script is below:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=9af82952-aab3-4562-ac64-3dae125f4058)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

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

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x70d170d1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   312,578,047   312,371,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073b24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   195,318,269   195,318,207  83 Linux
/dev/sdb2         195,318,270   203,125,859     7,807,590   5 Extended
/dev/sdb5         195,318,333   203,125,859     7,807,527  82 Linux swap / Solaris
/dev/sdb3         203,126,784 1,953,519,615 1,750,392,832   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        EC7CCAD57CCA99AA                       ntfs       System Reserved               
/dev/sda2        E442D31342D2E976                       ntfs                                     
/dev/sdb1        9af82952-aab3-4562-ac64-3dae125f4058   ext4                                     
/dev/sdb3        78A0F704A0F6C7A0                       ntfs       Data                          
/dev/sdb5        f872ef66-e750-4ab2-ae09-be613dfc48c4   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 9af82952-aab3-4562-ac64-3dae125f4058
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
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9af82952-aab3-4562-ac64-3dae125f4058
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9af82952-aab3-4562-ac64-3dae125f4058 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9af82952-aab3-4562-ac64-3dae125f4058
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9af82952-aab3-4562-ac64-3dae125f4058 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9af82952-aab3-4562-ac64-3dae125f4058
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9af82952-aab3-4562-ac64-3dae125f4058 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 9af82952-aab3-4562-ac64-3dae125f4058
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9af82952-aab3-4562-ac64-3dae125f4058 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ec7ccad57cca99aa
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
UUID=9af82952-aab3-4562-ac64-3dae125f4058 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda2 during installation
UUID=E442D31342D2E976 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb5 during installation
UUID=f872ef66-e750-4ab2-ae09-be613dfc48c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
   3.6GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.0GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .7GB: boot/vmlinuz-2.6.31-20-generic
   1.0GB: initrd.img
    .6GB: initrd.img.old
    .7GB: vmlinuz
    .5GB: vmlinuz.old
```

---

### Post by presence1960 on 2010-03-14
This what I would do. I would reboot & go into BIOS and set the 1 TB disk (sdb) as first in the hard disk boot order. Save changes to CMOS and continue booting. Boot into Ubuntu. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```Hit Enter at each window until you reach the window where you can choose where to put GRUB. You want to select sdb and deselect sda. Use the arrow keys to navigate and the space bar to select/deselect. Again deselect sda & select sdb. When that is set hit Tab to highlight OK and press Enter. Now any grub-pc (GRUB 2) updates will go to MBR of sdb.

In case you can't boot & get the same error after selecting sdb as first disk to boot there is an easy work around [here]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search") for that error.

Once you get GRUB fixed you may (but it is not necessary) want to fix the MBR of the windows 7 disk back to a windows MBR. You can do this from Ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```Ignore the warning. Now in terminal run ```
sudo lilo -M /dev/sda mbr
```Your sda MBR will now be windows and will allow you to boot right to windows should you make sda first disk to boot.

---

### Post by grepgav on 2010-03-14
Thank you for these instructions, I will try them when I get home.

However, I tried going into BIOS to set the 1TB drive as the first in the boot order but it only allows me to say Hard Drive in general, not select the actual drive.

Like I said, right now I can bring up the motherboard boot menu and select the 1TB drive (where grub works properly). My bigger question is it possible for grub to work on /dev/sda because it seems to automatically boot from this device.

Thanks - Gavin

---

### Post by grepgav on 2010-03-15
Great I got it fixed and working correctly. Thanks also for the commands to fix the Windows MBR - that will be nice if I ever need to use that drive separately. 

Thanks!

---

