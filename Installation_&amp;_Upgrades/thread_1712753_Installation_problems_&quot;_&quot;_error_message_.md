---
title: "Installation problems: &quot;??? ???&quot; error message &amp; &quot;ready when you are&quot; errors"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by &amp;Clyde on 2011-03-23
Hello,

I tried to install Ubuntu 10.10 on my system yesterday evening (night actually). However, I failed to complete the installation. All I got was a error notification box (the red X symbol) with a bunch of question marks in it: "??? ???".

I have win7 installed on the drive that I want to install Ubuntu, and since the drive has only one partition (which houses win7 and is the partition that boots) I selected the option to "...run along side..." and moved the slider in order create a new linux partition (about 20Gb) on that drive. 

However, when the partitioning was done and I was about to select my timezone when I got the error... :( I had no choice but to click OK and the installation process jumped back to the first screen/phase. Any ideas? I mean, there isn't much that can go wrong here, is there? A win7 on one big partition...


I also tied to create the partitions manually (\, \home, swap) but then the installation just hangs at the text "ready when you are". Here I just got to select my timezone and keyboard layout (it hangs on the keyboard layout, so it is not the uppercase-login-name-error).


I installed from a USB-stick. 64-bit.

Please help, I really want to get going with this dual booting thing.
Thanks.

---

### Post by Hakunka-Matata on 2011-03-23
> **&Clyde said:**
> Hello,

I tried to install Ubuntu 10.10 on my system yesterday evening (night actually). However, I failed to complete the installation. All I got was a error notification box (the red X symbol) with a bunch of question marks in it: "??? ???".

I have win7 installed on the drive that I want to install Ubuntu, and since the drive has only one partition (which houses win7 and is the partition that boots) I selected the option to "...run along side..." and moved the slider in order create a new linux partition (about 20Gb) on that drive. 

However, when the partitioning was done and I was about to select my timezone when I got the error... :( I had no choice but to click OK and the installation process jumped back to the first screen/phase. Any ideas? I mean, there isn't much that can go wrong here, is there? A win7 on one big partition...


I also tied to create the partitions manually (\, \home, swap) but then the installation just hangs at the text "**[COLOR=Magenta]ready when you are[/COLOR]**". Here I just got to select my timezone and keyboard layout (it hangs on the keyboard layout, so it is not the uppercase-login-name-error).




I installed from a USB-stick. 64-bit.

Please help, I really want to get going with this dual booting thing.
Thanks.

@ the ready when you are prompt, click on the Forward button if it's  visible.  That's what I did and it worked, not very obvious that that is  what one is meant to do.

---

### Post by &amp;Clyde on 2011-03-23
That I did. While the button was gray I could hit enter and see the "forward" button being pressed. Nothing happened.

---

### Post by Hakunka-Matata on 2011-03-23
Have you checked the Hash on your .iso file?  Or run the 'check CD for errors' in the Live CD Boot menu?

---

### Post by &amp;Clyde on 2011-03-23
> **Hakunka-Matata said:**
> Have you checked the Hash on your .iso file?  Or run the 'check CD for errors' in the Live CD Boot menu?

Did that check just now, seems to be ok.
Thanks.

---

### Post by Quackers on 2011-03-23
Have you started your username with a capital letter? No capitals allowed there.

Actually, if you are trying to install 10.10 and you have tried the "install alongside" option (which is not recommended!) you should first check whether Windows still boots ok. The install alongside option can cause serious problems in the 10.10 installer.
When you next try to install I would recommend that you use the "specify manually" option and create the partitions manually.

---

### Post by &amp;Clyde on 2011-03-23
> **Quackers said:**
> Have you started your username with a capital letter? No capitals allowed there.

Actually, if you are trying to install 10.10 and you have tried the "install alongside" option (which is not recommended!) you should first check whether Windows still boots ok. The install alongside option can cause serious problems in the 10.10 installer.
When you next try to install I would recommend that you use the "specify manually" option and create the partitions manually.


I didn't know it was not recommended. Luckily I can still use my win7. Btw, is it a bad idea to have the linux paritions on the same drive as my win7 partition? Also, could my additional RAID setup me giving problems (although it has nothing to do with the drive I try to install Ubuntu on)?

Nope, I did not get to the username part.

But as I said, I did try it the manual way, but then it just hangs on the "ready when you are" and I do not even get to the username selection process. :(

---

### Post by Quackers on 2011-03-23
Ok, so what is the last thing that you do before it stops, and what happens on the screen exactly?
Have you tried selecting "try ubuntu" and found out whether the live desktop loads?
If you try that go to System > Admin > gparted and see what it reports as your current partition structure. If you're not sure, post a screenshot of the gparted screen.
It may also be worth checking the cd for errors. At the first purple screen press any key, then choose language, then on the next screen choose the option to check for errors. You could have a bad burn of the image.

---

### Post by &amp;Clyde on 2011-03-23
> **Quackers said:**
> Ok, so what is the last thing that you do before it stops, and what happens on the screen exactly?
Have you tried selecting "try ubuntu" and found out whether the live desktop loads?
If you try that go to System > Admin > gparted and see what it reports as your current partition structure. If you're not sure, post a screenshot of the gparted screen.
It may also be worth checking the cd for errors. At the first purple screen press any key, then choose language, then on the next screen choose the option to check for errors. You could have a bad burn of the image.


Well, if i try the "alongside" option, I just get the ??? error when I'm about to select the timezone. On the manual bit I get a bit longer, I select the keyboard and in the message window I can see:

```
s.install (current: ubi-usersetup)
Ubuntu CRON [8597]: (root) CMD ( cd/ && run-parts -- report/etc/cron.hourly)
```[SIZE=2]

Yes, I can load the live CD. Browsed a bit using FF :)

I'll check the [/SIZE]partition structure later today.
[SIZE=2]
[/SIZE]

---

### Post by Quackers on 2011-03-23
If you are using raid0 it is possible that the installer cannot see your hard drives. Are you using raid0 or raid1 or something else. Is it bios raid or hardware controlled?
I elected to sack my bios raid array, as it seemed just too complicated to get it working :-)

---

### Post by &amp;Clyde on 2011-03-23
Forgot to mention that I could browse the ntfs RAID1 drive while in Live mode without problems. Could it still cause issues (even though I'm not installing Ubuntu onto this drive)?

Sorry, don't know the difference between BIOS and hardware RAID. I have no additional PCI cards or similar, just nVidia stuff from the motherboard/bios. Is this BIOS or hardware? ;)

---

### Post by Quackers on 2011-03-23
Yes, that would be what I call bios raid. Others insist on calling it fakeraid, for some reason.
From my limited experience with raid0 and raid1, I was under the impression that when using raid1 everything that is done to one drive is "mirrored" on the other drive. I wouldn't have thought that the same problems would exist for raid1 as exist for raid0, but I could be wrong :-)
I can't really advise any further as I selected non-raid when I started installing multiple distros on my laptop.
There is a wealth of information on raid and Linux, but it seems very confusing to me - especially when bios raid is being used.
Things are set to improve though, I believe. Ubuntu 11.04 is rumoured to be able to install on a bios raid raid0 system. We'll have to wait and see though :wink:

---

### Post by Hakunka-Matata on 2011-03-23
> **Quackers said:**
> Yes, that would be what I call bios raid. Others insist on calling it fakeraid, for some reason.
From my limited experience with raid0 and raid1, I was under the impression that when using raid1 everything that is done to one drive is "mirrored" on the other drive. I wouldn't have thought that the same problems would exist for raid1 as exist for raid0, but I could be wrong :-)
I can't really advise any further as I selected non-raid when I started installing multiple distros on my laptop.
There is a wealth of information on raid and Linux, but it seems very confusing to me - especially when bios raid is being used.
[COLOR=Red]Things are set to improve though, I believe. Ubuntu 11.04 is rumoure[/COLOR]d to be able to install on a bios raid raid0 system. We'll have to wait and see though :wink:

Slightly off topic, Not to do with RAID 0 &/or 1 but to do with the installer on the Desktop Alpha 3 ISO, It's finally working, a fix was implemented about the 15th of March, 2,011 which fixed the partitioning bug, and I've installed w/o problems both 11.04 32bit & 64bit Desktop Alpha3: systems. Heaps of updates are coming out almost daily, getting more stable all the time.
HK

---

### Post by &amp;Clyde on 2011-03-23
By the way. When I create the partitions manually. How should the be set up? Primary? Logical? Beginning? End? How about the number of partitions? Is it enough with a \, \home and swap?

How about the boot sector? Should it be on the drive itself or  in one of the partitions? On the win7 partition?


Thanks.

---

### Post by &amp;Clyde on 2011-03-23
Here is the partition structure of my drive, it\s on the unallocated part I try to install Ubuntu.

[IMG]http://img222.imageshack.us/img222/9572/74718085.png[/IMG]

---

### Post by Quackers on 2011-03-23
A / partiton, a /home partition and a swap partition are plenty :-) Partition types should be logical.
Grub is normally installed to the mbr of the drive (like /dev/sda or maybe /dev/sde). The default will be /dev/sda, which will often over-write Windows bootloader. This doesn't usually cause a problem as Windows can be booted from grub, but the mbr needs to be restored with a Windows repair cd or installation disc, should Ubuntu be removed from the system.
It is possible that the raid metadata on the HDD may cause the installer to have problems.

---

### Post by Hakunka-Matata on 2011-03-23
Available unallocated space is more or less 'small', but it will work for now.  Later you may have to resize some partitions.


[LIST]
[*]First make an extended partition out of all the unallocated space.
[*]2nd, make a swap partition with a size of 1.5GiB
[*]3rd, make a Logical partition with all remaining space, ext4 type with mount point of /
[/LIST]

I must learn to check if someone has posted while I'm making up a reply!!  Sorry Quackers........ HK

---

### Post by Quackers on 2011-03-23
No problem, 2 heads are usually better than one :wink:

---

### Post by &amp;Clyde on 2011-03-23
Thanks.
I got it working! I suppose it had to do with the partitions. I don't know exactly what I did differently (maybe that I selected the bootloader to root, read below).

However, as I did not read your replies before I tried to install, I selected the root partition (sde5) as the bootloader device. And now, (naturally, obviously :rolleyes:) I cannot boot into Ubuntu. Win7 just loads normally when I start my computer. 

What should I do? Make a fresh install with the plain "sde" as the bootloader?
What happens then? The computer simply loads GRUB and lets me select OS?
Is my MBR located on "sda"? As I see it my RAID drive is sda (and sdb). Shout I still use sda as my bootloader?

---

### Post by &amp;Clyde on 2011-03-23
> **Hakunka-Matata said:**
> Available unallocated space is more or less 'small', but it will work for now.  Later you may have to resize some partitions.


[LIST]
[*]First make an extended partition out of all the unallocated space.
[*]2nd, make a swap partition with a size of 1.5GiB
[*]3rd, make a Logical partition with all remaining space, ext4 type with mount point of /
[/LIST]

I must learn to check if someone has posted while I'm making up a reply!!  Sorry Quackers........ HK

Sorry, but what should the extended partition be mounted as? home?

---

### Post by Quackers on 2011-03-23
Which drive is set to boot first in your bios? I presume it is sde.

An extended partition is just a container for logical partitions and does not have a mount point.

I suggest that you boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then we can see where your Linux partitions are and give you a command to install grub to the mbr of the appropriate drive.

---

### Post by &amp;Clyde on 2011-03-23
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sde
 => Syslinux is installed in the MBR of /dev/sdf
 => No known boot loader is installed in the MBR of /dev/mapper/nvidia_dcgahedi

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sde2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

nvidia_dcgahedi1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

nvidia_dcgahedi2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

nvidia_dcgahedi5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, 
                       nvidia_dcgahedi5 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

nvidia_dcgahedi6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, 
                       nvidia_dcgahedi6 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sde2             206,848   940,806,950   940,600,103   7 HPFS/NTFS
/dev/sde3         940,808,190   976,771,071    35,962,882   5 Extended
/dev/sde5         940,808,192   954,478,591    13,670,400  83 Linux
/dev/sde6         954,480,640   966,197,247    11,716,608  82 Linux swap / Solaris
/dev/sde7         966,199,296   976,771,071    10,571,776  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63    15,654,239    15,654,177   c W95 FAT32 (LBA)


Drive: nvidia_dcgahedi ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_dcgahedi: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_dcgahedi1                 63    78,140,159    78,140,097   7 HPFS/NTFS
/dev/mapper/nvidia_dcgahedi2         78,333,001 1,953,520,064 1,875,187,064   f W95 Ext d (LBA)
/dev/mapper/nvidia_dcgahedi5         78,333,003   657,154,889   578,821,887   7 HPFS/NTFS
/dev/mapper/nvidia_dcgahedi6        678,135,843 1,953,520,064 1,275,384,222   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_dcgahedi1 66480567480536F9                       ntfs       HD1_RAID                   
/dev/mapper/nvidia_dcgahedi5 441406AF1406A3D0                       ntfs       HD2_RAID                    
/dev/mapper/nvidia_dcgahedi6 D4AC08A9AC0887E6                       ntfs       HD3_RAID                    
/dev/mapper/nvidia_dcgahedi: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sde1        58602D50602D35E2                       ntfs       System Reserved               
/dev/sde2        7CC83070C8302AB2                       ntfs                                     
/dev/sde3: PTTYPE="dos" 
/dev/sde5        d89ab5e1-5cf8-47d7-8b04-f0971b118aa8   ext4                                     
/dev/sde6        6f67198e-a454-4fa3-9198-3f92909919bd   swap                                     
/dev/sde7        95ff748a-e542-471d-841c-17347bda890a   ext4                                     
/dev/sde: PTTYPE="dos" 
/dev/sdf1        1CE0-1B22                              vfat       PENDRIVE                      
/dev/sdf: PTTYPE="dos" 
error: /dev/mapper/nvidia_dcgahedi2: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_dcgahedi
nvidia_dcgahedi1
nvidia_dcgahedi5
nvidia_dcgahedi6

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos5)'
search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
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
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d89ab5e1-5cf8-47d7-8b04-f0971b118aa8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=d89ab5e1-5cf8-47d7-8b04-f0971b118aa8 ro single 
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
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos5)'
    search --no-floppy --fs-uuid --set d89ab5e1-5cf8-47d7-8b04-f0971b118aa8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 58602d50602d35e2
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=d89ab5e1-5cf8-47d7-8b04-f0971b118aa8 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sde7 during installation
UUID=95ff748a-e542-471d-841c-17347bda890a /home           ext4    defaults        0       2
# swap was on /dev/sde6 during installation
UUID=6f67198e-a454-4fa3-9198-3f92909919bd none            swap    sw              0       0

=================== sde5: Location of files loaded by Grub: ===================


 483.1GB: boot/grub/core.img
 486.7GB: boot/grub/grub.cfg
 483.5GB: boot/initrd.img-2.6.35-22-generic
 483.1GB: boot/vmlinuz-2.6.35-22-generic
 483.5GB: initrd.img
 483.1GB: vmlinuz

=========================== sdf1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu in text mode" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntu.seed quiet --
    initrd    /install/initrd.gz
}
menuentry "Install in expert mode" {
    set gfxpayload=keep
    linux    /install/vmlinuz  file=/cdrom/preseed/ubuntu.seed priority=low --
    initrd    /install/initrd.gz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Rescue a broken system" {
    set gfxpayload=keep
    linux    /install/vmlinuz  rescue/enable=true --
    initrd    /install/initrd.gz
}

=================== sdf1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/mapper/nvidia_dcgahedi

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  28 0b c9 0f 00 00 00 01  |........(.......|
000001c0  01 00 07 fe ff ff 3f 00  00 00 c1 52 a8 04 00 fe  |......?....R....|
000001d0  ff ff 0f fe ff ff 49 44  ab 04 78 15 c5 6f 00 00  |......ID..x..o..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sde3

00000000  ac 62 f8 7f 2d b6 67 64  e2 2a 9d 18 d1 fd e5 66  |.b..-.gd.*.....f|
00000010  51 7d a9 99 3d 7d e1 01  ab b8 0e 6e 92 07 5d 85  |Q}..=}.....n..].|
00000020  00 d7 10 81 70 62 df 78  66 1e 67 91 9d d6 9a f4  |....pb.xf.g.....|
00000030  b8 68 9a 88 91 64 a3 26  61 48 39 ae 6d e6 ee 0a  |.h...d.&aH9.m...|
00000040  09 78 4f 50 47 10 11 12  c5 41 58 c6 d2 f1 df 98  |.xOPG....AX.....|
00000050  23 11 90 0c f7 35 f1 8d  cd ad 91 1a 3a de 67 69  |#....5......:.gi|
00000060  06 4e 6d 8d 57 f2 81 9e  b6 d3 49 3a 67 a2 fd 71  |.Nm.W.....I:g..q|
00000070  a8 56 de d2 7d 63 20 56  f3 18 d5 cd e6 0e a3 57  |.V..}c V.......W|
00000080  06 02 6b 72 61 af 71 be  e2 71 10 c7 2c bb c9 c5  |..kra.q..q..,...|
00000090  d1 4d e7 07 0e 49 48 73  cf 44 d8 3b d3 51 fb 92  |.M...IHs.D.;.Q..|
000000a0  71 ea fb ca 70 97 1b e7  d6 ec c2 59 ef a6 9d bd  |q...p......Y....|
000000b0  a4 1c 66 67 64 c6 45 d6  4b b2 de 43 b0 ba c1 d6  |..fgd.E.K..C....|
000000c0  d3 6d 1b e8 59 1b 3a e2  af bd 3a 7c 2c f6 23 a4  |.m..Y.:...:|,.#.|
000000d0  cd 7d 9e 91 4e 9e 9f cd  99 03 c2 fe 9e 22 ea 6d  |.}..N........".m|
000000e0  16 a9 a3 ca 3a d2 a9 ab  99 7f 72 4f 27 5e 9c 55  |....:.....rO'^.U|
000000f0  39 bf db 9a bb b7 b7 45  6c ba 1c a6 06 8a 6c 98  |9......El.....l.|
00000100  09 78 52 9e 47 10 11 13  58 dc 93 50 0e 4c 46 fa  |.xR.G...X..P.LF.|
00000110  06 12 69 a9 c8 d0 9a 2b  93 8a d3 b6 91 01 3b 24  |..i....+......;$|
00000120  e4 a0 2c 29 c7 fe 54 99  76 3b ce 3f f8 89 49 cb  |..,)..T.v;.?..I.|
00000130  ab e6 92 69 3a 74 05 1d  f6 25 74 dd 66 b1 90 fc  |...i:t...%t.f...|
00000140  ef 23 b5 78 dd 48 0b 12  e9 93 a5 de 2d 5e 06 08  |.#.x.H......-^..|
00000150  bc c7 64 4a 59 a1 69 0f  8b ca 7a be a2 b8 6a 01  |..dJY.i...z...j.|
00000160  3d 0f f8 13 fc 1a cb 4d  c0 57 0d 2d 58 c7 de 98  |=......M.W.-X...|
00000170  cd d2 c9 11 21 21 e7 6e  6b c3 7c c7 a1 96 d7 9d  |....!!.nk.|.....|
00000180  34 26 e9 d7 fc 65 cd 29  1a 49 2d cf 32 84 ff b5  |4&...e.).I-.2...|
00000190  20 a7 f7 f9 76 7a b1 93  63 72 5a b6 a1 6f 0f 14  | ...vz..crZ..o..|
000001a0  5d 64 17 52 a7 48 a4 e9  29 ba 3b 79 8b d6 6a 79  |]d.R.H..).;y..jy|
000001b0  a9 9a a7 1c fd ab 3f 6d  b8 8f 59 32 a3 15 00 ef  |......?m..Y2....|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 98 d0 00 00 ef  |................|
000001d0  ff ff 05 ef ff ff 72 9e  d0 00 90 c9 b2 00 00 00  |......r.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdf1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  21 dd ee 00 f8 76 00 00  00 00 00 00 02 00 00 00  |!....v..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 22 1b e0 1c 4e  4f 20 4e 41 4d 45 20 20  |..)"...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 14  ee 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on nvidia_dcgahedi2



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd 
=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/nvidia_dcgahedi2: No such file or directory
hexdump: /dev/mapper/nvidia_dcgahedi2: No such file or directory

```



Thanks!

---

### Post by Quackers on 2011-03-23
Just for clarification, which drive is set to boot first in the bios?
Where are drives sda, sdb, sdc, sdd?
Which drives are included in a raid array?

---

### Post by &amp;Clyde on 2011-03-23
> **Quackers said:**
> Just for clarification, which drive is set to boot first in the bios?
Where are drives sda, sdb, sdc, sdd?
Which drives are included in a raid array?


sde boots first.
sda and sdb are the RAID
sdf is the usb

sdc and sdd.. they show up as "Genreic Flash HS-COMBO" and "Genreic Flash HS-CF"... Dell monitor card readers.

---

### Post by Quackers on 2011-03-23
Ok, thanks.
From the live desktop please open a terminal and copy/paste the following commands in, one line at a time, pressing enter after each line.
```
sudo mount /dev/sde5 /mnt
sudo grub-install --root-directory=/mnt /dev/sde
```
If no errors are reported, you can then reboot. Ubuntu should now boot directly. If it does, open a terminal and run this ```
sudo update-grub
```and watch as grub.cfg is run. You should see it find the Windows loader. If it does, reboot and choose Windows from the new grub menu. If that boots ok, you're good!

---

### Post by &amp;Clyde on 2011-03-23
I got this warning when running the grub/install:

```
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.

```

Is this OK?

---

### Post by Quackers on 2011-03-23
Sorry for the dealy. Yes, it should be ok. FlexNet is a damned nuisance, but I believe that grub can now work around it.

---

### Post by &amp;Clyde on 2011-03-23
Wow, everything is working as it should.
Thank you all, you have been most helpful. One more Linux desktop user has been added. ;)

---

### Post by Quackers on 2011-03-23
Excellent :-) Well done! Have fun!
Can you please mark the thread as solved, using the Thread Tools at the top of the page? Thanks.

---

