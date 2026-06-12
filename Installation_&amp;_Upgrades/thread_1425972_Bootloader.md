---
title: "Bootloader"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by clydeseal on 2010-03-09
!This may sound really confusing, but I really need help!

I have Windows Vista installed on my laptop internal hard drive (hdd1) I also have Ubuntu installed on my 500gb external hard drive (hdd2) Now I have given hdd2 three partitions 100gb for ubuntu, 300gb of general storage, and another 100gb partition.

I was going to install windows XP on to the third 100gb partition of hdd2. However, when I did this it seems that it made XP the primary bootloader. So now every time I try to boot my computer it tries to boot XP and crashes. 

I had a similar problem when I installed Ubuntu on hdd2. After installing it my computer would load GRUB when I booted even when hdd2 was not attatched and I could not boot Vista. In a different forum I was told how to move GRUB onto hdd2 so it would only boot GRUB when I told it to boot from hdd2.

Now I was wondering if there was a way that I could make GRUB my primary bootloader and let me choose which os to boot.

P.S. Don't worry about my files I do not have anything important or anything I need to keep  on that computer. It has all been moved to a different computer.

---

### Post by presence1960 on 2010-03-09
First off I am assuming you have only 2 hard disks- the internal (sda) and the external sdb. What I would do is put GRUB on MBR of the external (sdb) and make the internal (sda) MBR a windows MBR if it is not already. This is a fairly simple process but I need some info so I can give you the exact commands to run to accomplish this.

What the above will do is have it so when you boot without the external you boot right to windows. If you boot with the external plugged in GRUB takes over and you can boot ubuntu.

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

### Post by clydeseal on 2010-03-10
Okay here it is. 
```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6776bb9c

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   234,440,703   231,366,656   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e6a6c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,728,574   209,728,512  83 Linux
/dev/sdb2         964,751,445   976,768,064    12,016,620   5 Extended
/dev/sdb5         964,751,508   976,768,064    12,016,557  82 Linux swap / Solaris
/dev/sdb3         419,465,980   943,770,554   524,304,575   7 HPFS/NTFS
/dev/sdb4         209,728,575   419,457,149   209,728,575   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C88691528691423C                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        022295AD2295A5E7                       ntfs       SQ004286V02                   
/dev/sdb1        55e8f7cb-7ba0-45ea-a9e2-9385183b6dba   ext4       Ub                            
/dev/sdb3        2E980367421E9A7F                       ntfs       TOM                           
/dev/sdb4        3E5CD5955CD547F3                       ntfs                                     
/dev/sdb5        749e3483-17cf-404f-a18a-f3825fe90eaa   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb4        /media/3E5CD5955CD547F3  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb3        /media/TOM               fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


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
search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
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
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 55e8f7cb-7ba0-45ea-a9e2-9385183b6dba
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set d2300e71300e5cbb
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
UUID=55e8f7cb-7ba0-45ea-a9e2-9385183b6dba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=749e3483-17cf-404f-a18a-f3825fe90eaa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.0GB: boot/grub/core.img
  13.0GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   2.8GB: boot/initrd.img-2.6.31-19-generic
   3.7GB: boot/initrd.img-2.6.31-20-generic
    .6GB: boot/vmlinuz-2.6.31-14-generic
   1.1GB: boot/vmlinuz-2.6.31-19-generic
   3.5GB: boot/vmlinuz-2.6.31-20-generic
   3.7GB: initrd.img
   2.8GB: initrd.img.old
   3.5GB: vmlinuz
   1.1GB: vmlinuz.old
```
I did want to give you an update, I have reinstalled vista on the internal drive so I can boot my laptop. I can also still boot Ubuntu from the external drive. So at the moment Xp is just a bunch of files taking up space. Also I noticed TOM in the Boot Info Script. That is the name I gave to the external drive stands for Toshiba Optional Memory. Just in case you were wondering.

---

### Post by presence1960 on 2010-03-10
It is a shame that you reinstalled Vista. You could have fixed the MBR of the internal drive by booting Ubuntu or the the ubuntu Live Cd and running in terminal ```
sudo apt-get install lilo
```which will install lilo. Ignore the warning and run in terminal ```
sudo lilo -M /dev/sda mbr
```which would have fixed the internal (sda) MBR so you can boot Vista. Alternatively you could have done [this]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to the section for Vista/7.

As far as XP- I may be incorrect but I believe you can't put windows on an external disk.

You should be good to go now as GRUB 2 is on MBR of the external and windows is  on MBR of the internal disk.

---

### Post by clydeseal on 2010-03-10
Um... that didn't seem to do anything. Vista still boots from the internal drive and Ubuntu still boots from the external drive. And XP is still just a bunch of useless files.

Is there some way I can add XP to GRUB and then be able to boot it?

---

### Post by presence1960 on 2010-03-10
I don't think you are going to get windows to boot from an external disk. Vista is supposed to boot from the internal and Ubuntu is supposed to boot from the external. This way you can boot vista without the external plugged in. 

See your quote from the original post:

> I had a similar problem when I installed Ubuntu on hdd2. After installing it my computer would load GRUB when I booted even when hdd2 was not attatched and I could not boot Vista. In a different forum I was told how to move GRUB onto hdd2 so it would only boot GRUB when I told it to boot from hdd2.

So just exactly what is it you want to do. You have accomplished to fix the above situation. I really do not understand what you are trying to do now.

Besides the fact that I am uncertain that you can install windows to an external disk, even if that is possible your XP will never boot because it is missing the boot files necessary to boot XP - namely boot.ini, NTdetect and NTLDR. See below from your script output you are missing XP boot files:
```

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
   [COLOR="Red"] Boot files/dirs:[/COLOR]   

sdb4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    [COLOR="Red"]Boot files/dirs:[/COLOR]  
```

**P.S. I did some googling and to get any windows to install and boot from an USB/external disk you have to jump through many hoops. I have read some of the how-to's from my google search and from the reports of people who have tried it it seems to be a mixed bag- some claim success and others say it never worked for them. Microsoft steadfastly claims that windows can not be on a USB/external as the main storage for the installed Operating System. As far as I am concerned your problem is solved because you have Vista on the internal and Ubuntu on the external booting properly. If you want to pursue booting XP from the external this is not the forum to do so.**

---

### Post by presence1960 on 2010-03-10
Clydeseal,

Please do not start duplicate threads on the same topic. You have one here also: [http://ubuntuforums.org/showthread.php?t=1418411&page=2](http://ubuntuforums.org/showthread.php?t=1418411&page=2)

And if you read the thread I just linked (as I just did) you were told basically the same thing on that thread too.

---

### Post by clydeseal on 2010-03-10
What I wanted originally was to install an operating system on my external drive and then be able to install programs on it and take the external drive with me and be able to boot it from any computer. However some of the programs I wanted to install were not compatible with linux so I was going to try installing XP on the external drive also, but then I got into this mess.

So what you are saying is that it is not really feasible to install XP on an external drive.

Also about the other thread. I had posted that shortly after I installed Ubuntu on the external drive because I was having trouble booting. When I got into this mess I put a post there, but nobody responded to it for a while so I made this thread. That response that you pointed out was posted like 45 minutes ago. My apologies, it was not my intention to duplicate threads.

Lastly I would like to thank you for helping me. :D

---

### Post by presence1960 on 2010-03-10
> **clydeseal said:**
> What I wanted originally was to install an operating system on my external drive and then be able to install programs on it and take the external drive with me and be able to boot it from any computer. However some of the programs I wanted to install were not compatible with linux so I was going to try installing XP on the external drive also, but then I got into this mess.

So what you are saying is that it is not really feasible to install XP on an external drive.

Also about the other thread. I had posted that shortly after I installed Ubuntu on the external drive because I was having trouble booting. When I got into this mess I put a post there, but nobody responded to it for a while so I made this thread. That response that you pointed out was posted like 45 minutes ago. My apologies, it was not my intention to duplicate threads.

Lastly I would like to thank you for helping me. :D

I hope you don't think I was chastising you for the duplicate post. I see you are a newer member of the community and I assumed that you probably didn't know.

I have been reading through those google results and I wouldn't try putting windows on a USB/external. The hoops you have to jump through just are not worth the time & effort to get it work- if that is possible anyway. You have a windows install on the internal so at least you can run windows.

---

### Post by clydeseal on 2010-03-11
:( Well that is unfortunate. Stupid Windows has to go off and make things difficult...

And yes I did think that you were mad at me.

Well thanks for you help anyway :D

---

