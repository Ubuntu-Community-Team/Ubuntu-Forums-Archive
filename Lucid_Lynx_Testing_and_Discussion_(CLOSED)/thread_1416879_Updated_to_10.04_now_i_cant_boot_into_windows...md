---
title: "Updated to 10.04 now i cant boot into windows.."
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by WatTwo on 2010-02-26
Well I upgraded from 9.10 to 10.04 and now when i choose my windows 7 in grub

All that comes up is "GRUB _"

And i have to restart...

---

### Post by utnubuuser on 2010-02-26
check for threads with "fix MBR+Windows7".  Lots of them out there.

---

### Post by wilee-nilee on 2010-02-26
> **WatTwo said:**
> Well I upgraded from 9.10 to 10.04 and now when i choose my windows 7 in grub

All that comes up is "GRUB _"

And i have to restart...

Does Lucid boot normally? you may need to reinstall the W7 bootloader then grub but before that try sudo update-grub and see if it reads the W7 partition.

---

### Post by WatTwo on 2010-02-26
I can boot into ubuntu, but it says something, no point point or something, then it boots.

It shows windows fine but wont boot into it.

Also tried sudo update-grub already

---

### Post by wilee-nilee on 2010-02-26
Here is a older MBR W7 link I have never had to do this, but I have reloaded grub2 from a live CD which would be your next step after the W7 MBR.
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Here is a Grub2 wiki step 11 is what you need there are three methods. Just mounting the Ubuntu partition has worked every-time for me, then running the update grub command in the OS on the HD.

---

### Post by WatTwo on 2010-02-26
okay i will try that next.

Here is what comes up when i "sudo update-grub"

> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-14-generic
Found initrd image: /boot/initrd.img-2.6.32-14-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1


---

### Post by VMC on 2010-02-26
> **WatTwo said:**
> okay i will try that next.

Here is what comes up when i "sudo update-grub"

Now dump "/boot/grub/grub/cfg" back here so we can have a look see.

Also fdisk -l & blkid. so, do this:

```
cat /boot/grub/grub.cfg
sudo fdisk -l
sudo blkid
```

Then we can look it over.

---

### Post by WatTwo on 2010-02-26
umm...

```
[1] 14495
/dev/sda1: UUID="3498250E9824D062" TYPE="ntfs" 
/dev/sdb1: LABEL="New Volume" UUID="1E48BFA548BF79DB" TYPE="ntfs" 
/dev/sdb5: UUID="36e95b92-00fb-497f-a2f5-a7119155ee4b" TYPE="swap" 
/dev/sdc1: LABEL="Files" UUID="A4781FFF781FCF44" TYPE="ntfs" 
```

and....

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xf063f063

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9730    78148320+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0xc63be949

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5878    47210496    7  HPFS/NTFS
/dev/sdb2            5878        9720    30859375   83  Linux
/dev/sdb3            9721        9729       72292+   5  Extended
/dev/sdb5            9721        9729       72261   82  Linux swap / Solaris

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes
Disk identifier: 0x8d9f8d9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4866    39079936    7  HPFS/NTFS

```



..i don't get it, there's no way to just uninstall grub, reinstall it, then have it automatically detect the OS's like a clean install does?

---

### Post by VMC on 2010-02-27
> **WatTwo said:**
> 
..i don't get it, there's no way to just uninstall grub, reinstall it, then have it automatically detect the OS's like a clean install does?Yes, 'sudo update-grub'.

But I see you have several hard drives. Raid perhaps?

I need a more complete list. Download and run boot_info_script.
the location is under my signature. then output the RESULTS.txt file back here.

---

### Post by kansasnoob on 2010-02-27
Instructions for running the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'm sure this can be straightened out.

---

### Post by WatTwo on 2010-02-27
Okay, this is alot of text.  Hopefully you meant paste it in and not upload the file somewhere lol

(I'm fairly new to linux so bear with me XD)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 101751104 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #2 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 101715832 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdb and 
                       looks on partition #2 for /boot/grub. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,703   156,296,641   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048    94,423,039    94,420,992   7 HPFS/NTFS
/dev/sdb2          94,423,040   156,141,789    61,718,750  83 Linux
/dev/sdb3         156,151,800   156,296,384       144,585   5 Extended
/dev/sdb5         156,151,863   156,296,384       144,522  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048    78,161,919    78,159,872   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3498250E9824D062                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1E48BFA548BF79DB                       ntfs       New Volume                    
/dev/sdb2        d968fc0e-289b-48b3-9383-238acbac57d1   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        36e95b92-00fb-497f-a2f5-a7119155ee4b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        A4781FFF781FCF44                       ntfs       Files                         
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set default="2"
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
set root=(hd1,2)
search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
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
set root=(hd1,2)
search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-14-generic" {
        recordfail
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=d968fc0e-289b-48b3-9383-238acbac57d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.32-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    echo    Loading Linux 2.6.32-14-generic ...
    linux    /boot/vmlinuz-2.6.32-14-generic root=UUID=d968fc0e-289b-48b3-9383-238acbac57d1 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.32-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" {
        recordfail
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d968fc0e-289b-48b3-9383-238acbac57d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d968fc0e-289b-48b3-9383-238acbac57d1 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set d968fc0e-289b-48b3-9383-238acbac57d1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3498250e9824d062
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=d968fc0e-289b-48b3-9383-238acbac57d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=36e95b92-00fb-497f-a2f5-a7119155ee4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  52.0GB: boot/grub/core.img
  53.1GB: boot/grub/grub.cfg
  51.8GB: boot/initrd.img-2.6.31-14-generic
  49.1GB: boot/initrd.img-2.6.32-14-generic
  48.9GB: boot/vmlinuz-2.6.31-14-generic
  49.8GB: boot/vmlinuz-2.6.32-14-generic
  49.1GB: initrd.img
  49.8GB: vmlinuz
```

---

### Post by kansasnoob on 2010-02-27
I'm trying to parse that now. The first "oddity" I see is this:

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #2 for /boot/grub.

Errrm, the only thing installed on sda is Windows so how can it **look on the same drive in partition #2 for /boot/grub**?

It may not help but can't do any harm to reinstall grub2 to the mbr of both sda and sdb. While booted into Ubuntu run:

```
sudo grub-install /dev/sda
```

```
sudo grub-install --recheck /dev/sda
```

```
sudo grub-install /dev/sdb
```

```
sudo grub-install --recheck /dev/sdb
```

```
sudo update-grub
```

I included the "--recheck" commands because it invokes additional "checks" and you can expect each of those "--recheck" commands to take several minutes to complete. That terminal output may even provide some useful info.

It might also help to see the output of;

```
aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```

---

### Post by kansasnoob on 2010-02-27
This may also apply:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by VMC on 2010-02-27
WatTwo, Do you know how you have your BIOS set to boot your have drives? Is it set for sda1 or sda2.

---

### Post by WatTwo on 2010-02-27
> **kansasnoob said:**
> 

```
aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4 && aptitude show os-prober|head -4
```


```
Package: grub
State: not installed
Version: 0.97-29ubuntu60
Priority: optional
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.98~20100128-1ubuntu3
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.98~20100128-1ubuntu3
Package: os-prober
State: installed
Automatically installed: yes
Version: 1.35

```Also, I'm pretty sure my boot order is, 

Removable
disk
USB
Windows hdd
Ubuntu hdd

But the last 2 dont matter i dont think... since it loads grub anyway

I think I'm just going to do a fresh install, i need to make my partition bigger anyway

---

### Post by VMC on 2010-02-27
WatTwo, Windows7 uses two partitions when you install it. One has a 100mb recovery partition and the boot files are in there, the other has the OS of Windows7. It looks like the Windows7 recovery partition got wipe out somehow.

---

### Post by WatTwo on 2010-02-27
According to my windows disk it's all good.

So I'm going to do "bootrec.exe /fixmbr"

Should overwrite grub, then im going to use "easybcd" and add a ubuntu selection to it,

Hopefully that will work out.

If not, ill just reinstall ubuntu again :/

---

### Post by kansasnoob on 2010-02-28
> **VMC said:**
> WatTwo, Windows7 uses two partitions when you install it. One has a 100mb recovery partition and the boot files are in there, the other has the OS of Windows7. It looks like the Windows7 recovery partition got wipe out somehow.

I believe that's only true with a fresh install of Win 7. I just did an install of Win 7 (OEM) for my daughter-in-law without removing her XP and it installed to the one existing XP partition.

After restoring grub2 to the mbr all was well.

---

### Post by kansasnoob on 2010-02-28
> **WatTwo said:**
> According to my windows disk it's all good.

So I'm going to do "bootrec.exe /fixmbr"

Should overwrite grub, then im going to use "easybcd" and add a ubuntu selection to it,

Hopefully that will work out.

If not, ill just reinstall ubuntu again :/

Good. I'm also curious.

Just BTW if you ever want to restore a Windows "readable" mbr with just an Ubuntu Live CD you can use Lilo:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr
```

Of course the X must be replaced with the proper drive designation. That's a nice "tool" to be able to use while sorting out boot problems.

---

### Post by kansasnoob on 2010-02-28
Oops posted in the wrong thread so I deleted it.

---

### Post by WatTwo on 2010-02-28
Well after trying for awhile, i had to disconnect my ubuntu hdd to even get windows to boot up.

So now im just using windows today.  Tomorrow ill mess with it some more

---

### Post by kansasnoob on 2010-02-28
Well at least you know that Windows will boot so that rules out a problem with the Windows boot sector.

I'm going to look this over a little bit more.

---

