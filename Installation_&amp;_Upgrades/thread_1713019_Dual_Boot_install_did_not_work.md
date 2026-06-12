---
title: "Dual Boot install did not work"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by Howski on 2011-03-23
Hi,

Last night I tried to put on 10.10 64 bit on to a computer that already has Windows XP. The install itself all went along fine and everything completed as you'd expect. Not having enough time I shutdown the machine after the install.

My only issue is there does not seem to be a boot menu and when I turn on it boots straight in to XP. I can see the partitions in disk manager and they seem to have data in the main part

Have I missed a step, does Ubuntu not install a boot loader? Can I add it manually into boot.ini? If so which partition? 

Is there a way to get this sorted by ubuntu?

Thanks in advance!
-Howard

---

### Post by Dutch70 on 2011-03-23
Hi & welcome to UF

We'll need to get a look at your boot info script.

Follow the directions on the link below & post the output between code tags, by highlighting the info and clicking the "#" in the toolbar.

[[COLOR="blue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")

Download the file to your desktop and run this command in a terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Howski on 2011-03-23
Hi,

Please see the results below:



                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => ThinkPad is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   768,265,335   768,265,273   7 HPFS/NTFS
/dev/sda2         963,401,985   976,768,064    13,366,080  12 Compaq diagnostics
/dev/sda3         768,266,238   963,401,727   195,135,490   5 Extended
/dev/sda5         768,266,240   955,375,615   187,109,376  83 Linux
/dev/sda6         955,377,664   963,401,727     8,024,064  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        02A41F11A41F06B7                       ntfs       Preload                       
/dev/sda2        482E-9859                              vfat       SERVICEV001                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d   ext4                                     
/dev/sda6        ddec1f6d-ed22-4c1c-91f5-79c09b53a3aa   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 02a41f11a41f06b7
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ff0ceb61-d5eb-48bf-a1d0-432882eb1d3d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ddec1f6d-ed22-4c1c-91f5-79c09b53a3aa none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 483.6GB: boot/grub/core.img
 421.4GB: boot/grub/grub.cfg
 413.6GB: boot/initrd.img-2.6.35-22-generic
 483.6GB: boot/vmlinuz-2.6.35-22-generic
 413.6GB: initrd.img
 483.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  61 74 68 3d 22 43 3a 5c  50 72 6f 67 72 61 6d 20  |ath="C:\Program |
00000010  46 69 6c 65 73 5c 4f 70  65 6e 4f 66 66 69 63 65  |Files\OpenOffice|
00000020  2e 6f 72 67 20 33 5c 70  72 6f 67 72 61 6d 5c 22  |.org 3\program\"|
00000030  2f 3e 0a 3c 65 72 72 6f  72 6d 61 69 6c 3a 53 74  |/>.<errormail:St|
00000040  61 63 6b 49 6e 66 6f 20  70 6f 73 3d 22 31 30 35  |ackInfo pos="105|
00000050  32 35 39 33 32 30 31 22  20 69 70 3d 22 30 78 30  |2593201" ip="0x0|
00000060  30 36 33 30 30 36 39 22  20 72 65 6c 3d 22 30 78  |0630069" rel="0x|
00000070  30 30 32 33 30 30 36 39  22 20 6e 61 6d 65 3d 22  |00230069" name="|
00000080  73 6f 66 66 69 63 65 2e  62 69 6e 22 20 70 61 74  |soffice.bin" pat|
00000090  68 3d 22 43 3a 5c 50 72  6f 67 72 61 6d 20 46 69  |h="C:\Program Fi|
000000a0  6c 65 73 5c 4f 70 65 6e  4f 66 66 69 63 65 2e 6f  |les\OpenOffice.o|
000000b0  72 67 20 33 5c 70 72 6f  67 72 61 6d 5c 22 2f 3e  |rg 3\program\"/>|
000000c0  0a 3c 65 72 72 6f 72 6d  61 69 6c 3a 53 74 61 63  |.<errormail:Stac|
000000d0  6b 49 6e 66 6f 20 70 6f  73 3d 22 31 30 35 32 35  |kInfo pos="10525|
000000e0  39 33 32 30 32 22 20 69  70 3d 22 30 78 30 30 36  |93202" ip="0x006|
000000f0  33 30 30 36 39 22 20 72  65 6c 3d 22 30 78 30 30  |30069" rel="0x00|
00000100  32 33 30 30 36 39 22 20  6e 61 6d 65 3d 22 73 6f  |230069" name="so|
00000110  66 66 69 63 65 2e 62 69  6e 22 20 70 61 74 68 3d  |ffice.bin" path=|
00000120  22 43 3a 5c 50 72 6f 67  72 61 6d 20 46 69 6c 65  |"C:\Program File|
00000130  73 5c 4f 70 65 6e 4f 66  66 69 63 65 2e 6f 72 67  |s\OpenOffice.org|
00000140  20 33 5c 70 72 6f 67 72  61 6d 5c 22 2f 3e 0a 3c  | 3\program\"/>.<|
00000150  65 72 72 6f 72 6d 61 69  6c 3a 53 74 61 63 6b 49  |errormail:StackI|
00000160  6e 66 6f 20 70 6f 73 3d  22 31 30 35 32 35 39 33  |nfo pos="1052593|
00000170  32 30 33 22 20 69 70 3d  22 30 78 30 30 36 33 30  |203" ip="0x00630|
00000180  30 36 39 22 20 72 65 6c  3d 22 30 78 30 30 32 33  |069" rel="0x0023|
00000190  30 30 36 39 22 20 6e 61  6d 65 3d 22 73 6f 66 66  |0069" name="soff|
000001a0  69 63 65 2e 62 69 6e 22  20 70 61 74 68 3d 22 43  |ice.bin" path="C|
000001b0  3a 5c 50 72 6f 67 72 61  6d 20 46 69 6c 65 00 fe  |:\Program File..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 27 0b 00 fe  |............'...|
000001d0  ff ff 05 fe ff ff 02 10  27 0b 00 78 7a 00 00 00  |........'..xz...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2011-03-23
You show this, which is not a normal windows bootloader.
ThinkPad is installed in the MBR of /dev/sda

Do you have some security settings to prevent writing into the MBR? Like bitlocker or a BIOS setting.

Does you boot give you special options other than the standard windows boot. Possible  f keys or something. 

You may want to back up MBR just to have the custom settings saved.

This backs up the boot code not the partition table. From liveCD:
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1

Copy mbr.bin to some other device.

If MBR is not locked.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Howski on 2011-03-23
I've not knowingly got anything other than a non-standard Windows install, howevr its not suprising as I installed off a Lenvo disk and it has caused nothing but issues. I wish I did not have to but thats M$ ;-)

Its probably the "recovery partition" which I've never used but since I have no option to install windows off a normal windows CD I have to have it.


I'll give that a go. I was kinda hoping I could just add a single line to the windows boot.ini. Ah well its never easy ;-)

Thanks again!

---

### Post by Howski on 2011-03-23
Hi,

Might be getting confused but the first command:

dd if=/dev/sda of=/mbr.bin bs=446 count=1

Comes back with permission denied

---

### Post by oldfred on 2011-03-23
I still forget sudo. Whenever I get a permission denied I just add sudo to the beginning.

sudo dd if=/dev/sda of=/mbr.bin bs=446 count=1

---

### Post by Howski on 2011-03-24
Sorted, thanks ever so much!!

---

