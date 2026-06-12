---
title: "Grub installed on wrong HDD"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Gurrrh on 2010-05-26
Ok

I have 2 hard drives 1 x 250 GB and 1 x 100 GB

The 100 GB one is a old backup hardrive that had Win XP and Mandriva as dual boot.

The 250 GB one has Windows 7 Home Premium and I recently installed Ubuntu 10.04 LTS.

Now I accidently had my old backup drive connected via USB while I was installing Ubuntu.

Now it turns out the grub is looking for my backup hard drive in order to show the Grub selection menu. Most of the time when this back up hard drive is connected it is fine and I can boot into Windows 7 or Ubuntu. However intermitently is does and shows

error device not found UUID (of one of the partitions on the 100 GB back up HDD)
> grub Rescue


Of course without the backup hdd connected it always shows the above.

How do I sort this so the grub is on my primary 250 HDD and just has the Windows 7 and Ubuntu choices.

My partitions are as follows:

For 250 GB HDD: (sda)

/dev/sda1: Windows 7 bootable 100MB ntfs
/dev/sda2: Contains windows 7 files 
such as users program files 136.2 GB ntfs
/dev/sda3: unknown 21.0 GB(suspect FAT 16 from Disk Util in Ubuntu)
/dev/sda4: 69.6 GB ntfs
free space 23.1 GB

For 100 GB HDD (back up HDD) (sdb)

/dev/sdb1/ ntfs bootable Windows XP (lba)
/dev/sdb2/ extended 39.45GB
  /dev/sdb5/ ext3 18.21GB
  /dev/sdb7/ ext4 16.74GB
  unallocated 1.0MB
  /dev/sdb8/ linux-swap 793.00 MB (suspect DVD Drive ?)
  /dev/sdb6/ linux swap  3.72 GB
  
One of the sdb's above has the same UUID as what the grub loader is looking for.

Just a few points to note:
At present although I can boot into Ubuntu 10.04 I cannot connect to the internet as wireless is my only option and the drivers for this need downloading and installing.

I don't have the Win 7 DVD yet but do have the Ubuntu 10.04 Live CD

Any help much appreciated.

Thanks

Gurrrh

---

### Post by darkod on 2010-05-26
You said ubuntu is installed on the 250GB with win7 if I understood correctly.

But in the partitions list you specified there is no single linux partition on that disk.

I think ubuntu might have actually installed on /dev/sdb7. What is that ext4 partition?

That is why if the disk is not plugged in, grub2 is not working. Its config files are obviously on the root partition and it can't work without the 100GB disk.

---

### Post by Gurrrh on 2010-05-27
Thanks for the help Darkod.

I was wondering myself where Ubuntu 10.04 is installed. The ext3 and 4 partitions where created when I put XP and Mandriva on as dual boot a year ago. I have put this backup drive back in and it does boot to grub with a choice of XP or Mandriva so it doesn't appear to be affected.

Is there any command I can use to find out which drive Ubuntu is installed on if it is. Is it possible to uninstall unbuntu to go back to just having Win7? at least to try the install again without my backup being connected this time!

many thanks

---

### Post by darkod on 2010-05-27
To give us better view of the boot process, run this script with both disks connected.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Post the content of the results file as explained. Then we will know more.

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Gurrrh on 2010-05-27
Darkod,

Looks like you were right and Ubuntu is installed on my backup hdd on /dev/sdb7 ext 4 which is the same UUID as what grub is looking for on boot.

Below is the script results:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.1 
                       (Official) for i586 Kernel 2.6.29.1-desktop586-4mnb on 
                       a Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Windows XP
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   266,242,047   266,035,200   7 HPFS/NTFS
/dev/sda3         266,242,048   307,202,047    40,960,000   6 FAT16
/dev/sda4         307,202,048   443,189,247   135,987,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   112,631,714   112,631,652   7 HPFS/NTFS
/dev/sdb2         112,631,776   195,366,464    82,734,689   f W95 Ext d (LBA)
/dev/sdb5         112,631,778   150,817,121    38,185,344  83 Linux
/dev/sdb6         187,558,938   195,366,464     7,807,527  82 Linux swap / Solaris
/dev/sdb7         150,818,816   185,931,775    35,112,960  83 Linux
/dev/sdb8         185,933,824   187,557,887     1,624,064  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D48C9DE18C9DBE84                       ntfs                                     
/dev/sda2        D034A3C834A3AFC0                       ntfs                                     
/dev/sda4        2CBCFFE7BCFFAA0A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14281FE4281FC420                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        f23b0800-9d5d-4aa4-9470-6a43f635cd0c   ext3                                     
/dev/sdb6        c4ef0514-7867-4895-a2de-8373295c58bb   swap                                     
/dev/sdb7        3b45a549-5402-4661-8ac7-944e351d8e27   ext4                                     
/dev/sdb8        7ef886c1-a656-43d5-a418-cf1638b1b283   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb7        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/14281FE4281FC420  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/f23b0800-9d5d-4aa4-9470-6a43f635cd0c ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/D034A3C834A3AFC0  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

=========================== sdb5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 3

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c 
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c failsafe
initrd (hd0,4)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title desktop586 2.6.29.1-4mnb
kernel (hd0,4)/boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.29.1-desktop586-4mnb.img

title desktop586 2.6.31.12-1mnb
kernel (hd0,4)/boot/vmlinuz-2.6.31.12-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.31.12-1mnb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
initrd (hd0,4)/boot/initrd-2.6.31.12-desktop586-1mnb.img

=============================== sdb5/etc/fstab: ===============================

# Entry for /dev/sda5 :
UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c / ext3 defaults 1 1
none /proc proc defaults 0 0

=================== sdb5: Location of files loaded by Grub: ===================


  57.8GB: boot/grub/menu.lst
  57.8GB: boot/grub/stage2
  57.7GB: boot/initrd-2.6.29.1-desktop586-4mnb.img
  57.8GB: boot/initrd-2.6.31.12-desktop586-1mnb.img
  57.8GB: boot/initrd-desktop586.img
  57.8GB: boot/initrd.img
  57.8GB: boot/vmlinuz
  57.8GB: boot/vmlinuz-2.6.29.1-desktop586-4mnb
  57.8GB: boot/vmlinuz-2.6.31.12-desktop586-1mnb
  57.8GB: boot/vmlinuz-desktop586

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3b45a549-5402-4661-8ac7-944e351d8e27 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=3b45a549-5402-4661-8ac7-944e351d8e27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set 3b45a549-5402-4661-8ac7-944e351d8e27
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d48c9de18c9dbe84
	chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 14281fe4281fc420
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "linux (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
	initrd (hd0,4)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	initrd (hd0,4)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c failsafe
	initrd (hd0,4)/boot/initrd.img
}
menuentry "desktop586 2.6.29.1-4mnb (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	linux /boot/vmlinuz-2.6.29.1-desktop586-4mnb BOOT_IMAGE=desktop586_2.6.29.1-4mnb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
	initrd (hd0,4)/boot/initrd-2.6.29.1-desktop586-4mnb.img
}
menuentry "desktop586 2.6.31.12-1mnb (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set f23b0800-9d5d-4aa4-9470-6a43f635cd0c
	linux /boot/vmlinuz-2.6.31.12-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.31.12-1mnb root=UUID=f23b0800-9d5d-4aa4-9470-6a43f635cd0c splash=silent vga=788
	initrd (hd0,4)/boot/initrd-2.6.31.12-desktop586-1mnb.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=3b45a549-5402-4661-8ac7-944e351d8e27 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=7ef886c1-a656-43d5-a418-cf1638b1b283 none            swap    sw              0       0

=================== sdb7: Location of files loaded by Grub: ===================


  81.6GB: boot/grub/core.img
  86.5GB: boot/grub/grub.cfg
  81.6GB: boot/initrd.img-2.6.32-21-generic
  81.6GB: boot/vmlinuz-2.6.32-21-generic
  81.6GB: initrd.img
  81.6GB: vmlinuz

---

### Post by darkod on 2010-05-27
Yes, it's installed on /dev/sdb7.

Now it's up to you what you want to do.

---

### Post by Gurrrh on 2010-05-27
Ok,

What I would like to do is install this onto the current 250GB HDD and obviously change the grub to boot without having the other backup HHD connected as the process is intermittment. Sometimes even with the HDD connected at startup it doesn't recognise the drive and it seems to be pot luck if I get the grub selection up at all.

How best would it be to do this?

I could put the live CD in and install Ubuntu into one of the partitions on the 250 GB but I remember when I tried this before I am where I am now it recognised Windows 7 loader but only gave me the option of wipe entire disk or manually configure partitions. Without some help on the latter I don't feel confident enough to try. Could anyone help on how I would manually do it without affecting the Windows 7 partitions?

thanks for the help so far.

Alternatively, I could install Ubuntu as above move the grub loader somehow on to my 250GB so it would give me a choice of Win 7 or Ubuntu, but if I connected my USB drive also extra choices between Win XP and Mandriva without the grub not working (I realise Ubuntu is available here too which presumably I can uninstall to avoid confusion)

This way I wouldn't have to keep unscrewing my laptop and take out my 250 and put 100GB in if I needed to boot into XP sometimes. I could just do it by USB connection. Unfortunately I have an older computer than doesn't support USB boot up. I didn't realise that although I made a mistake on what I have done it has shown me an advantage!

---

### Post by darkod on 2010-05-27
It only gave you the option to wipe the disk or use manual partitioning because you already have 4 primary partitions on the disk, and that is the limit.

What I would do is: move the data from /dev/sda4 to the backup hdd, delete /dev/sda4 and create extended partition in its place. Inside an extended partition you can have more logical partitions, and this is how you can have more than 4 partitions on the disk.

Note that in windows the partition is not called /dev/sda4, I am using linux terms now, and you should start learning them too (if you don't know them yet :) ). That partition is around 60GB in size.

If you can give all that size to ubuntu, even better and easier to install. If you still need to use part of that partition as ntfs so windows can see it and keep data there, it can be done too.

BEFORE YOU START: Copy all data you need from that partition. When deleting the partition ALL DATA WILL BE LOST!!! After you have copied the data disconnect the backup disk to avoid confusion if it's connected.

Option 1: You can give those 60GB to ubuntu and keep the data you copied on another disk or partition.

In this case it is very easy to install. Boot windows, open Disk Management and delete the 60GB partition. Do not create any partition in that space from windows, leave it as unallocated.
Boot with the ubuntu cd, start the installer and in step 4 select Use Largest Available Free space. This time because you will have unallocated space that option will be present. That will install ubuntu into the unallocated space.
And that's all you need to do.

Option 2: You have to use part of the 60GB for windows data too, as ntfs partition.

In that case lets split it 50/50, 30GB for ubuntu, 30GB for windows.
Boot the ubuntu cd in live mode, and use Gparted to delete the /dev/sda4 partition. Then in the unallocated space create new logical ntfs partition of 30GB. It should be named automatically /dev/sda5 because it's logical.
Then start the installer (you can do it from the Install icon on the live desktop), and again use the Use Largest Available Free space option. This time ubuntu will be installed in the 30GB that remained after you created one 30GB ntfs partition.

In my opinion option 1 is better because it gives you more space for working with ubuntu. But it all depends what data you have now in that 60GB partition and whether you can keep it somewhere else.

PS EDIT: Lets sort out the internal installation first. After that if you want to boot XP from usb, no problem. First you will boot your ubuntu which now will be on the internal disk. Then plug in the usb disk and just run:

sudo update-grub

to detect the XP and Mandriva on the usb disk. It will add them to the boot menu and because your ubuntu is installed on the internal grub will always work even with the usb hdd disconnected. But of course you will only be able to boot XP and Mandriva from the menu if you have the disk connected.

---

### Post by Gurrrh on 2010-05-27
Thanks for the clear advice Darkod!

I have done this (option1) and everything works fine. Just one final question. How do I configure the default operating system Grub uses and time limit etc.

Well done and thanks! I no longer have to swap hard drives now thanks to updating the grub too!!

---

### Post by darkod on 2010-05-27
In your case, with actually 4 OSs, I think the best would be to install the package Startup Manager.

sudo apt-get install startupmanager

I don't use it and don't know exactly where it will be after the install, maybe in System-Administration. Look around.

With that package you can easily set timeout and default OS.

I use direct editing of the grub2 config file, but for 4 OSs startupmanager might be better.

PS. We forgot to mention but now you can delete the ubuntu partition created on the external disk. And then you can use that space to create ntfs partition for example, which you can use from both windows and linux. You make sure you delete the correct one, not Mandriva. :)

Also, if you ran update-grub it might have detected the ubuntu on the external disk too. Just run update-grub again after you delete the partition and it will remove it from the menu.

---

### Post by drs305 on 2010-05-27
StartUp-Manager will be available under System, Administration, StartUp-Manager once it's installed.

---

