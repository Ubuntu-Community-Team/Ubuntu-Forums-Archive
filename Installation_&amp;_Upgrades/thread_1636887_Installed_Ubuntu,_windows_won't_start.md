---
title: "Installed Ubuntu, windows won't start"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by RobertR171192 on 2010-12-03
Let me just start by saying I've installed ubuntu on another computer before but I just erased the entire hard drive and used all of it for Ubuntu. But, on my laptop I wanted to install Ubuntu in a second partition on my hard drive, the other partition would have windows 7 on it. Here's my problem though, windows 7 won't start. All it will do is go to the windows loading screen and flash a blue screen(too quick to notice the first word so no help there) then restart.Ubuntu works fine in fact I'm using it right now to type this. I can still see the files on the other partition so windows is not gone. When I went to partition in the Ubuntu installer I choose side by side splitting it windows 140 gb and Ubuntu 170 gb. I have a 320 gb hard drive and the rest of the hard drive was a recovery partition and a system partition. I did not delete those partitions. Here's what throws me off:
[IMG]http://i1139.photobucket.com/albums/n541/robertr171192/Screenshot.png[/IMG]
For some reason it shows 3 large partitions and the two that I mentioned. Clearly one of them should not be there and I'm almost positive it's the extended 170 gb partition that says it's empty when I click on it. I tried deleting it and it came up with an error that I can't delete. The 170 GB extended partition gives this information when I click on it:

Usage: Container for Logical
Partitions                                          Device: /dev/sda4
Partition Type: Extended (0x05) 
                                                    Partiton Label: -
Partition Flags: -                                                                              
Capacity: 170 GB

I'm more confused with how it even got there in the first place. I never created a blank partition and it's impossible to put 490 GB worth of partitions on a 320 GB hard drive so I don't know what the hell is going on.... The 140 gb partition is windows and the 163 gb is linux. I don't know if that's the reason windows won't start but I really don't think that's helping anything either. All I know is it won't boot into windows but all of the files for windows are still on the hard drive, I have full access to all of them. Does anyone have any idea what might have caused windows to stop working and that random partition to pop up out of nowhere?

I figured it would be more appropriate to ask on the Ubuntu forums rather than a pc forum because it was most likely caused somewhere in the installation.

If anyone can help, thanks. If you need more info tell me what you need.

---

### Post by Quackers on 2010-12-03
Your third partition is an extended partition of 170GB which includes the 163GB ext4 partition and the 6.9GB swap space.
Regarding your Windows boot problem please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by RobertR171192 on 2010-12-03
Thanks for the quick reply here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   276,506,151   273,432,104   7 HPFS/NTFS
/dev/sda3         608,497,664   625,141,759    16,644,096  17 Hidden HPFS/NTFS
/dev/sda4         276,506,622   608,497,663   331,991,042   5 Extended
/dev/sda5         276,506,624   594,941,951   318,435,328  83 Linux
/dev/sda6         594,944,000   608,497,663    13,553,664  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C603A50603A30DE                       ntfs       System                        
/dev/sda2        508060AE80609C6A                       ntfs       TI102763W0F                   
/dev/sda3        04FA86DDFA86CA7E                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        de0439d5-3c82-4047-8e10-4ebb7ecf61b6   ext4                                     
/dev/sda6        08d00470-ff45-46bb-99f8-c56ead0e52a4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=de0439d5-3c82-4047-8e10-4ebb7ecf61b6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=de0439d5-3c82-4047-8e10-4ebb7ecf61b6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set de0439d5-3c82-4047-8e10-4ebb7ecf61b6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5c603a50603a30de
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 508060ae80609c6a
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 04fa86ddfa86ca7e
    chainloader +1
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=de0439d5-3c82-4047-8e10-4ebb7ecf61b6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=08d00470-ff45-46bb-99f8-c56ead0e52a4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 234.0GB: boot/grub/core.img
 274.8GB: boot/grub/grub.cfg
 234.0GB: boot/initrd.img-2.6.32-24-generic
 234.0GB: boot/vmlinuz-2.6.32-24-generic
 234.0GB: initrd.img
 234.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 fa 12 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f0  fa 12 00 d8 ce 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2010-12-03
You have /bootmgr /Boot/BCD on both sda1 and sda2. You also have /BOOTMGR /BOOT/BCD same names but in capitals on sda3. Your boot flag is set on sda1.
Have you run startup repairs or similar from a Windows repair/installation disc?

---

### Post by RobertR171192 on 2010-12-03
I don't have a cd because I'm using a netbook but I think I can run start up repairs on one of those. When I choose one in the boot menu last night and I saw the option to do start up repair or start windows normally but it was late so I just decided sleeping was a better option. I forgot about it until you just reminded me so I think I'll try that real quick.

---

### Post by Quackers on 2010-12-03
I wasn't suggesting you run startup repair - just asking if you have done :-)

One other question. You appear to have 3 Windows Loader options to boot from in the grub menu. Which have you tried to boot Windows with?

---

### Post by RobertR171192 on 2010-12-03
Both windows 7. Haven't tried the vista because vista was never installed on the computer I'm not even sure why it's there. I'm unsure now. Should I run the startup repair?

---

### Post by Quackers on 2010-12-04
The Vista Loader is probably appearing because you have /BOOTMGR /BOOT/BCD in sda3 for some reason. Try booting from that, although I suspect it won't work any better than the others.
I am confused as to how you have got 3 sets of Windows boot files in 3 separate partitions, without a Windows repair cd.
And we are talking about 2 different types of startup repair.
If you try booting from the Windows loader in sda2 it can not do any harm if you run the startup repair that is being offered by the menu there.
Please let us know what happens.

---

### Post by RobertR171192 on 2010-12-04
Well start up repair fixed it and windows boots now. I still have no idea how it ended up with all of that nonsense on the computer in the first place but whatever. I booted from the windows loader in sda2 and choose start up repair. Left it alone for a couple hours, it said it would take over an hour to fix the hard disk errors and I forgot it was on and came back like 4 hours later. I started windows in sda3 and booted from that. 

Thanks.

---

### Post by Quackers on 2010-12-04
Me neither but I'm glad it's working now :-)
Windows can be decidedly dodgy at times! And very fussy too!

---

