---
title: "Boot problem (Error 15) after reinstall from CD"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2011-05-01
Hi,

I had a version conflict in packages I used a lot. I thought to solve this by installing Ubuntu fresh over my old installation. So I downloaded the software (Ubuntu 11.04 amd64), burned a CD, and rebooted. After installation I rebooted again, and ran into troubles. I got a "GRUB error 15". I now learned this means that ["the file grub wants is not there"]("http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/"). After some reading I got stuck on what to do. So, if you could help me...

I ran a dual boot (XP/Ubuntu) dual disk system. This is my configuration:
```

> sudo fdisk -l | grep -i linux
/dev/sda8           46187       57080    87506023+  83  Linux
/dev/sda9           57081       57367     2305296   82  Linux swap / Solaris
/dev/sda13          44620       45681     8523776   83  Linux
/dev/sda14          45681       46187     4061184   82  Linux swap / Solaris
/dev/sdb1   *           1        9964    80035798+  83  Linux

> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

My startupmanager does not want to come to play:
```

> startupmanager
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying
GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

```

I also have not so much information in my grub directory:
```

> more /boot/grub/grub.cfg
/boot/grub/grub.cfg: No such file or directory
> ls /boot/grub
gfxblacklist.txt  grubenv

```

Lastly, a update-grub does not make me happy too.
```

sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

Anyone know what my options are?

TIA,
Macamba

---

### Post by Macamba on 2011-05-01
After executing boot_info_script055.sh I got the following RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #13 for cadc4.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda12 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   102,414,374   102,414,312   7 HPFS/NTFS
/dev/sda2         102,414,375   409,609,304   307,194,930   7 HPFS/NTFS
/dev/sda3         409,609,366 1,465,144,064 1,055,534,699   5 Extended
/dev/sda5         409,609,368   512,007,614   102,398,247   7 HPFS/NTFS
/dev/sda6         512,007,678   614,405,924   102,398,247   7 HPFS/NTFS
/dev/sda7         614,405,988   716,804,234   102,398,247   7 HPFS/NTFS
/dev/sda8         741,978,153   916,990,199   175,012,047  83 Linux
/dev/sda9         916,990,263   921,600,854     4,610,592  82 Linux swap / Solaris
/dev/sda10        921,600,918 1,126,397,474   204,796,557   7 HPFS/NTFS
/dev/sda11      1,126,397,538 1,331,194,094   204,796,557   7 HPFS/NTFS
/dev/sda12      1,331,194,158 1,465,144,064   133,949,907   7 HPFS/NTFS
/dev/sda13        716,806,144   733,853,695    17,047,552  83 Linux
/dev/sda14        733,855,744   741,978,111     8,122,368  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   160,071,659   160,071,597  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       3600BCB400BC7D05                       ntfs       Films                         
/dev/sda11       6ACCCC47CCCC0F6F                       ntfs       NZB                           
/dev/sda12       845CE6995CE684F0                       ntfs       Comics                        
/dev/sda13       92ab9d4b-d543-4c0f-80e0-0f4a249d93e8   ext4                                     
/dev/sda1        3A58E18258E13CEF                       ntfs       Harde schijf                  
/dev/sda2        2E203B76203B43DD                       ntfs       Verloren zoon                 
/dev/sda3: PTTYPE="dos" 
/dev/sda5        CCA00FA4A00F945C                       ntfs       Development                   
/dev/sda6        B00C31B10C317386                       ntfs       Muziek                        
/dev/sda7        DE4817804817571D                       ntfs       Niet meer vrij                
/dev/sda8        e6813a59-b8ec-4f6f-9b61-7651d77f459f   ext3                                     
/dev/sda9        38232412-528d-41a4-82c8-8e6d65e7e46f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        56e96ed1-4787-4081-afbc-3f4e77f6b2d2   ext3                                     
/dev/sdb: PTTYPE="dos" 

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

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


========================== sda13/boot/grub/grub.cfg: ==========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos13)'
search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos13)'
search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos13)'
	search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=92ab9d4b-d543-4c0f-80e0-0f4a249d93e8 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos13)'
	search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=92ab9d4b-d543-4c0f-80e0-0f4a249d93e8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos13)'
	search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos13)'
	search --no-floppy --fs-uuid --set=root 92ab9d4b-d543-4c0f-80e0-0f4a249d93e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 3A58E18258E13CEF
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

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb13      /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb14 during installation
#UUID=8592d279-d03d-456d-bf34-864a759ea281 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda13: Location of files loaded by Grub: ===================


 374.5GB: boot/grub/core.img
 374.5GB: boot/grub/grub.cfg
 368.6GB: boot/initrd.img-2.6.38-8-generic
 374.5GB: boot/vmlinuz-2.6.38-8-generic
 368.6GB: initrd.img
 374.5GB: vmlinuz
```

---

### Post by Macamba on 2011-05-01
Furthermore, I mounted the partition I installed the new version of Unbuntu on, and performed a grub-install:
```

ubuntu@ubuntu:/media/sda13/etc/default$ sudo grub-install --root-
directory=/mnt /dev/sda/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

So there might be a bit more happening then I bargained for.

---

### Post by apollothethird on 2011-05-01
> **Macamba said:**
> Hi,

I had a version conflict in packages I used a lot. I thought to solve this by installing Ubuntu fresh over my old installation. So I downloaded the software (Ubuntu 11.04 amd64), burned a CD, and rebooted. After installation I rebooted again, and ran into troubles. I got a "GRUB error 15". I now learned this means that ["the file grub wants is not there"]("http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/"). After some reading I got stuck on what to do. So, if you could help me...

I ran a dual boot (XP/Ubuntu) dual disk system. This is my configuration:
```

> sudo fdisk -l | grep -i linux
/dev/sda8           46187       57080    87506023+  83  Linux
/dev/sda9           57081       57367     2305296   82  Linux swap / Solaris
/dev/sda13          44620       45681     8523776   83  Linux
/dev/sda14          45681       46187     4061184   82  Linux swap / Solaris
/dev/sdb1   *           1        9964    80035798+  83  Linux

> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

```

My startupmanager does not want to come to play:
```

> startupmanager
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying
GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

```

I also have not so much information in my grub directory:
```

> more /boot/grub/grub.cfg
/boot/grub/grub.cfg: No such file or directory
> ls /boot/grub
gfxblacklist.txt  grubenv

```

Lastly, a update-grub does not make me happy too.
```

sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.

```

Anyone know what my options are?

TIA,
Macamba

Your install method would probably never be the best way.  Many of the user configuration files might be incompatible with a new version and not be touched.  If you use the distribution upgrade, option the developers and testers knows about the personalized configuration files and will patch them to be compatible with the new version.

I believe with a lot of this in mind, your best bet would be to backup your important data and perform a truly fresh install then bring your data over to the new environment.  I'm sure it's too late to perform a distribution upgrade.

Your short cut is turning out to be a very long process.  While it's too late to save you from a lot of work ahead, knowing this might spare you or others who hasn't made this mistake yet of the problems you're in for.

You might be lucky and someone else might have a more standard method of fixing your mistake.

But again, I feel that once you get past the boot problem (the boot program) you may experience something similar with many other programs such as X, gnome, init, and countless others.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Macamba on 2011-05-01
Hi Apollo (L. James),

When starting the live CD and going into the install menu I had four options. The first (relevant) being a complete new install, and the other an upgrade. I take it you think I did the second? I opted for the first. But I will wipe the partition clean, and start a new. Now I only have to figure out how I can format the partition (luckily my data resides on a separate partition, and even on the separate disk).

Thanks for the help.

Macamba

---

### Post by apollothethird on 2011-05-01
> **Macamba said:**
> Hi Apollo (L. James),

When starting the live CD and going into the install menu I had four options. The first (relevant) being a complete new install, and the other an upgrade. I take it you think I did the second? I opted for the first. But I will wipe the partition clean, and start a new. Now I only have to figure out how I can format the partition (luckily my data resides on a separate partition, and even on the separate disk).

Thanks for the help.

Macamba

Actually it's the first option that I thought you did, which it appears that you explained.  It's the upgrade that I was explaining would have been better.  The upgrade would have taken in consideration that you were installing over a current installation and I would expect for it to perform all the needed updates would would include overwriting or removing old binaries and patching your configurations for the updates, and notifying you if it couldn't.

Keep in mind that the presence of configuration files overrides the default settings.  If you install applications in an area that has configuration files, the application might not destroy your configuration files.  So when you try to run the application, the obsolete configuration controls might can cause problems.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Dutch70 on 2011-05-01
From your boot script...
> Grub 2 is installed in the MBR of /dev/sdb and **looks on the same drive** in partition #13 for cadc4.

I'm not sure what cadc4 is, but there is no partition #13 on sdb. Which is what Grub2 appears to be looking for.

I'm thinking you need Grub2 installed in sda.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Macamba on 2011-05-02
I fixed my MBR using the XP CD. To be on the safe side I also performed a
```
sudo rm -rf *
```
in the root of the previously installed system. During installation I saw the option to assign on what partition I wanted the root, home directories.  I also performed an format of the root partition. However when I rebooted the system (keeping my fingers crossed) I did not get into a grub menu, but booted XP directly.

Might I have issues with the second HD, which according to my BIOS setup is seen as my secondary master (Primary being the CDROM, and primary slave being the second build in HD containing data)? What do I need to do to let the HD containing Ubuntu (and XP) be the secondary master? Should I flip some switches on the back of the new (old) HD containing data?

Macamba

---

### Post by Macamba on 2011-05-02
FWIW, my system can get a bit confused on what hard disk is sda and what harddisk is sdb. I noticed that the mount points I defined using /dev/sda8 where screwed up because the drive that should be mounted was suddenly situated on /dev/sdb8. I solved that by using the UUID. But I'm a bit mystified how this should be done in the boot menu. And in the forest of the grub2 documentation I can't find the tree I need to cut down. Hence probably that I do not see a boot menu at all and XP auto boots.

---

### Post by Dutch70 on 2011-05-02
Ok, at this point another boot info script would be useful. 0.55 doesn't really work well with Natty though, use the following command to get this one. 

From the live cd/usb of course.
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh; hb=HEAD'
```

That should put it in your downlaods folder, cut & paste it to your desktop then run this command. 
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Macamba on 2011-05-02
Hi Dutch,

I think I have my problem whipped. I removed the new (old) harddisk and changed the jumper to slave/second hd. This did not solve my problem. However, I opened the computer case, removed the current from the new (old) hd, reinstalled, and now it works. My next big trick will be connecting the new (old) hd again. But me thinks this would not be such a problem. When my problem returns, I will look what running the script you suggest might bring us.

Macamba

---

### Post by Dutch70 on 2011-05-02
Well good, sounds like you're on the right track.

Just so you know, the command I gave you just downloads the newest version of Boot Info Script. Same as you did before with Boot_Info_Script 0.55, Except that command will put it in your downloads folder.

---

