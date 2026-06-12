---
title: "Grub2 detecting wrong hard drives"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by regneva on 2010-07-25
I performed a clean install of 64 bit 10.04 overwriting my previous install of 32 bit 9.04. I find that grub configuration has wrong partition. As in if I manually edit the entry from (hd2,5) to (hd4,5), the boot works fine. Otherwise it is just stuck. I reinstalled grub-pc from synaptic to no effect! Also post re-installation grub just drops me to the grub> shell. Please help!

---

### Post by drs305 on 2010-07-25
If you are able to boot into your normal Ubuntu install (by whatever method), you can try to update things with:
```

sudo update-grub

```

If that fails, but again you are in your normal Ubuntu OS, try uninstalling and reinstalling. Make sure you have a stable power supply and Internet before running this command, as you will temporarily lose Grub2:
```
sudo apt-get purge grub-common && sudo apt-get install grub-pc
```

You say it works if you change it to (hd4,5). Do you have 5 drives on your machine? In any case, when you run the above commands, install Grub2 to the correct *drive*, not a partition. When you get to that screen, highlight the correct drive and press the Spacebar to place an asterisk next to the *drive*. Do not select any partitions. TAB to "OK" and press ENTER.

If you can't boot to the normal OS, boot the LiveCD to the desktop and install Grub2 by mounting the partition with your OS. The first command designates the *partition* to mount (your Ubuntu partition), while the second command should only designate the *drive*. **Substitute the correct partition and drive - your's will most likely NOT be sda or sda1 based on your post.**

```
sudo mount /dev/**[COLOR="DarkRed"]sda1[/COLOR]** /mnt
sudo grub-install --root-directory=/mnt **[COLOR="DarkRed"]/dev/sda[/COLOR]**
```
Reboot.

---

### Post by regneva on 2010-07-25
Thanks drs305, the purge and install worked. 

I do have the doubt still, though. These are the hard disks I have

> /dev/sdc5 on / type reiserfs (rw,notail)
/dev/sdc2 on /media/sdc2 type reiserfs (rw,notail)
/dev/sdd1 on /media/sdd1 type reiserfs (rw,notail)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/sda1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1 on /media/sde1 type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


The primary master is sda and grub is installed on the MBR of sda. Now my doubt is as follows. From the grub shell I find that (hd4,5) corresponds to the /dev/sdc5. But the grub.cfg has the following entry

> 
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}


And now it boots fine! Previously it was getting stuck. I had assumed that it was because of this (hd2,5) being incorrect. 

What am I missing?

Thanks once again!

---

### Post by drs305 on 2010-07-25
If you run the following script by user *meierfra* and post the results we can see everything that Grub2 is looking at. Copy/paste the results between [noparse]```

```[/noparse] tags, which you can generate by pressing the # icon in the post's menu.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by regneva on 2010-07-25
Here is the result:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /ntdetect.com 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 124   170,931,599   170,931,476   f W95 Ext d (LBA)
/dev/sdc5                 126   158,963,174   158,963,049  83 Linux
/dev/sdc6         158,963,238   170,931,599    11,968,362  82 Linux swap / Solaris
/dev/sdc2    *    170,931,600   488,392,064   317,460,465  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   976,768,064   976,768,002  83 Linux


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
64 heads, 32 sectors/track, 953869 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             32 1,953,521,663 1,953,521,632   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9688C60688C5E4B9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46FC-5996                              vfat                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc2        718904e7-ecfa-443b-8f15-fbe603cd666a   reiserfs                                 
/dev/sdc5        f9b989d5-5784-4eff-9d6d-4a76df85d9b4   reiserfs                                 
/dev/sdc6        25622937-2074-4bb9-8d45-b62b99bb6131   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        0ea78fcc-e8ed-440f-810c-a737127a2152   reiserfs                                 
/dev/sdd: PTTYPE="dos" 
/dev/sde1        6CFE4B18FE4AD9CA                       ntfs                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        reiserfs   (rw,notail)
/dev/sdc2        /media/sdc2              reiserfs   (rw,notail)
/dev/sdd1        /media/sdd1              reiserfs   (rw,notail)
/dev/sdb1        /media/sdb1              vfat       (rw,noexec,nosuid,nodev)
/dev/sda1        /media/sda1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sde1        /media/sde1              fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Unidentified operating system on drive C."


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
insmod reiserfs
set root='(hd2,5)'
search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
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
insmod reiserfs
set root='(hd2,5)'
search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
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
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 ro  splash  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 ro single  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod reiserfs
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set f9b989d5-5784-4eff-9d6d-4a76df85d9b4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 9688c60688c5e4b9
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod fat
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 46fc-5996
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=f9b989d5-5784-4eff-9d6d-4a76df85d9b4 /               reiserfs notail          0       1
# swap was on /dev/sdc6 during installation
UUID=25622937-2074-4bb9-8d45-b62b99bb6131 none            swap    sw              0       0
#/dev/sda1
/dev/sda1   /media/sda1            ntfs    rw,auto      0   0
#/dev/sdb1
UUID=46FC-5996   /media/sdb1            vfat    rw,auto      0   0
#/dev/sdc2
UUID=718904e7-ecfa-443b-8f15-fbe603cd666a /media/sdc2               reiserfs notail          0       1
#/dev/sdd1
UUID=0ea78fcc-e8ed-440f-810c-a737127a2152   /media/sdd1               reiserfs notail          0       1
#/dev/sde1
/dev/sde1   /media/sde1            ntfs    rw,auto      0   0

=================== sdc5: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: boot/grub/grub.cfg
    ??GB: boot/initrd.img-2.6.32-21-generic
    ??GB: boot/initrd.img-2.6.32-24-generic
    ??GB: boot/vmlinuz-2.6.32-21-generic
    ??GB: boot/vmlinuz-2.6.32-24-generic
    ??GB: initrd.img
    ??GB: initrd.img.old
    ??GB: vmlinuz
    ??GB: vmlinuz.old


```

---

### Post by oldfred on 2010-07-25
Do you have mixed SATA & PATA drives and/or removable devices?

When I installed to a Flash drive that was sdf it set the drive number & UUID correctly, but I removed the Flash drive sde that I installed from, grub would not boot until I edited the drive number. I think when it found a missing drive in the drive order search stops looking for UUIDs and the drive was above a space in drive order. Reinstalling grub then worked for me also. When I plug the flash into my portable it becomes sdb and the search works and overrides the drive number and it boots ok.

---

### Post by drs305 on 2010-07-25
The first lines of the script says G2 is installed in sda's MBR and looks at sda5, but this normally would not work as you don't have an sda5. It also says you have Grub legacy installed on sdc and it looks at sdc5, but there is no menu.lst in that location for Grub legacy to use. It may have something to do with removable drives. 'Tis very strange.

The one thing I can think of is to check your Grub device map at /boot/grub/device.map  Perhaps it is switching the drives around a bit, designating (hd0) as /dev/sdc and (hd2) as /dev/sda. That could explain things.

---

### Post by regneva on 2010-07-25
All my drives are SATA2. I did install ubuntu from a flash drive as this machine lacks a optical drive and had to change boot sequence from PM, PS, SM to USB, PM, PS to get it to boot. That explains something?

---

### Post by regneva on 2010-07-25
> **drs305 said:**
> The first lines of the script says G2 is installed in sda's MBR and looks at sda5, but this normally would not work as you don't have an sda5. It also says you have Grub legacy installed on sdc and it looks at sdc5, but there is no menu.lst in that location for Grub legacy to use. It may have something to do with removable drives. 'Tis very strange.

The one thing I can think of is to check your Grub device map at /boot/grub/device.map  Perhaps it is switching the drives around a bit, designating (hd0) as /dev/sdc and (hd2) as /dev/sda. That could explain things.

I don't think device map is the issue:

```
neo@matrix:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory
neo@matrix:~$ cd /boot/grub/
neo@matrix:/boot/grub$ find . | grep map
./lsmmap.mod
./bitmap.mod
./bitmap_scale.mod
./drivemap.mod
./partmap.lst
./mmap.mod
neo@matrix:/boot/grub$ 

```

---

### Post by oldfred on 2010-07-25
They did away with device.map as standard. It just does searches.

The boot in sda is probably correct. There is a issue with either grub2 or the script that mis-identifies the drive. On my system MBR in sda script  says I boot from same drive partition 7 for my test install but it is really sdc7 and I only have 3 partitions in sda. I think kansasnoob reported it to meierfra.

---

### Post by drs305 on 2010-07-25
It's common to not have a device.map. But it can be useful or cause problems in some cases.

Here is the Jul 2010 GNU Grub Manual on device.map:
> 
GRUB avoids this problem nowadays by using UUIDs or file system labels when generating grub.cfg, and we advise that you do the same for any custom menu entries you write. If the device map file does not exist, then the GRUB utilities will assume a temporary device map on the fly. This is often good enough, particularly in the common case of single-disk systems.

However, the device map file is not entirely obsolete yet, and there are still some situations that require it to exist. If necessary, you may edit the file if grub-mkdevicemap makes a mistake. You can put any comments in the file if needed, as the GRUB utilities assume that a line is just a comment if the first character is &#8216;#&#8217;. 


I think I've talked to meierfra about the way the script sometimes identifies things and am pretty sure he is aware of it. I've sent him a link to this post's RESULTS.txt just to be sure.

---

### Post by regneva on 2010-07-25
I've rebooted the machine about 20-30 times now and grub has randomly dropped me into grub> prompt about 5-6 times. The remainder of times it runs perfectly. This is quite inexplicable. I've been running various ubuntu since Aug 2006 and this is the first time I'm facing this kind of problem.

Any solutions comes to mind? Should I go back to legacy grub?

Thanks in advance..

---

### Post by oldfred on 2010-07-25
That sounds more like a timing issue between hardware & grub/ubuntu.

The keep speeding up the boot process and maybe all your drives are not fully up to speed so it has issues reading drive???

---

### Post by regneva on 2010-07-26
> **oldfred said:**
> That sounds more like a timing issue between hardware & grub/ubuntu.

The keep speeding up the boot process and maybe all your drives are not fully up to speed so it has issues reading drive???

How can I solve this? Is there some delay I can add BEFORE grub loads up?

---

### Post by drs305 on 2010-07-26
I agree with oldfred that it sounds like a timing/sequencing issue. 

"rootdelay" is something you can add to the linux kernel line in /etc/default/grub but I think that would be too late in the process to work.

There may be a BIOS setting that could slow things down. I'll do a bit of research later. In the meantime, one workaround might be to have a USB thumb drive inserted at boot. This might take enough time to read that everything will be ready once it gets to your SATA drives. It might confirm that all your system needs is another second or two to prepare your SATA drive for reading by GRUB.

---

### Post by regneva on 2010-07-26
Drs305, I tried having a USB, but for BIOS to check it, I need to modify the boot sequence to include USB, which messes several things up. Currently I check every time I reboot the machine. Only problem is, this machine is supposed to be used as a headless server most of the time and a script shuts it down when the UPS power is low. I can't be around all the time when it turns back on (BIOS boot-on-power)... :(

---

### Post by regneva on 2010-07-27
OK. I isolated the problem to the following. If I restart the computer, either from ubuntu or windows, there is a very high probability that grub drops me to the grub> shell. If I shut down, and start the computer again, even if I do it instantly, the problem never happens. 

I am thinking of getting rid of grub2 altogether and go back to legacy grub, which worked very well in the past for me. Any side effects from that? Will I be able to use 10.04 normally (update kernels and all) with legacy grub?

Thanks in advance..

---

