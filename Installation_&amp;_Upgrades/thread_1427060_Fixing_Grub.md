---
title: "Fixing Grub"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by TutAmongUs on 2010-03-11
Hi guys,

  First post, but not new to Linux or Ubuntu.

  I set my drives up with MY boot loader, and I boot several OSes.  I installed Ubuntu and told it to place grub on the / drive, which is where I always put it with any other install and it works fine.  I find now that despite telling the install where to put it, you guys have taken it upon yourselves to alter the MBR of the volume ANYWAY!

  That is not too bright.

  SO, what I need to do is re-install grub, but I see that you also have no repair facility on this disc either.  All I want to do is use MY boot loader.  Currently, when I point at the / volume it just hangs with a non-blinking cursor in the upper left.  No other Linux installs I have performed over the years do this.  I want the drive to boot by merely pointing my bootloader at that volume.  It always has in the past, so what did you guys change?  I want NO action on my MBR, but I DO want a working grub on the actual root volume, which is NOT the first volume on the drive.

---

### Post by dstew on 2010-03-11
My understanding is that if you direct grub-install to a drive, the boot loader goes into the MBR, but if you direct it to a partition, the loader goes into the boot record of the partiton. So, if you do```
grub-install /dev/sda
```the boot loader goes into the MBR. But if you do```
grub-install /dev/sda1
```the boot loader goes into the boot record of the partition. I think if you do not put an argument with grub-install, the boot loader goes to the MBR of the first disk by default.

---

### Post by WaveRunner on 2010-03-11
dstew:
I am new to these foreums so bear with me!  I had posted a thread yesterday on how to install Grub Legacy after installing W XP.  I think I have the right number of partitions?  No files I have to worry about destroyin and no LiveUsb possible.  I have downloaded the alt-iso of zubuntu 9.04 and Grub Legacy 0.97 and unzipped.  But these files are to burn a cd with and do install.  I don't have a cd burner.  So my questions are:  1)  Can I use thes files anyway and install manually into the correct partitions?  2)  You had indicated to TutAmongUs above writing code...where and how do you write this code?  Via Grub on a Flopp or CD (cd is not an option)  and can I use Windows XP Cosole to write code?  Or do I write directly into Widows boot.ini file?  Thanks!  I did post a thread in more detail earlier in the General Area.  -WaveRunner

---

### Post by dstew on 2010-03-11
WaveRunner, please create a new thread in the Installation and Upgrades forum and post your question there. Thanks.

---

### Post by TutAmongUs on 2010-03-11
> **dstew said:**
> My understanding is that if you direct grub-install to a drive, the boot loader goes into the MBR, but if you direct it to a partition, the loader goes into the boot record of the partiton. So, if you do```
grub-install /dev/sda
```the boot loader goes into the MBR. But if you do```
grub-install /dev/sda1
```the boot loader goes into the boot record of the partition. I think if you do not put an argument with grub-install, the boot loader goes to the MBR of the first disk by default.

  Thanks.  I will attempt an install from command line. That is going to be kind of difficult since it will not boot!  So, do I have to chroot after booting the Ubuntu disc again, and install it from there?  As it stands, I have no way of booting that volume, because there is no such menu choice available.  I suppose I could edit the boot command and point to the drive.  This install behavior is sad, and should not be taking place.

 I notice that Ubuntu has decided to NOT have any sort of repair facility in place on the install disc either.

  It was installed by the installation script on the install disc.  It asks, and I elected to place it at/on the root/boot drive volume.  It is the third volume of my machine. I am absolutely certain that I made the correct choice, because I have done it so many times before.  It installed fine (Ubuntu), and booted fine, except that I knew immediately that it had wiped my MBR and put a piece of grub there.  That is a really STUPID paradigm for Ubuntu to follow.  If a user ALREADY HAS a boot loader installed and wants to use THAT boot loader, the selection of placing grub in an other than MBR location should be enough of a clue that they should NOT be doing ANYTHING with the danged MBR!  It goes beyond stupid when I put MY bootloader back and point to where I told Ubuntu to put grub, it is NOT there!

  So yeah, I have serious doubts that a command line install would have enough brains to pay attention to the user's choices either!  Grub has become pathetic, or Ubuntu has, because NONE of my 40 or so previous installs of various distros EVER had this problem.  I guess that I should have NOT trusted Ubuntu to honor my friggin selections!
AND NO, calling it and Ubuntu stupid is NOT disrespect OR a violation of the forum policy, because it happens to be FACT if they cannot even get their install script drafted accurately, and functioning properly.

---

### Post by presence1960 on 2010-03-11
Why don't you let us see exactly your setup & boot process before you make any changes? Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by TutAmongUs on 2010-03-11
> **presence1960 said:**
> Why don't you let us see exactly your setup & boot process before you make any changes? Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

  It appears that you did not read my post very well.  I did not say that Ubuntu would not or did not install.  Ubuntu runs fine.  It ran fine once I installed it.  THE PROBLEM is that despite my choosing the grub install location as being the / drive (dev/sda3), as was provided by an option selection, grub decided to modify my MBR anyway, and from all the reading on Ubuntu's help site, it does it no matter what drive you select to put it on, because that is what "grub-setup" does and no command line option stops it from doing it.  It makes me wish I still had one of those motherboards that curtail MBR writes.
<snip>

  I have been using XOSL for years, and have NEVER had a problem.  I also had no problem putting it back.  NOW, I want to get grub working AT THE LOCATION I TOLD IT TO INSTALL TO.  Since all the reading I have done tells me that it will again TRASH MY MBR AND again fail if I overwrite it, tells me that the new grub crew has no clue about the application they are working on.  So SOMEBODY needs to review this issue, and then FIX it, befcause there is NO REASON for grub to FORCE an MBR modification.  NONE WHATSOEVER!

---

### Post by presence1960 on 2010-03-12
> **TutAmongUs said:**
> It appears that you did not read my post very well.  I did not say that Ubuntu would not or did not install.  Ubuntu runs fine.  It ran fine once I installed it.  THE PROBLEM is that despite my choosing the grub install location as being the / drive (dev/sda3), as was provided by an option selection, grub decided to modify my MBR anyway, and from all the reading on Ubuntu's help site, it does it no matter what drive you select to put it on, because that is what "grub-setup" does and no command line option stops it from doing it.  It makes me wish I still had one of those motherboards that curtail MBR writes.

<snip>

  I have been using XOSL for years, and have NEVER had a problem.  I also had no problem putting it back.  NOW, I want to get grub working AT THE LOCATION I TOLD IT TO INSTALL TO.  Since all the reading I have done tells me that it will again TRASH MY MBR AND again fail if I overwrite it, tells me that the new grub crew has no clue about the application they are working on.  So SOMEBODY needs to review this issue, and then FIX it, befcause there is NO REASON for grub to FORCE an MBR modification.  NONE WHATSOEVER!

I did read your post very well. In order to fix your problem you need to see your boot process and any and all locations of GRUB and/or any bootloaders. This would be the wise thing to do before changing anything. The boot info script will shed light on that as well as many other things to do with setup & boot process. Maybe you should run it and diagnose your problem instead of complaining about ubuntu. With the above attitude I have no interest in helping you.

You must be reading the wrong info then!

---

### Post by presence1960 on 2010-03-12
here is my setup & boot process. I have not a standard installation and multi boot. I installed in this order, karmic, mint 8, vista, sabayon & lucid.

karmic's install put GRUB on MBR. other than Vista over writing GRUB on MBR (which I promptly fixed) I had no problem with Lucid, mint or sabayon messing with the MBR. BTW lucid is ubuntu and mint is ubuntu based. I also have wubi installed for testing & learning about wubi.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 325098505 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   146,801,969   146,801,907   7 HPFS/NTFS
/dev/sda2         146,801,970   396,371,744   249,569,775   5 Extended
/dev/sda5         146,802,033   209,712,509    62,910,477  83 Linux
/dev/sda6         209,712,573   272,623,049    62,910,477  83 Linux
/dev/sda7         272,623,113   335,533,589    62,910,477  83 Linux
/dev/sda8         335,533,653   343,935,584     8,401,932  82 Linux swap / Solaris
/dev/sda9         343,935,648   396,371,744    52,436,097  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009028

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,048,578,614 1,048,578,552  83 Linux
/dev/sdc2       1,048,578,615 1,258,291,124   209,712,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       be56ee14-353d-4f00-af8b-577fe3f0bbbe   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        1E47E31A54CBB211                       ntfs       vista                         
/dev/sda5        101653d6-6dc9-4c4f-8487-eee283357676   ext4       mint                          
/dev/sda6        e0b415e6-168b-49e7-b62b-0fc42c83a6d7   ext4       karmic                        
/dev/sda7        35f50606-c5dc-4981-b609-cc08aa8aa6ef   ext4       sabayon                       
/dev/sda8        e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8   swap                                     
/dev/sda9        b732f52f-9f80-4272-8db0-8e586348ac14   ext4       lucid                         
/dev/sdb1        bd4ff60f-606d-43ac-81f2-6713bed14313   ext4       backup                        
/dev/sdc1        a9ce88a4-7a81-492e-958c-75ed13b54e0a   ext4       data                          
/dev/sdc2        790BFB1526B4964C                       ntfs       win-data                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/data              ext4       (rw,nosuid,nodev,uhelper=devkit)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Other Operating System - Microsoft Windows (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   3.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   3.5GB: boot/initrd.img-2.6.31-19-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   3.1GB: boot/vmlinuz-2.6.31-19-generic
   3.5GB: initrd.img
    .8GB: initrd.img.old
   3.1GB: vmlinuz
   2.3GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0452923552922c04
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=101653d6-6dc9-4c4f-8487-eee283357676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  78.9GB: boot/grub/core.img
  80.8GB: boot/grub/grub.cfg
  81.5GB: boot/initrd.img-2.6.31-17-generic
  76.2GB: boot/vmlinuz-2.6.31-17-generic
  81.5GB: initrd.img
  76.2GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
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
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-19-generic
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
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Other Operating System - Microsoft Windows (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	linux /boot/vmlinuz-2.6.32-14-generic root=/dev/sda9
	initrd /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 110.4GB: boot/grub/core.img
 112.2GB: boot/grub/grub.cfg
 120.3GB: boot/initrd.img-2.6.31-19-generic
 124.4GB: boot/initrd.img-2.6.31-20-generic
 115.6GB: boot/vmlinuz-2.6.31-19-generic
 113.5GB: boot/vmlinuz-2.6.31-20-generic
 124.4GB: initrd.img
 120.3GB: initrd.img.old
 113.5GB: vmlinuz
 115.6GB: vmlinuz.old

========================== sda7/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/kernel-genkernel real_root=/dev/sda7
#          initrd /boot/initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sda7
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd0,6)/boot/grub/splash.xpm.gz


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Other Operating System - Microsoft Windows
	rootnoverify (hd7,0)
	chainloader +1
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefault
title=Sabayon Linux (kernel-genkernel-x86_64-2.6.32-sabayon)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
	savedefault


=============================== sda7/etc/fstab: ===============================

/dev/sda7               /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sda8               swap                    swap    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


 157.6GB: boot/grub/grub.conf
 157.6GB: boot/grub/menu.lst
 166.4GB: boot/grub/stage2
 166.6GB: boot/initramfs-genkernel-x86_64-2.6.31-sabayon
 166.6GB: boot/initramfs-genkernel-x86_64-2.6.32-sabayon

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b732f52f-9f80-4272-8db0-8e586348ac14 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 195.6GB: boot/initrd.img-2.6.32-14-generic
 195.5GB: boot/vmlinuz-2.6.32-14-generic
 195.6GB: initrd.img
 195.5GB: vmlinuz

=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

If you have it working then what is the problem? Maybe you really don't know what you are doing. I chose to not install GRUB on mint & lucid and allow the bootloader (GRUB2) already on MBR handle those. Sabayon I had to install a bootloader so I put it in the boot sector of Sabayon's / directory. 

You are entitled to your opinion as I am entitled to mine. Whether my "friends" on here will bother to help is a matter strictly for them to decide. 

As for all the name calling I will pray for you because you really have an anger problem. Although I made reference to your attitude I did not personally attack you or throw names your way. Have fun with Ubuntu- it rocks!

---

### Post by presence1960 on 2010-03-13
[http://lindesk.com/2009/01/xosl-boot-loader-an-alternate-for-grub/](http://lindesk.com/2009/01/xosl-boot-loader-an-alternate-for-grub/)

[http://en.wikipedia.org/wiki/XOSL](http://en.wikipedia.org/wiki/XOSL)

After reading the above links and some others from a google search it is obvious the OP did not click the advanced button at the Ready to install window of the Live CD installer and choose where to install GRUB (i.e. /dev/sdXY). For if he/she did GRUB would not have touched the MBR because it would have been put onto the boot sector of that partition and the XOSL boot loader would have pointed to GRUB on that / partition. Case closed.

---

