---
title: "Dual boot: upgrading from W2K to XP ???"
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by jfl on 2010-07-23
I was running (happily) Lucid and W2K on separate hard drives.
The W2K is necessary to run our accountant program and only used for that.
Now he wants us to run Quickbooks 2010 that needs XP or W7. The hardware is not able to run W7 so I have to upgrade to Windoze XP.
I have no idea where to start.
The Ubuntu side runs perfect, the last thing I want is to compromise it.
I was thinking of unplugging the drive with Lucid on it, upgrade the drive with Windoze and reconnect The Lucid drive (which has GRUB).  It seems almost TOO easy :).
I don't want to run QB2010 in VirtualBox or other VM.

In short, I need to upgrade Windoze, leaving Ubuntu alone.

What is the best way of doing this ???

Thanks !

---

### Post by linux18 on 2010-07-23
Your suggestion was pretty much the best way to do it and if you already backed up W2K then go for it.
One thing you should do is use nlite on your ( assuming ) legal copy of xp and lighten it up a little, since your still running W2K (it is acctually very common to run 2k.. for the cheap system requirements ) you need all of the xp speed tweaks you can get ( nlite, reduce fonts, appearance settings, etc ) 
good luck

---

### Post by spydeyrch on 2010-07-23
You have the right idea. This is actually how I go about upgrading/installing new OSes. I have four HDD. 1TB & 3 x 500GB. My 1TB is for Win7, 500GB for Ubuntu 10.04, 500GB for Mint9, and the last 500GB is for a shared data drive.
   
  It is actually pretty simple to get everything done correctly.
   
  Here are some basic steps. If you have questions, just ask. Oh, and the steps are assuming you are running your HDD via SATA and not PATA (IDE). If they are IDE, seeing as you are running Win2K, let me know and I will change the steps accordingly.
  Windows = HDD1
  Ubuntu = HDD2
  1.)   Using nLite, as previously mentioned, create a slipstreamed WinXP CD that will include your machines needed drivers for its hardware as well as SP2 or SP3 and any other tweaks that you might want.
  2.)   Backup any and all files from your Win2k OS (i.e. music, pictures, documents, etc) to an external source, such as an external HDD, or to a DVD.
  3.)   Power down computer.
  4.)   Disconnect HDD2, either power or data or both. Doesn’t matter which as long as the computer can’t detect HDD2.
  5.)   Power on computer and via BIOS make sure that your ODD is in first place in your boot sequence because you will need to boot from your WinXP CD.
  6.)   Boot off of your slipstreamed WinXP CD and install.
  7.)   Update and install programs as wanted/needed.
  8.)   Once finished with install, power off the machine.
  9.)   Connect your HDD2 again.
  10.)  Power on the computer and enter the BIOS. Via the BIOS, make sure that HDD2 is the primary boot drive.
  11.)  Restart and boot into Ubuntu.
  12.)  Once logged in run this in a terminal:
  ```

  sudo update-grub2
  
```
  13.)  You should see the terminal window updating your grub.cfg file.
  14.)  Once completed, reboot your machine and you should see Windows as an option in your GRUB boot menu.
  15.)  Select it and viola! You should be able to now boot into both ubuntu and windows at the boot menu.
  Let me know if you need anything else.
   
  -Spydey :KS

---

### Post by jfl on 2010-07-23
Thanks for the detailed instructions.

What is a "slipstreamed XP CD"; is it something special to ***nlite*** ?

---

### Post by spydeyrch on 2010-07-23
> **jfl said:**
> Thanks for the detailed instructions.

What is a "slipstreamed XP CD"; is it something special to ***nlite*** ?

When you use nLite, the CD you create is a slipstreamed cd. 

Slipstreaming is the process by which you take drivers, service packs, and other files/tweaks typically not found on the XP install disk and basically "update" or create a customized XP install disk. The disk is customized for your specific hardware along with the tweaks that you added/removed.

Hopefully that is clear enough. :D

-Spydey :KS

---

### Post by jfl on 2010-07-23
Quite clear !
Thanks spydeyrch.

---

### Post by linux18 on 2010-07-23
nlite is sort of like the ubuntu customization kit and is great for creating a windows OS that is fast, lightweight, and stable out-of-the-box.

---

### Post by jfl on 2010-07-26
OK, got the brand new XP CD-ROM.
Unplugged the Ubuntu HD.
Boot show an error:

```
error: no such device 56145584-a886- (more numbers)............
grub rescue>
```

Rebooted, went in the BIOS, made sure the unplugged disk was "Not Installed", same error.
FWIW, both HD are IDE, not SATA.

Any advice ???          Thanks

---

### Post by jfl on 2010-07-26
Double post, sorry !

---

### Post by jfl on 2010-07-27
I just ran "bootinfoscript", here are the results.
Is it normal that grub 2 is installed on both HD ?


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,531,069    20,531,007  83 Linux
/dev/sda2         319,709,565   321,669,494     1,959,930  82 Linux swap / Solaris
/dev/sda3         195,318,270   310,118,759   114,800,490  83 Linux
/dev/sda4          20,531,070   194,964,839   174,433,770   f W95 Ext d (LBA)
/dev/sda5          20,531,133   194,964,839   174,433,707  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb3    *             63    15,117,164    15,117,102   7 HPFS/NTFS
/dev/sdb4          15,117,165    39,086,144    23,968,980   f W95 Ext d (LBA)
/dev/sdb5          15,117,228    22,523,129     7,405,902   7 HPFS/NTFS
/dev/sdb6          22,523,193    34,828,919    12,305,727   7 HPFS/NTFS
/dev/sdb7          34,828,983    38,925,494     4,096,512   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56145584-a886-415d-93a8-8bf6cdc8ac5d   ext3                                     
/dev/sda2        05cc57e2-3c56-4819-bb53-bfde34aed764   swap                                     
/dev/sda3        1cdc3133-5892-4966-a152-a7899e19a5ff   ext3                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        526c71f8-b5f8-499f-83c0-ea9da01f19a1   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb3        625C2B895C2B56D7                       ntfs                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        0F55E8CFB7705589                       ntfs       Apps                          
/dev/sdb6        AE8C31DC8C319FAF                       ntfs       Data                          
/dev/sdb7        4564-22DB                              vfat       FAT32                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /home                    ext3       (rw)
/dev/sda1        /boot                    ext3       (rw)


============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set 1cdc3133-5892-4966-a152-a7899e19a5ff
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
search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	linux	/vmlinuz-2.6.32-23-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro   quiet splash
	initrd	/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/vmlinuz-2.6.32-23-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	linux	/vmlinuz-2.6.32-22-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro   quiet splash
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/vmlinuz-2.6.32-22-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	linux	/vmlinuz-2.6.31-22-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro   quiet splash
	initrd	/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	echo	'Loading Linux 2.6.31-22-generic ...'
	linux	/vmlinuz-2.6.31-22-generic root=UUID=1cdc3133-5892-4966-a152-a7899e19a5ff ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 56145584-a886-415d-93a8-8bf6cdc8ac5d
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 2000 Professional (on /dev/sdb3)" {
	insmod ntfs
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set 625c2b895c2b56d7
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .0GB: grub/grub.cfg
    .5GB: initrd.img-2.6.31-22-generic
    .1GB: initrd.img-2.6.32-22-generic
    .1GB: initrd.img-2.6.32-23-generic
    .4GB: vmlinuz-2.6.31-22-generic
    .5GB: vmlinuz-2.6.32-22-generic
    .0GB: vmlinuz-2.6.32-23-generic

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=1cdc3133-5892-4966-a152-a7899e19a5ff /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=56145584-a886-415d-93a8-8bf6cdc8ac5d /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=526c71f8-b5f8-499f-83c0-ea9da01f19a1 /home           ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=05cc57e2-3c56-4819-bb53-bfde34aed764 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 100.1GB: initrd.img
 100.1GB: initrd.img.old
 100.0GB: vmlinuz
 100.5GB: vmlinuz.old

================================ sdb3/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
```

---

### Post by wilee-nilee on 2010-07-27
So whats going on can you boot either OS?

---

### Post by spydeyrch on 2010-07-27
> **jfl said:**
> OK, got the brand new XP CD-ROM.
Unplugged the Ubuntu HD.
Boot show an error:

```
error: no such device 56145584-a886- (more numbers)............
grub rescue>
```Rebooted, went in the BIOS, made sure the unplugged disk was "Not Installed", same error.
FWIW, both HD are IDE, not SATA.

Any advice ???          Thanks


Have you backed up all your files from W2K?

I would like you to try something:

Connect the Ubuntu drive and disconnect the Win2K drive. Try to boot from the Ubuntu drive. Are you able to get into ubuntu without the win2k drive connected?

If you have both drives connected, are you able to boot into both OSes?

-Spydey :KS

---

### Post by spydeyrch on 2010-07-27
> **jfl said:**
> ....
I was thinking of unplugging the drive with Lucid on it, upgrade the drive with Windoze.....

What is the best way of doing this ???

Thanks !


Are you really going to run the 'upgrade' path going from Win2K to XP? Or woudl you do a fresh install of XP?

-Spydey :KS

---

### Post by wilee-nilee on 2010-07-27
> **spydeyrch said:**
> Are you really going to run the 'upgrade' path going from Win2K to XP? Or woudl you do a fresh install of XP?

-Spydey :KS

sdb has XP on it.

---

### Post by jfl on 2010-07-27
> **spydeyrch said:**
> Have you backed up all your files from W2K?

I would like you to try something:

Connect the Ubuntu drive and disconnect the Win2K drive. Try to boot from the Ubuntu drive. Are you able to get into ubuntu without the win2k drive connected?

If you have both drives connected, are you able to boot into both OSes?

-Spydey :KS

Yes, I can get in Ubuntu with the w2k disconnected

Yes I can go into both OSes with both drives connected.

---

### Post by jfl on 2010-07-27
> **spydeyrch said:**
> Are you really going to run the 'upgrade' path going from Win2K to XP? Or woudl you do a fresh install of XP?

-Spydey :KS

I am burning the nlite CD right now.

I am not sure about upgrading vs fresh install; I have 4-5 apps running on w2k, I could reinstall ... another evening shot ;).
Do you think fresh install is better ?

In Ubuntu, I did net upgrade since Dapper on 3 machines and it went well except once.
No, no, no I am not comparing windoze and Linux :D

---

### Post by spydeyrch on 2010-07-27
@ wilee-nilee

I love the avatar pic. The super-man squirrel. It cracks me up!!!  :lolflag:
Sorry, off-topic comment. 

-Spydey :KS

---

### Post by spydeyrch on 2010-07-27
> **wilee-nilee said:**
> sdb has XP on it.


Yeah, so I went back and read the output of the bootscript and saw a few things that caught my attention and made me question how the HDDs are setup and why, such as:

-What happened to sdb1 & sdb2? they don't exist.
-sdb3 says that it is XP
-Then it also appears that XP is installed on an extended partition.
-Why is XP installed twice? Could it be that the bootscript sees Win2K as the XP on sdb3?
-Why is XP installed on an extended parition?
-GRUB is installed on both sda & sdb, why?

(Those are just questions that I asked myself. You don't have answer them. They were just things that stood out to me.)

So this is what I would do, and this is for an IDE setup. Also, this is doing a fresh full install of XP. Meaning you will need to re-install all of your old win2K programs, settings, etc.  Some of it may be over-kill & repetitive, but this is how I would do it. I recently did this for a friend's computer with two IDE HDD and it worked just fine. You also stated that with just your ubuntu drive connected, you could boot into your ubuntu system, that is important. :

HDD1 = ubuntu drive
HDD2 = windows drive

-Make sure all your files are backed up from Win2K, XP, & ubuntu (if you can get into XP and have anything in it) just in case this fails.
-Power off the computer
-Make sure that HDD1 (ubuntu drive) is in the master position (the last connection) on the IDE ribbon. Also make sure that the jumpers on the HDD are set to the master position.
-Make sure that HDD2 (Windows drive) is in the slave position (the middle connection) on the IDE ribbon. Also make sure that the jumpers on the HDD are set to the 'slave' or 'cable select' position.
-With both HDDs connected in the order previously described, power on the computer.
-Enter the BIOS and make sure that HDD1 (ubuntu drive) is selected as the boot drive.
-Boot into ubuntu.
-Using g-parted from within ubuntu, on HDD2 (windows drive) create one partition and reformat it to a FAT32 file system. Format the entire drive making sure that there is a single partition the size of your drive. 


!!!!****WARNING****!!!! 
If you do not select the correct drive, you could erase your ubuntu drive completely and lose your files. Hense the need to backup prior to doing any of this. Make sure that you select the correct drive.
!!!!****WARNING****!!!!


-Once finished formating and partitioning your old windows drive, power down the computer.

----------

*This next step is somewhat not needed but I like to do it just to make sure everything went ok and nothing affected my ubuntu drive*

-Disconnect your newly formatted/partitioned HDD (HDD2).
-With only your HDD1 (ubuntu drive) connected, boot it just to make sure that will still boot correctly and that all things are still where they should be.

----------

-Disconnect HDD1 (ubuntu drive).
-Change the jumper on HDD2 from 'slave or cable select' to 'master'.
-Connect HDD2 to the master connection on the IDE ribbon
-Power on the computer and via BIOS, make sure that your boot order goes something like this:

1.) CD/DVD drive
2.) .....
3.) .....
4.) HDD2

The important thing is that your CD/DVD drive is before your HDD2 in the boot sequence. 

-Reboot and insert slipstreamed XP Install CD.
-Install XP. Update, install programs, etc.
-Power off machine.
-Disconnect HDD2 (windows drive). Change jumper to 'slave' or 'cable select'.
-Connect HDD1 (ubuntu drive) to master connection on IDE ribbon.
-Connect HDD2 (windows drive) to slave connection on IDE ribbon.
-Power on machine and enter BIOS.
-Make sure that HDD1 (ubuntu drive) is the boot HDD and not HDD2.
-Reboot after saving the BIOS settings.
-Select Ubuntu.
-Once in Ubuntu, open the terminal and run:
```

sudo update-grub2

```That should update your grub menu and place WinXP in it.

-Once done, reboot the machine.
-At the grub boot menu, select Windows XP and boot into it.

-------------------

If everything has gone according to how it should, you now have your ubuntu drive still in tact and a dual boot system with XP.

This is what I would do. I never had any success with upgrades in windows. It always ran slower or never worked the right way. I always did a fresh re-install. If I had to re-install programs, I preferred that to having my whole windows system run slower and cluttered with left over files.

I don't know if that helps or not but it is what I would do.

-Spydey :KS

P.S. Hope it helps.

---

### Post by jfl on 2010-07-27
Thanks for the detailed instructions !!!
I will work on it this week-end when the office is closed.

I believe there is a problem with the bootscript.
I never had an XP cd in my life before yesterday and it never got within 10 feet of that box :D
My windoze drive is formatted:
C:  W2K
D:  Applications
E:  Data

I have no idea how grub got on that drive either.
It is an office machine, used to run Quickbooks on windoze and OO writer,  spreadsheet, Firefox and Tbird on Ubuntu. 
No tinkering, improving, whatever.

Why run these apps in Ubuntu as they would run on W2K ?
Because I hope to switch 100% to Ubuntu and doing this gets the person using that machine to Ubuntu.

Thanks again for your time, guys and I'll let you know how it goes !!!

I'll do a fresh install like you said, formatting the C: partition.

---

### Post by spydeyrch on 2010-07-28
> **jfl said:**
> I believe there is a problem with the bootscript.
I never had an XP cd in my life before yesterday and it never got within 10 feet of that box :D
My windoze drive is formatted:
C:  W2K
D:  Applications
E:  Data


Well, that would explain the multi-partition setup ...... to some degree. Still, I don't know why sdb1 & sdb2 were not listed and why there was an extended partition split into three. Interesting........

> **jfl said:**
> I have no idea how grub got on that drive either.
It is an office machine, used to run Quickbooks on windoze and OO writer,  spreadsheet, Firefox and Tbird on Ubuntu. 
No tinkering, improving, whatever.


Well, if Win2K was installed first then ubuntu but while the win2k drive was still connected, as I understand it, Grub would have changed the MBR on the Win2K drive to point correctly to the ubuntu drive in order to boot the grub menu.  But I could be wrong.

> **jfl said:**
> Why run these apps in Ubuntu as they would run on W2K ?
Because I hope to switch 100% to Ubuntu and doing this gets the person using that machine to Ubuntu.

Thanks again for your time, guys and I'll let you know how it goes !!!

I'll do a fresh install like you said, formatting the C: partition.

Well, if you can run everything that is needed but in ubuntu, then go for it!! Make the switch. :D  then you could use the extra HDD (the old windows one) as a data drive for extra storage, etc.

Let us know if there is anything else that you might need help with. Thank!!

-Spydey :KS

---

### Post by jfl on 2010-08-05
Spydey, a big thank you for the instructions !!!

I found the time to do the upgrade this after-noon; it went without a hitch.
I changed your procedure a bit: I used the XP CD to format the C: drive, left the D: E: and F: alone as it is where my data resides.
I did the format after I disconnected the Ubuntu drive ;) so there was no risk of zapping the wrong one.

I like to modify the Linux drives with Gparted and the windoze drives with Partition Magic; a few years ago, I moved a Linux partition with Partition Magic; it took me 2 days and $80 for an app to "de-scramble" the Linux drive; I must say I recovered 95% of my data.

---

