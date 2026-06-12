---
title: "Can't boot Windows 7 after installing Ubuntu"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by Bjorn Jonsson on 2010-04-05
I'm trying to install Ubuntu 9.10 on my machine which already has Windows 7 (I want to be able to dual-boot). I had no problems installing Ubuntu but now I cannot boot Windows, I get this error after selecting Windows in the Grub boot menu:

error: invalid signature
Press any key to continue

When I press a key I'm returned to the Grub menu. There I can boot Linux without problems.

I have two 500 GB disks in a RAID 1 array. Windows 7 is installed there. Then I have a 1.5 TB disk where I installed Linux in a partition I created for it.

I think the problem may be that I have RAID because this seems to show up as two disks and not one:

more /boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

Three disks and not two.

If I do sudo update-grub I get this:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/mapper/isw_ccdddiiiea_Mirror1
grub-probe: error: no mapping exists for `isw_ccdddiiiea_Mirror1'
done

Any help appreciated. I'm a Linux novice but have been Googling a lot; it's after this Googling that I suspect the RAID is the problem. However, I have been unable to find out what to do next.

---

### Post by stlsaint on 2010-04-05
Sorry if this is of little help but i dont deal with raid much!! ;)
Based off that error i would say that you need to add a custom stanza entry into your 40_customs or maybe os_probe config to point grub to see where windows is installed. I believe thats what that mapping error comes from. (Again i have not dealt with raid in some time!) It seems that grub notices windows but thats about it. Again sorry i cannot offer more advice on the matter.

---

### Post by oldfred on 2010-04-05
If you boot from the raid does windows boot?

Since you have multiple drives and Ubuntu on a separate drive you should still have the windows boot loader in the MBR of the other drive(s). The normal way grub works is to chainboot to the PBR where windows has additional boot files. That is all the windows boot loader in the MBR does. New grub2 now does some checking to make sure things should work where old grub just chainbooted (jumped to that PBR) and if it did not work you crashed. I think you should be able to chainboot to the MBR with a minimal chainboot entry like this in 40_custom if the raid array boot for windows is sda or hd0.

Add to /etc/grub.d/40_custom and run sudo update-grub..
Chainboot to sda to MBR not partition
# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hd0)
    chainloader +1
}

---

### Post by Bjorn Jonsson on 2010-04-06
> **oldfred said:**
> If you boot from the raid does windows boot?
No - if I use a BIOS menu at startup to select to boot from the RAID I get exactly the same result as from a normal boot, i.e. I get the Grub boot menu and cannot boot Windows. So the suggested solution (chainboot to sda) wouldn't work if I understand this correctly.

I also tried booting from the 1.5 TB disk but as I expected it didn't work and resulted in this:
BOOTMGR is missing
Press Ctrl+Alt+Del to restart

BTW dual booting by booting Windows 7 by default and Ubuntu by selecting the 1.5 TB disk from the BIOS menu would be an acceptable interim solution (if I knew how to make it work) but what I really want is 'true' dual boot. I have the information I need repair Windows to get it to boot but if I repair it I'm pretty sure I wouldn't be able to boot Linux.

Additional information from fdisk -l, i don't know if it's needed here but I'm posting it just in case:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d62975b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       25497   204697600    7  HPFS/NTFS
/dev/sda3           25497       60800   283572224    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d62975b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       25497   204697600    7  HPFS/NTFS
/dev/sdb3           25497       60800   283572224    7  HPFS/NTFS

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13dd8673

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       72079   578968576    7  HPFS/NTFS
/dev/sdc2           91201      182402   732567552    7  HPFS/NTFS
/dev/sdc3           72080       74510    19527007+   5  Extended
/dev/sdc4           74511       91200   134062425   83  Linux
/dev/sdc5           72080       74510    19526976   82  Linux swap / Solaris

---

### Post by oldfred on 2010-04-06
Did grub also overwrite the windows boot loader?

Post this but I do not know what it will show with raid.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Bjorn Jonsson on 2010-04-06
This is what I got:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => Grub 2 is installed in the MBR of /dev/mapper/isw_ccdddiiiea_Mirror and 
    looks for (UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_ccdddiiiea_Mirror1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_ccdddiiiea_Mirror2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_ccdddiiiea_Mirror3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d62975b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   409,602,047   409,395,200   7 HPFS/NTFS
/dev/sda3         409,602,048   976,746,495   567,144,448   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13dd8673

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,157,939,199 1,157,937,152   7 HPFS/NTFS
/dev/sdc2       1,465,139,200 2,930,274,303 1,465,135,104   7 HPFS/NTFS
/dev/sdc3       1,157,949,135 1,197,003,149    39,054,015   5 Extended
/dev/sdc5       1,157,949,198 1,197,003,149    39,053,952  82 Linux swap / Solaris
/dev/sdc4       1,197,003,150 1,465,127,999   268,124,850  83 Linux


Drive: isw_ccdddiiiea_Mirror ___________________ _____________________________________________________

Disk /dev/mapper/isw_ccdddiiiea_Mirror: 500.1 GB, 500104826880 bytes
255 heads, 63 sectors/track, 60800 cylinders, total 976767240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d62975b

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_ccdddiiiea_Mirror1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_ccdddiiiea_Mirror2            206,848   409,602,047   409,395,200   7 HPFS/NTFS
/dev/mapper/isw_ccdddiiiea_Mirror3        409,602,048   976,746,495   567,144,448   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_ccdddiiiea_Mirror1 CCFAD20FFAD1F624                       ntfs       System Reserved               
/dev/mapper/isw_ccdddiiiea_Mirror2 F6E6D3FBE6D3BA57                       ntfs                                     
/dev/mapper/isw_ccdddiiiea_Mirror3 DACC392ECC3905F3                       ntfs                                     
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        4A42F70742F6F713                       ntfs                                     
/dev/sdc2        4E74FC1E74FC0A8B                       ntfs                                     
/dev/sdc4        14af58f1-42d2-43d6-8e91-da3b8e7456f7   ext4                                     
/dev/sdc5        8958f71f-a2c2-4356-a42c-cd89cb6a2057   swap                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_ccdddiiiea_Mirror
isw_ccdddiiiea_Mirror1
isw_ccdddiiiea_Mirror2
isw_ccdddiiiea_Mirror3

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc4        /                        ext4       (rw,errors=remount-ro)


=========================== sdc4/boot/grub/grub.cfg: ===========================

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
set default="6"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,4)
search --no-floppy --fs-uuid --set 14af58f1-42d2-43d6-8e91-da3b8e7456f7
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
    set root=(hd2,4)
    search --no-floppy --fs-uuid --set 14af58f1-42d2-43d6-8e91-da3b8e7456f7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,4)
    search --no-floppy --fs-uuid --set 14af58f1-42d2-43d6-8e91-da3b8e7456f7
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd2,4)
    search --no-floppy --fs-uuid --set 14af58f1-42d2-43d6-8e91-da3b8e7456f7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,4)
    search --no-floppy --fs-uuid --set 14af58f1-42d2-43d6-8e91-da3b8e7456f7
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7 ro single 
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
menuentry "Windows 7 (loader) (on /dev/mapper/isw_ccdddiiiea_Mirror1)" {
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc4 during installation
UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=8958f71f-a2c2-4356-a42c-cd89cb6a2057 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc4: Location of files loaded by Grub: ===================


 618.2GB: boot/grub/core.img
 618.3GB: boot/grub/grub.cfg
 613.0GB: boot/initrd.img-2.6.31-14-generic
 613.2GB: boot/initrd.img-2.6.31-20-generic
 613.0GB: boot/vmlinuz-2.6.31-14-generic
 613.0GB: boot/vmlinuz-2.6.31-20-generic
 613.2GB: initrd.img
 613.0GB: initrd.img.old
 613.0GB: vmlinuz
 613.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3



=======Devices which don't seem to have a corresponding hard drive==============

sdb: "jmicron" and "isw" formats discovered (using isw)! sda: "jmicron" and "isw" formats discovered (using isw)! 
=============================== StdErr Messages: ===============================

ERROR: only one argument allowed for this option
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
ERROR: only one argument allowed for this option
```

---

### Post by oldfred on 2010-04-06
I think some of the unknown information is that the script is not particularly designed for raid as that is not very common for desktop and is more for servers which are not multibooting.

You have two copies of grub installed and both boot from UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7. 

I would try to reinstall windows to the MBR of your raid if that is possible. Again I am not as familiar with raid.

Install windows to overwrite this:
Grub 2 is installed in the MBR of /dev/mapper/isw_ccdddiiiea_Mirror and 
    looks for (UUID=14af58f1-42d2-43d6-8e91-da3b8e7456f7)/boot/grub.

---

### Post by Bjorn Jonsson on 2010-04-07
Still no success - anyone here with RAID and dual boot experience?
 
I thought I would be able to get Windows 7 back by booting from the Windows 7 installation DVD and then doing bootrec.exe /fixboot and bootrec.exe /fixmbr but this didn't change anything. I can still boot Ubuntu but not Windows 7. This seems to be a mess because when I decided to see what happened if I selected to install Windows 7 only the 1.5 TB disk showed up when I was asked where I wanted to install (I didn't proceed to install Windows 7 though).
 
What I would like to do is make Windows 7 bootable again, even if that means a non-bootable Ubuntu, because I suspect that if this is successful I can easily add the Ubuntu boot option using EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)).
 
I'm starting to think I might need to completely reinstall Windows 7. Not as bad as it sounds (if I can get the W 7 installation process to 'see' the 500 GB RAID) but still something I'd like to avoid.

---

### Post by oldfred on 2010-04-08
Did your windows repairs reinstall windows to the MBR of your windows drive? You can quickly check with the boot_info script. If that did not work it is a windows repair problem with repairing in raid sets.

the windows entry was never correct in your grub.cfg. If you can directly boot windows you can run this to correct the windows entry in grub.
sudo update-grub

---

### Post by Bjorn Jonsson on 2010-04-10
Some good news at last: I managed to get Windows 7 to boot again after lots of messing with the MBR, BCD, drive letters etc. I ended up physically disconnecting the 1.5 TB disk to get the $%#* Windows 7 repair utilities to understand that the 500 GB RAID was disk 0 and not disk 1, thus forcing them to write MBR/BCD to that disk and not the 1.5 TB disk when I did bootrec /fixmbr, bootrec /fixboot and bootrec /rebuildbcd.
 
I now want to use EasyBCD to add Ubuntu to the Windows 7 bootloader menu - in fact I have already tried that. I pointed it to the Linux partition but Linux didn't boot. I'm pretty sure the reason is that I need to install Grub to the bootsector of the Linux partition by booting from the Ubuntu DVD. I really want to do that without messing everything up again ;-) so any help/information on how to do that would be greatly appreciated.

---

### Post by oldfred on 2010-04-10
I do not know EasyBCD. With grub or grub2 most of the instructions on chainbooting assume you want to chainboot to a partition, but you can chainboot in grub to another MBR.

Maybe in EasyBCD instead of a drive, partition entry you can just put in the drive and it will chainboot to the MBR of that drive??

Grub entry:
# Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

# Chainload another bootloader
menuentry "Chainload MBR drive 1" {
set root=(hd1)
chainloader +1
}

---

### Post by Bjorn Jonsson on 2010-04-13
[SIZE=2]What I want to do is use the Windows bootloader to boot Ubuntu by pointing it to the Linux partition. This is trivial using EasyBCD but didn't work, probably because I need to install Grub to the Linux partition's bootsector. The Linux partition is /dev/sdc4 as can be seen earlier in the thread. So I tried this:[/SIZE]
 
[SIZE=2]sudo grub-install /dev/sdc4[/SIZE]
 
[SIZE=2]However, this didn't work and resulted in this:[/SIZE]
[SIZE=2]ubuntu@ubuntu:~$ sudo grub-install /dev/sdc4[/SIZE]
[SIZE=2]grub-probe: error: cannot find a device for /boot/grub[/SIZE]
 
[SIZE=2]No path or device specified[/SIZE]
[SIZE=2]Try ``grub-probe --help'' for more information[/SIZE]
[SIZE=2]Auto-detection of file system module failed[/SIZE]
[SIZE=2]Please specify the module with the option '--module' explicitly[/SIZE]
 
[SIZE=2]Am I completely misunderstanding what I need to do to boot Ubuntu from the Windows bootloader or am I making some minor error?[/SIZE]

---

### Post by oldfred on 2010-04-13
See this for general instructions:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if you want to install to a partition it will complain. you have to add --force to the install command.

---

### Post by Bjorn Jonsson on 2010-04-16
It works!! I used the EasyBCD 2.0 Beta to add the Ubuntu entry to the Windows bootloader. When I select Ubuntu my original Grub menu appears and I can select Ubuntu there. Now all that's left is to clean up that menu a bit but that's trivial.
 
Note: If you want to use EasyBCD it's important to use the EasyBCD 2.0 Beta and not the newest official version if you have a Ubuntu release subsequent to 8.04. There is helpful information at [http://neosmart.net/forums/index.php](http://neosmart.net/forums/index.php)
 
My impression is that using EasyBCD like I did is (probably by far) the easiest way if you want a Windows 7/Linux dual boot, at least if you have a complex system (RAID like I do and/or Linux is not on the same hard disk as Windows) and if you are using a recent version of Ubuntu.

---

### Post by imranrs on 2010-05-01
Hello,
My computer has 2 drives.
One has windows 7 and another has Ubuntu 10... 
After upgrading from 9 to 10, my windows 7 does not load irrespective of disconnecting Ubuntu installed hard drive.
Initially it use to do it.
I am pasting the grub info, I am a beginner in using linux.

**********************************************************

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6d5d02b3-80f6-4676-a9e9-d57fb16f35bc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=6d5d02b3-80f6-4676-a9e9-d57fb16f35bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6d5d02b3-80f6-4676-a9e9-d57fb16f35bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(/dev/sdb,1)'
	search --no-floppy --fs-uuid --set 01ca970006f67610
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

Please help me out how to fix it.

If more infomation is needed, I will provide.

Thanks

---

### Post by oldfred on 2010-05-02
imranrs 
Welcome to the forums, but you should start your own thread as this one is solved and has raid as a complicating factor.

Many have found this as the solution as you installed grub to the windows partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If not the above, start a new thread and post the results.txt referenced in the above link.

---

