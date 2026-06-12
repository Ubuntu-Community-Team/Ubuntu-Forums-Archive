---
title: "Grub issues with full USB install 10.04"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by BananaPeal on 2011-02-18
Hello guys,

I've recently tried to do a full install to a USB stick using a 10.04 cd. 
2 things happen as I boot:
1. if Hdds are attached, boot hangs on "checking dmi pool data..."
2. if hdds not attached, "hdd error" scrolls across screen

boots normally w/o the usb stick.

I've set up my partitions on usb stick as

1: fat32 2gb    <<windows/storage
2: fat32 1.5gb  << future persistent install
3: ext4  4gb    << hoped-for full install

1 is the first partition so windows finds it nicely.

Before install, i unplugged my hdds so that grub wouldn't get  confused.
I told the installer to put the full install on sda3 with no swap space. 
I checked (advanced button on summary page) that bootloader is being installed to the usb on dev/sda (sda since no other drives attached). This should put it in the MBR (i think?)

Seems like I pressed all the right buttons huh? Is there a way to diagnose grub and see what's wrong? is there a reason grub may not initialize properly from a usb drive?

Thank you all for your insights, not sure where else to turn...

p.s: when holding shift to enter the grub menu, the word GRUB is printed to bottom of screen then nothing happens.

---

### Post by oldfred on 2011-02-18
Plug everything in and run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by BananaPeal on 2011-02-18
ello Oldfred! 

I was wondering where people got those nice boot summaries from! I'll stay on the liveCD until we get this sorted. Here's what bootscript had to say:

```
 
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 10247208 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sdc1 starts at sector 0. But according to the info 
                       from fdisk, sdc1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 4261888.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   385,094,114   385,094,052  83 Linux
/dev/sda2         385,094,115   390,716,864     5,622,750  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   976,766,975   976,560,128   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048     4,257,224     4,255,177   b W95 FAT32
/dev/sdc2           4,261,888     7,432,191     3,170,304   b W95 FAT32
/dev/sdc3           7,432,192    15,661,055     8,228,864  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a8b1632e-b66c-4266-b104-4e893ece691a   ext4                                     
/dev/sda2        7012a9a8-d26b-484e-8946-b0f74f5eea60   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6E3C15F33C15B755                       ntfs       System Reserved               
/dev/sdb2        3AAC182BAC17E065                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6C22-D826                              vfat                                     
/dev/sdc2        6C33-2701                              vfat                                     
/dev/sdc3        26c44801-dbd8-42c6-b035-44c1f1fe4b1a   ext4                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro  splash quiet vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro single  splash quiet vga=794
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro  splash quiet vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro single  splash quiet vga=794
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
UUID=a8b1632e-b66c-4266-b104-4e893ece691a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7012a9a8-d26b-484e-8946-b0f74f5eea60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb2       /media/windows  ntfs  nls=utf8,umask=0222 0    0

=================== sda1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/core.img
   3.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
  10.7GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   4.3GB: boot/vmlinuz-2.6.31-20-generic
  10.7GB: initrd.img
    .7GB: initrd.img.old
   4.3GB: vmlinuz
    .6GB: vmlinuz.old

=========================== sdc3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
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
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
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

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a /               ext4    errors=remount-ro 0       1
# /space was on /dev/sda2 during installation
UUID=6C33-2701  /space          vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=6C22-D826  /windows        vfat    utf8,umask=007,gid=46 0       1

=================== sdc3: Location of files loaded by Grub: ===================


   5.2GB: boot/grub/core.img
   5.1GB: boot/grub/grub.cfg
   5.7GB: boot/initrd.img-2.6.32-24-generic
   5.3GB: boot/vmlinuz-2.6.32-24-generic
   5.7GB: initrd.img
   5.3GB: vmlinuz
```

Looks like it mentions what the errors might be.... but I'm not too sure how to interpret those "offsets" of where it thinks the partitions should start or what can be done about them.

Thanks for your help!

---

### Post by oldfred on 2011-02-18
I do not see anything major wrong with boot script. You do have grub installed to the FAT partition of the flash drive, which may cause issues as windows partitions need windows partitions. 

This message
According to the info in the boot sector, 
                       sdc1 starts at sector 0. But according to the info 
                       from fdisk, sdc1 starts at sector 2048.
And similar message on sdc2 may be part of the problem as boot sectors should match partition table.

With NTFS you can fix with windows repair tools or testdisk. I assume but do not know if it works the same for fat?

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.

See if this also works for FAT:
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by BananaPeal on 2011-02-18
Hello, 

I've made some screenshots of my rebuildBS experience, seems to have worked without errors.

What do you think of the warnings? The program seems to think they're ok!

image usbFS is the partition summary as seen in testdisk
image fat32 is the first partition that holds the grub files and shows warnings about sector size.

the middle fat32 partition has no warnings about size.

I will now restart and see if the usb can boot. (just wanted to get imgs up from liveCD!)

Thanks again for your time!

---

### Post by BananaPeal on 2011-02-18
Hello oldfred,

some new info: I played around with testdisk to remove those warnings off of the first partition. I simply exchanged the numbers cited in the warnings using the [geometry] menu. 

The errors on the first fat32 have now oddly enough moved to the second fat32 and are now opposite! The second fat32 apparently expects a different number of heads/sector and sectors per track than the first!

Either way, this is surely an improvement, since at least the booting fat32 isn't broken in any way...

Attached are images of results of my actions:

if you compare these pictures to the earlier one showing warnings, you'll notice the warnings have switched their numbers around! now fat32 *should* have 247 not 255 heads!

not sure what to make of that... 

Does this mean I can now go chroot into the usb and reinstall grub?

I was going to use this process (since it seems comprehensive...) to do that:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Thanks for your time,

:P

---

### Post by oldfred on 2011-02-18
If you are not yet using the second FAT partition can you just delete it for now.

You can put ISO into your install and loopmount them directly with grub2. It might then be better to have just one FAT for windows data anyway and make the full install the 5.5GB. With only 4GB you will have very little working room after updating the install. Constant housecleaning & limited additional software.

---

### Post by BananaPeal on 2011-02-18
Just gparted it up! (took awhile to move the installation over...!)

I now have:
0. 1mb of unallocated space ... (?)
1. fat32 2gb 
2. ext4  5.5gb

testdisk reports no errors or warnings for the fat32 partition!

should I now chroot into ext4 linux and reinstall grub using the purge and install commands?
If yes, do you approve of the purge/reinstall process i linked in the earlier post?

Thanks for your continued support!

---

### Post by oldfred on 2011-02-18
I would just try reinstalling grub2 first. Then if that does not work do the full chroot method.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdc3 and want grub2 in drive sdc's MBR:
#Find linux partition, change sdc3 if not correct:
sudo fdisk -l
#confirm that linux is sdc3
sudo mount /dev/sdc3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc
# After rebooting into working system
sudo update-grub

---

### Post by BananaPeal on 2011-02-18
Hello, surely we must be getting close. This is 2nd attempt, first one came out "not a boot device".

I had to lookup how to do the mbr, here's my source: [http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/](http://www.pendrivelinux.com/install-a-new-mbr-to-your-usb-flash-device/)

the commands I used were:

sudo apt-get install mbr
sudo fdisk -l             ##>> sdc3 indeeed
sudo install-mbr dev/sdc
sudo mount /dev/sdc3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
Installation finished. No error reported.
ubuntu@ubuntu:~$ cd Dow*
ubuntu@ubuntu:~/Downloads$ ls
boot_info_script055.sh
ubuntu@ubuntu:~/Downloads$ sudo chmod +x boo*
ubuntu@ubuntu:~/Downloads$ sudo bash boo*

and here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   385,094,114   385,094,052  83 Linux
/dev/sda2         385,094,115   390,716,864     5,622,750  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdb2             206,848   976,766,975   976,560,128   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048     4,257,224     4,255,177   b W95 FAT32
/dev/sdc3           4,257,225    15,647,309    11,390,085  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        a8b1632e-b66c-4266-b104-4e893ece691a   ext4                                     
/dev/sda2        7012a9a8-d26b-484e-8946-b0f74f5eea60   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6E3C15F33C15B755                       ntfs       System Reserved               
/dev/sdb2        3AAC182BAC17E065                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        6C22-D826                              vfat                                     
/dev/sdc3        26c44801-dbd8-42c6-b035-44c1f1fe4b1a   ext4                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc3        /mnt                     ext4       (rw)


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
search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
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
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro  splash quiet vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro single  splash quiet vga=794
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro  splash quiet vga=794  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a8b1632e-b66c-4266-b104-4e893ece691a
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a8b1632e-b66c-4266-b104-4e893ece691a ro single  splash quiet vga=794
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
UUID=a8b1632e-b66c-4266-b104-4e893ece691a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7012a9a8-d26b-484e-8946-b0f74f5eea60 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb2       /media/windows  ntfs  nls=utf8,umask=0222 0    0

=================== sda1: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/core.img
   3.7GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.31-14-generic
  10.7GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   4.3GB: boot/vmlinuz-2.6.31-20-generic
  10.7GB: initrd.img
    .7GB: initrd.img.old
   4.3GB: vmlinuz
    .6GB: vmlinuz.old

=========================== sdc3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
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
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 26c44801-dbd8-42c6-b035-44c1f1fe4b1a
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

=============================== sdc3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=26c44801-dbd8-42c6-b035-44c1f1fe4b1a /               ext4    errors=remount-ro 0       1
# /space was on /dev/sda2 during installation
UUID=6C33-2701  /space          vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=6C22-D826  /windows        vfat    utf8,umask=007,gid=46 0       1

=================== sdc3: Location of files loaded by Grub: ===================


   3.0GB: boot/grub/core.img
   3.5GB: boot/grub/grub.cfg
   4.1GB: boot/initrd.img-2.6.32-24-generic
   3.7GB: boot/vmlinuz-2.6.32-24-generic
   4.1GB: initrd.img
   3.7GB: vmlinuz
```

Despite that same offset-type error in the report, testdisk this time shows no errors or warnings for the fat32. And there's an asterix next to it saying the fat32 is boot.

will rreboot and see if i missed a step on the first attempt.

---

### Post by BananaPeal on 2011-02-18
Still no dice... not a bootable disk it says. 

Do you have to unmount the drive for the changes to stick? 

I did another bootinfo upon restarting and getting into liveCD and it looks exactly the same as the one i posted, so it seems like unmounting isn't necessary and that it installed right. Seems like bios isn't finding grub2.

Bios is indeed using USB-HDD to look for bootable drive

I really have no idea what else could be the issue... 

Thanks for your patience, had no idea it would take this long!

Also some people have mentioned that pny drives in particular may not boot... not sure why,

there is also a readyBoostTest*.tmp sitting in the fat32 that testDisk can see. might this get in the way? (I've never used readyBoost). Will now restart and try all usb-cdrom etc options.

---

### Post by oldfred on 2011-02-18
My BIOS on my Desktop would not boot from any of many USB options including USB-HD. But when I went in to choose HD, it became one of my hard drives to boot.

Some BIOS (Intel for one) need a boot flag on a primary partition. You can use gparted, disk utility or command line to set boot flags. Grub does not use a boot flag, but windows has to have one for its boot loader.

It should not have mattered, but mbr is a windows boot loader, but you overwrote that with grub and it should be ok.

I have seen something like quickboot in the MBR that had to be turned off to get grub to work.

I have had good luck with both Kingston & Microcenter no name flash drives.

---

### Post by BananaPeal on 2011-02-18
usb drive works on an hp laptop. Looks like it's a bios thing. Thank you so much in helping me track this down. Don't understand why it's hard for people to write conforming software... don't these bios people test their software before sending it out?

ugh.

Well. Let you know if  I get it to work. Thanks again for your time and patience.

---

### Post by BananaPeal on 2011-02-19
Hello,

I took a suggestion from Mr. Cameron on another similar thread to use ntfs for the first partition on the ubs that holds the grub mbr. This allowed my bios to finally realize the usb drive was bootable and here I am, finally installing video drivers.

the fat32 worked fine on a hp bios, but I geuss mine's just more picky.

Thank you for your help oldfred, i needed to use those commands/programs many times  to make sure stuff was getting installed right.

---

### Post by oldfred on 2011-02-19
Glad you got it working.

I wonder if it was just totally reformatting the first partition is what solved it, but we will never know.

---

### Post by BananaPeal on 2011-02-19
> **oldfred said:**
> Glad you got it working.

I wonder if it was just totally reformatting the first partition is what solved it, but we will never know.

i think my bios just doesn't like fat32 for mbr since it worked ok on the other computer as fat32... inconsistent results like these are hard to diagnose. i blame the bios people.

---

