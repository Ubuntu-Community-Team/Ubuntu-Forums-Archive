---
title: "No GRUB after fresh install"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Ardghal on 2010-06-08
Hello, I've seen many threads with GRUB related problems, but I couldn't find the one I have, so here it goes:

I have a new 500GB disk, with a partition with Windows XP, one with Windows 7, one for Ubuntu 10.04, one for /Home and one for swap. The systems were installed in that order.

But after finishing with the Ubuntu installation, removing the CD from the drive and restarting, GRUB never showed up, and the system went straight to the Windows OS selector; the one prompting to start Windows 7 or an "Earlier version of Windows". So I can't get to Ubuntu, even though it seems it installed just fine.

As a note: just after the installation process ends and it shows the "remove CD" message, it spilled out a list of I/O errors in some sr0 device or something. But I just installed the same Ubuntu on a friend's computer and it showed a similar error list, yet his system works just fine... However, he doesn't have Windows 7, thus no OS selection screen other than GRUB.

Any idea how to solve this? :confused: I didn't want to rush into editing the MBR or re-installing GRUB before I knew I had to do that. I had problems before for trying solutions to problems I wasn't having. :|

---

### Post by darkod on 2010-06-08
Run the boot info script so we can see what is where:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

You can run it in live mode. You did right with not rushing to reinstall or do anything else until you have an idea what is happening.

---

### Post by ronparent on 2010-06-08
I'll venture a guess that you've got more than 4 primary partitions (especially if you prior partitioned with win7). I so, you will probably need to delete all the Ubuntu partitions and recreate them so that you end up with no more than 4 primary partitions including the extended one. Ubuntu will install fine to an extended partition and you will be able to use as many as you please.

---

### Post by Ardghal on 2010-06-09
I just ran the script. Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 65. But according to the info from fdisk, 
                       sda9 starts at sector 428389355.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃ*sico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   142,512,614   142,512,552   7 HPFS/NTFS
/dev/sda2         142,512,676   976,751,999   834,239,324   5 Extended
/dev/sda5         142,512,678   284,334,434   141,821,757   7 HPFS/NTFS
/dev/sda6         284,334,498   347,244,974    62,910,477  83 Linux
/dev/sda7         347,245,039   411,344,324    64,099,286  83 Linux
/dev/sda8         411,344,388   428,389,289    17,044,902  82 Linux swap / Solaris
/dev/sda9         428,389,355   976,751,999   548,362,645   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 61.5 GB, 61492838400 bytes
255 cabezas, 63 sectores/pista, 7476 cilindros, 120103200 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
TamaÃ±o de sector (lÃ³gico / fÃ*sico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *             66   120,101,939   120,101,874   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D08438C68438B0B8                       ntfs       Windows XP                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9CA9EA45FB4B1D82                       ntfs       Windows 7                     
/dev/sda6        62a62c0a-a7fb-4795-b5f9-e4cca65d617d   ext4                                     
/dev/sda7        77c63b16-4613-4c77-b263-ea4cc102882f   ext4                                     
/dev/sda8                                               swap                                     
/dev/sda9        6321E01BEE2A5CB0                       ntfs       Vault  15                   
/dev/sda: PTTYPE="dos" 
/dev/sdb2        45E53E7955BA96BB                       ntfs       IDE                           
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
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
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=62a62c0a-a7fb-4795-b5f9-e4cca65d617d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-21-generic (modo recuperaciÃ³n)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
	echo	'Cargando Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=62a62c0a-a7fb-4795-b5f9-e4cca65d617d ro single 
	echo	'Cargando el disco RAM inicial...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,6)'
	search --no-floppy --fs-uuid --set 62a62c0a-a7fb-4795-b5f9-e4cca65d617d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set d08438c68438b0b8
	chainloader +1
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb6       /               ext4    errors=remount-ro 0       1
/dev/sdb7       /home           ext4    defaults        0       2
/dev/sdb8       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 169.4GB: boot/grub/core.img
 169.4GB: boot/grub/grub.cfg
 169.4GB: boot/initrd.img-2.6.32-21-generic
 169.3GB: boot/vmlinuz-2.6.32-21-generic
 169.4GB: initrd.img
 169.3GB: vmlinuz
```

sdb is my old 60GB IDE disk. It had Mandriva at one point, but its partition was turned into an NTFS. Though there are references to another GRUB in the results file, it was the Mandriva GRUB. sda is the 500GB SATA drive. Just to avoid confusion. :D

[QUOTE=ronparent]I'll venture a guess that you've got more than 4 primary partitions (especially if you prior partitioned with win7). I so, you will probably need to delete all the Ubuntu partitions and recreate them so that you end up with no more than 4 primary partitions including the extended one. Ubuntu will install fine to an extended partition and you will be able to use as many as you please. [/QUOTE]

I don't understand what you say about the primary partitions. A partitioning software I have makes reference to two NTFS partitions as "Primary" (I believe one on each physical drive. Can't check now, I'm in Win7, the software is in XP), but I don't know if that's what you mean. If you mean number of partitions, then yes, there are 5 partitions, plus the swap.

---

### Post by ronparent on 2010-06-09
Your script results invalidates my comments. Apparently the mbr of sda boots windows (as you have discovered). Grub2 was written to the mbr of sdb. That would have to be 1st in bios boot for you to boot to the grub menu.

The easiest thing for you to try is to set what is currently sdb as 1st in bios boot order. If that works you are home free! Incidently that should work even though 10.04 is installed to what is now sda. Good luck.

---

### Post by darkod on 2010-06-09
Grub2 (or the script) seems very confused in this case. It reports:

=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

But it is /dev/sda which has all those partitions. /dev/sdb has only got one. How can grub2 be looking for partition #6 on /dev/sdb???

Anyway, from live mode do:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It should be fine after that.

---

### Post by kansasnoob on 2010-06-09
> **darkod said:**
> Grub2 (or the script) seems very confused in this case. It reports:

=> Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

But it is /dev/sda which has all those partitions. /dev/sdb has only got one. How can grub2 be looking for partition #6 on /dev/sdb???

Anyway, from live mode do:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It should be fine after that.

Darko,

That's a known bug in the Boot Info Script. It doesn't always happen but I pointed that out to Meierfra once.

You can depend on the script telling you what the MBR is, but sometimes it says it's "looking on the same drive" when it's actually not.

---

### Post by darkod on 2010-06-09
> **kansasnoob said:**
> Darko,

That's a known bug in the Boot Info Script. It doesn't always happen but I pointed that out to Meierfra once.

You can depend on the script telling you what the MBR is, but sometimes it says it's "looking on the same drive" when it's actually not.

Thanks. So, the first half of the sentence is correct and you can depend on it, the second might be wrong?

---

### Post by ronparent on 2010-06-09
In my limited experience I have found that I can depend on the grub2 mbr to point to the install from which it was created. Your comments would be consistent with that!

---

### Post by kansasnoob on 2010-06-09
> **darkod said:**
> Thanks. So, the first half of the sentence is correct and you can depend on it, the second might be wrong?

I think this is the same example I showed Meierfra:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 [B][COLOR="Red"]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #3 for /boot/grub.[/COLOR][/B]

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 7 Gloria - Main 
                       Edition
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda14: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda15: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda16: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda17: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda18: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux squeeze/sid
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda19: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

[B][COLOR="Red"]sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)[/COLOR][/B]
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 34102329 on boot drive #2 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #2 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 12 (Constantine) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

[B][COLOR="Red"]sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
[/COLOR][/B]
sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,648,049    31,647,987   7 HPFS/NTFS
/dev/sda2          46,620,630   312,576,704   265,956,075   5 Extended
/dev/sda5          46,620,693    58,990,679    12,369,987  83 Linux
/dev/sda6          58,990,743    67,280,219     8,289,477  83 Linux
/dev/sda7          67,280,283    79,650,269    12,369,987  83 Linux
/dev/sda8          79,650,333    88,052,264     8,401,932  83 Linux
/dev/sda9          88,052,328   100,518,704    12,466,377  83 Linux
/dev/sda10        100,518,768   108,840,374     8,321,607  83 Linux
/dev/sda11        108,840,438   117,145,979     8,305,542  83 Linux
/dev/sda12        117,146,043   129,564,224    12,418,182  83 Linux
/dev/sda13        129,564,288   137,869,829     8,305,542  83 Linux
/dev/sda14        310,118,823   312,576,704     2,457,882  82 Linux swap / Solaris
/dev/sda15        305,524,233   310,118,759     4,594,527  83 Linux
/dev/sda16        262,630,683   305,524,169    42,893,487  83 Linux
/dev/sda17        240,525,243   262,630,619    22,105,377  83 Linux
/dev/sda18        137,869,893   150,400,529    12,530,637  83 Linux
/dev/sda19        150,400,593   158,690,069     8,289,477  83 Linux
/dev/sda3          31,648,050    46,620,629    14,972,580  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical / optimal IO): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    30,732,344    30,732,282   7 HPFS/NTFS
/dev/sdb2          30,732,345    43,022,069    12,289,725  83 Linux
/dev/sdb3          43,022,070   156,296,384   113,274,315   5 Extended
/dev/sdb5          43,022,133    51,391,934     8,369,802  83 Linux
/dev/sdb6         153,806,373   156,296,384     2,490,012  82 Linux swap / Solaris
/dev/sdb7         149,468,823   153,806,309     4,337,487  83 Linux
/dev/sdb8         117,772,578   149,468,759    31,696,182  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       bc1516d1-981b-4797-a1ad-7379b2e5fa67   ext3       Hardy Home                    
/dev/sda11       3128dea7-b986-4b45-8004-0b48bf97f9dd   ext3       Lucid Home                    
/dev/sda12       33b90c3d-da7e-4671-b78a-5adafb0a927d   ext3       Karmic Root                   
/dev/sda13       4f260672-aff0-4912-9bb3-5e8c2b6158d2   ext3       Karmic Home                   
/dev/sda14       bc99fdc7-0dd8-40e7-8567-f0882352d256   swap                                     
/dev/sda15       16ebe9de-80aa-42c0-804f-ccdd81e43e95   ext3                                     
/dev/sda16       5ebdcaaf-da9e-4695-847e-200054e7559e   ext3                                     
/dev/sda17       115e96dd-3ef5-4cee-8e2b-7ef6a5e1a9ef   ext3       Pictures                      
/dev/sda18       84f9bd6c-4042-495a-99c5-2136f706bfc3   ext3       Debian Root                   
/dev/sda19       c67d9b53-8226-4c67-ab44-2f189e058b47   ext3       Debian Home                   
/dev/sda1        C02402022401FC62                       ntfs       Windows XP                    
/dev/sda2: PTTYPE="dos" 
/dev/sda3        91760bb5-455b-4adc-8e34-a8f2d5cae023   ext3                                     
/dev/sda5        6ceb25f1-5904-490b-a7cc-d14b9d63c3b7   ext3       Jaunty Root                   
/dev/sda6        238b5ad8-c8fd-4c65-a190-1828af9fe54a   ext3       Jaunty Home                   
/dev/sda7        51ebb887-909b-43cb-b022-1300ddd78074   ext3       Gloria Root                   
/dev/sda8        2c9d2789-e4b6-46c3-b9c8-145951f916cc   ext3       Gloria Home                   
/dev/sda9        ee620c21-7f87-41fb-a7af-d868f72ce754   ext3       Hardy Root                    
/dev/sda: PTTYPE="dos" 
/dev/sdb10       63839fec-0a76-40f4-b049-12469e5eee7b   ext3       Backups                       
/dev/sdb1        5A3CAE183CADEEE7                       ntfs       Old Win XP                    
/dev/sdb2        4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1   ext4       Fedora-12-i686-L              
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        dcdced28-c63f-4405-b143-05876492b04d   ext4       Fedora 12 Home                
/dev/sdb6        58aec1b2-6dfe-4f02-b77d-207fe6cc5551   swap                                     
/dev/sdb7        571cfad8-68c7-4703-883e-c0baa2a381d4   ext3       Documents                     
/dev/sdb8        05289ee4-d681-4806-b6fd-aefd784f9323   ext3       Downloads                     
/dev/sdb9        ded953b6-3c52-4b2b-9053-d5d99f193f5e   ext3       Pictures                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sdb8        /mnt/sdb8                ext3       (rw)
/dev/sda11       /home                    ext3       (rw)
/dev/sdb7        /mnt/sdb7                ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-18-generic
uuid		6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-18-generic

title		Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode)
uuid		6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
kernel		/boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro  single
initrd		/boot/initrd.img-2.6.28-18-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda7 during installation
UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7  /               ext3         relatime,errors=remount-ro  0  1  
# /home was on /dev/sda8 during installation
UUID=238b5ad8-c8fd-4c65-a190-1828af9fe54a  /home           ext3         relatime                    0  2  
# swap was on /dev/sda6 during installation
UUID=bc99fdc7-0dd8-40e7-8567-f0882352d256  none            swap         sw                          0  0 
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
#/dev/fd0                                  /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
#/dev/sdb7                                 /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4  /mnt/sdb7       ext3         defaults                    0  2  
#/dev/sdb8                                 /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
UUID=05289ee4-d681-4806-b6fd-aefd784f9323  /mnt/sdb8       ext3         defaults                    0  2  

=================== sda5: Location of files loaded by Grub: ===================


  26.5GB: boot/grub/menu.lst
  26.4GB: boot/initrd.img-2.6.28-17-generic
  26.4GB: boot/initrd.img-2.6.28-18-generic
  26.5GB: boot/vmlinuz-2.6.28-17-generic
  26.4GB: boot/vmlinuz-2.6.28-18-generic
  26.4GB: initrd.img
  26.4GB: initrd.img.old
  26.5GB: vmlinuz

=========================== sda7/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## Graphical boot menu location
gfxmenu=/boot/gfxmenu/linuxmint.message

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
#timeout		10

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Linux Mint 7 Gloria, kernel 2.6.28-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
initrd		/boot/initrd.img-2.6.28-15-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single 
initrd		/boot/initrd.img-2.6.28-16-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single 
initrd		/boot/initrd.img-2.6.28-15-generic
savedefault
boot

# Added by me

title		Ubuntu 9.10, kernel 2.6.31-10-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-10-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro single 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault

title		Ubuntu 9.10, kernel 2.6.31-9-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-9-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-9-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-9-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-9-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro single 
initrd		/boot/initrd.img-2.6.31-9-generic
savedefault

title		Ubuntu 9.10, kernel 2.6.31-5-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-5-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-5-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=7db477ac-4ebe-4127-9c3d-21f12ab406e4 ro single 
initrd		/boot/initrd.img-2.6.31-5-generic
savedefault
boot


=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda9 during installation
UUID=51ebb887-909b-43cb-b022-1300ddd78074  /               ext3         relatime,errors=remount-ro  0  1  
# /home was on /dev/sda10 during installation
UUID=2c9d2789-e4b6-46c3-b9c8-145951f916cc  /home           ext3         relatime                    0  2  
# swap was on /dev/sda6 during installation
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d  none            swap         sw                          0  0  
#/dev/sdb7                                 /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4  /mnt/sdb7       ext3         errors=remount-ro           0  2  
#/dev/sdb8                                 /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
UUID=05289ee4-d681-4806-b6fd-aefd784f9323  /mnt/sdb8       ext3         errors=remount-ro           0  2  
/dev/scd1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
#/dev/sdb7                                 /media/sdb7     ext3         defaults                    0  2  
#/dev/sdb8                                 /media/sdb8     ext3         errors=remount-ro           0  2  

=================== sda7: Location of files loaded by Grub: ===================


  39.0GB: boot/grub/menu.lst
  38.9GB: boot/grub/stage2
  38.8GB: boot/initrd.img-2.6.28-11-generic
  36.9GB: boot/initrd.img-2.6.28-13-generic
  38.8GB: boot/initrd.img-2.6.28-14-generic
  38.6GB: boot/initrd.img-2.6.28-15-generic
  36.9GB: boot/vmlinuz-2.6.28-11-generic
  38.8GB: boot/vmlinuz-2.6.28-13-generic
  38.8GB: boot/vmlinuz-2.6.28-14-generic
  36.8GB: boot/vmlinuz-2.6.28-15-generic
  38.6GB: initrd.img
  38.8GB: initrd.img.old
  36.8GB: vmlinuz
  38.8GB: vmlinuz.old

=========================== sda9/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
initrd		/boot/initrd.img-2.6.24-27-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro single
initrd		/boot/initrd.img-2.6.24-27-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                        /proc           proc         defaults                    0  0  
# /dev/sda13
UUID=ee620c21-7f87-41fb-a7af-d868f72ce754   /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda14
UUID=bc1516d1-981b-4797-a1ad-7379b2e5fa67   /home           ext3         relatime                    0  2  
# /dev/sda9
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d   none            swap         sw                          0  0  
/dev/scd1                                   /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd0                                   /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                    /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
#/dev/sdb7                                  /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4   /mnt/sdb7       ext3         defaults                    0  2  
#/dev/sdb8                                  /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
UUID=05289ee4-d681-4806-b6fd-aefd784f9323   /mnt/sdb8       ext3         defaults                    0  2  

  
#/dev/sdb7                                  /media/sdb7     ext3         defaults                    0  0  
#/dev/sdb8                                  /media/sdb8     ext3         defaults                    0  0  
#/dev/sdb7                                  /mnt/sdb7       ext3         auto,users,exec,relatime    0  0  
#UUID=571cfad8-68c7-4703-883e-c0baa2a381d4  /mnt/sdb7       ext3         defaults                    0  2  
#/dev/sdb8                                  /mnt/sdb8       ext3         auto,users,exec,relatime    0  0  
#UUID=05289ee4-d681-4806-b6fd-aefd784f9323  /mnt/sdb8       ext3         defaults                    0  2  


/dev/sdb7                                   /media/sdb7     ext3         defaults                    0  0  
/dev/sdb8                                   /media/sdb8     ext3         errors=remount-ro           0  0  

=================== sda9: Location of files loaded by Grub: ===================


  48.6GB: boot/grub/menu.lst
  48.4GB: boot/grub/stage2
  46.7GB: boot/initrd.img-2.6.24-24-generic
  46.7GB: boot/initrd.img-2.6.24-24-generic.bak
  46.7GB: boot/initrd.img-2.6.24-26-generic
  46.7GB: boot/initrd.img-2.6.24-26-generic.bak
  46.8GB: boot/initrd.img-2.6.24-27-generic
  46.7GB: boot/initrd.img-2.6.24-27-generic.bak
  46.7GB: boot/vmlinuz-2.6.24-24-generic
  46.7GB: boot/vmlinuz-2.6.24-26-generic
  46.8GB: boot/vmlinuz-2.6.24-27-generic
  46.8GB: initrd.img
  46.7GB: initrd.img.old
  46.8GB: vmlinuz
  46.7GB: vmlinuz.old

========================== sda12/boot/grub/menu.lst: ==========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=33b90c3d-da7e-4671-b78a-5adafb0a927d

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		33b90c3d-da7e-4671-b78a-5adafb0a927d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro quiet splash
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		33b90c3d-da7e-4671-b78a-5adafb0a927d
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro single
initrd		/boot/initrd.img-2.6.31-20-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
#UUID=238b5ad8-c8fd-4c65-a190-1828af9fe54a /home           ext3    defaults        0       2
# /home moved to sda12
UUID=4f260672-aff0-4912-9bb3-5e8c2b6158d2 /home           ext3    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda12: Location of files loaded by Grub: ===================


  63.2GB: boot/grub/menu.lst
  63.2GB: boot/grub/stage2
  62.1GB: boot/initrd.img-2.6.31-19-generic
  62.4GB: boot/initrd.img-2.6.31-20-generic
  62.3GB: boot/vmlinuz-2.6.31-14-generic
  62.1GB: boot/vmlinuz-2.6.31-19-generic
  62.1GB: boot/vmlinuz-2.6.31-20-generic
  62.4GB: initrd.img
  62.1GB: initrd.img.old
  62.1GB: vmlinuz
  62.1GB: vmlinuz.old

========================== sda18/boot/grub/grub.cfg: ==========================

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
insmod ext2
set root=(hd0,18)
search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
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
set locale_dir=/boot/grub/locale
set lang=en
insmod gettext
set timeout=60
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,18)
search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686" {
	insmod ext2
	set root=(hd0,18)
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	echo	Loading Linux 2.6.32-trunk-686 ...
	linux	/boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro  splash quiet quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-trunk-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (recovery mode)" {
	insmod ext2
	set root=(hd0,18)
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	echo	Loading Linux 2.6.32-trunk-686 ...
	linux	/boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro single  splash quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-trunk-686
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/hda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set c02402022401fc62
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/hda12)" {
	insmod ext2
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/hda12)" {
	insmod ext2
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic (on /dev/hda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 9c10b8f7-89d3-4a72-a0ab-e89d061653b0
	linux /boot/vmlinuz-2.6.32-16-generic root=UUID=9c10b8f7-89d3-4a72-a0ab-e89d061653b0 ro quiet splash
	initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu lucid (development branch), kernel 2.6.32-16-generic (recovery mode) (on /dev/hda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 9c10b8f7-89d3-4a72-a0ab-e89d061653b0
	linux /boot/vmlinuz-2.6.32-16-generic root=UUID=9c10b8f7-89d3-4a72-a0ab-e89d061653b0 ro single
	initrd /boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/hda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/hda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (on /dev/hda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode) (on /dev/hda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/hda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/hda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/hdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 5a3cae183cadeee7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Fedora (2.6.31.12-174.2.22.fc12.i686) (on /dev/hdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.12-174.2.22.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.12-174.2.22.fc12.i686.img
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/hdb2)" {
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda18/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/hda18 during installation
UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 /               ext3    errors=remount-ro 0       1
# /home was on /dev/hda19 during installation
UUID=c67d9b53-8226-4c67-ab44-2f189e058b47 /home           ext3    defaults        0       2
# swap was on /dev/hda14 during installation
UUID=bc99fdc7-0dd8-40e7-8567-f0882352d256 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda18: Location of files loaded by Grub: ===================


  71.6GB: boot/grub/core.img
  71.7GB: boot/grub/grub.cfg
  71.7GB: boot/initrd.img-2.6.32-trunk-686
  71.7GB: boot/initrd.img-2.6.32-trunk-686.bak
  71.7GB: boot/vmlinuz-2.6.32-trunk-686
  71.7GB: initrd.img
  71.7GB: vmlinuz

=========================== sda3/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 91760bb5-455b-4adc-8e34-a8f2d5cae023
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 91760bb5-455b-4adc-8e34-a8f2d5cae023
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=60
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 91760bb5-455b-4adc-8e34-a8f2d5cae023
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 91760bb5-455b-4adc-8e34-a8f2d5cae023
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=91760bb5-455b-4adc-8e34-a8f2d5cae023 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 91760bb5-455b-4adc-8e34-a8f2d5cae023
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=91760bb5-455b-4adc-8e34-a8f2d5cae023 ro single  splash quiet
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c02402022401fc62
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda12)" {
	insmod ext2
	set root='(hd0,12)'
	search --no-floppy --fs-uuid --set 33b90c3d-da7e-4671-b78a-5adafb0a927d
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=33b90c3d-da7e-4671-b78a-5adafb0a927d ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro splash quiet quiet
	initrd /boot/initrd.img-2.6.32-trunk-686
}
menuentry "Debian GNU/Linux, with Linux 2.6.32-trunk-686 (recovery mode) (on /dev/sda18)" {
	insmod ext2
	set root='(hd0,18)'
	search --no-floppy --fs-uuid --set 84f9bd6c-4042-495a-99c5-2136f706bfc3
	linux /boot/vmlinuz-2.6.32-trunk-686 root=UUID=84f9bd6c-4042-495a-99c5-2136f706bfc3 ro single splash quiet
	initrd /boot/initrd.img-2.6.32-trunk-686
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-18-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 6ceb25f1-5904-490b-a7cc-d14b9d63c3b7
	linux /boot/vmlinuz-2.6.28-18-generic root=UUID=6ceb25f1-5904-490b-a7cc-d14b9d63c3b7 ro single
	initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Linux Mint 7 Gloria, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set 51ebb887-909b-43cb-b022-1300ddd78074
	linux /boot/vmlinuz-2.6.28-15-generic root=/dev/sda7 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro quiet splash
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sda9)" {
	insmod ext2
	set root='(hd0,9)'
	search --no-floppy --fs-uuid --set ee620c21-7f87-41fb-a7af-d868f72ce754
	linux /boot/vmlinuz-2.6.24-27-generic root=UUID=ee620c21-7f87-41fb-a7af-d868f72ce754 ro single
	initrd /boot/initrd.img-2.6.24-27-generic
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 5a3cae183cadeee7
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Fedora (2.6.31.12-174.2.22.fc12.i686) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.12-174.2.22.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.12-174.2.22.fc12.i686.img
}
menuentry "Fedora (2.6.31.5-127.fc12.i686) (on /dev/sdb2)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1
	linux /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=91760bb5-455b-4adc-8e34-a8f2d5cae023 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda11 during installation
UUID=3128dea7-b986-4b45-8004-0b48bf97f9dd /home           ext3    defaults        0       2
#/dev/sdb7    /mnt/sdb7 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sdb7       ext3    defaults        0       2
#/dev/sdb8    /mnt/sdb8 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sdb8       ext3    defaults        0       2
# swap was on /dev/sda14 during installation
UUID=bc99fdc7-0dd8-40e7-8567-f0882352d256 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
#UUID=58aec1b2-6dfe-4f02-b77d-207fe6cc5551 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


=================== sda3: Location of files loaded by Grub: ===================


  20.3GB: boot/grub/core.img
  20.3GB: boot/grub/grub.cfg
  20.3GB: boot/initrd.img-2.6.32-16-generic
  20.2GB: boot/vmlinuz-2.6.32-16-generic
  20.3GB: initrd.img
  20.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


========================== sdb2/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,1)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb2
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sdb2
default=0
timeout=5
splashimage=(hd1,1)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.12-174.2.22.fc12.i686)
	root (hd1,1)
	kernel /boot/vmlinuz-2.6.31.12-174.2.22.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.12-174.2.22.fc12.i686.img
title Fedora (2.6.31.5-127.fc12.i686)
	root (hd1,1)
	kernel /boot/vmlinuz-2.6.31.5-127.fc12.i686 ro root=UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /boot/initramfs-2.6.31.5-127.fc12.i686.img
title Other
	rootnoverify (hd0,0)
	chainloader +1

=============================== sdb2/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Sat Feb 27 21:07:49 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=4afe8bf2-f7c6-4c7a-b7ee-77d9541065d1 /                       ext4    defaults        1 1
UUID=dcdced28-c63f-4405-b143-05876492b04d /home                   ext4    defaults        1 2
UUID=2897adb6-b16f-4ba7-901f-2aec9e1c994d swap                    swap    defaults        0 0
UUID=58aec1b2-6dfe-4f02-b77d-207fe6cc5551 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sdb2: Location of files loaded by Grub: ===================


  19.4GB: boot/grub/grub.conf
  19.4GB: boot/grub/menu.lst
  17.4GB: boot/grub/stage2
  19.4GB: boot/initramfs-2.6.31.12-174.2.22.fc12.i686.img
  17.8GB: boot/initramfs-2.6.31.5-127.fc12.i686.img
  19.4GB: boot/vmlinuz-2.6.31.12-174.2.22.fc12.i686
  17.3GB: boot/vmlinuz-2.6.31.5-127.fc12.i686
```

Obviously grub can't be installed to an extended partition :)

Oh, and everything worked there.

---

### Post by Ardghal on 2010-06-09
[QUOTE=ronparent]The easiest thing for you to try is to set what is currently sdb as 1st in bios boot order. If that works you are home free! Incidently that should work even though 10.04 is installed to what is now sda. Good luck. [/QUOTE]

I wanted to do that, but I didn't see where that was, I mean, the only option that looked like that, didn't show my SATA drive, only the IDE one, and I don't know much about changing settings in the BIOS, so I left it alone.

[QUOTE=darkod]Anyway, from live mode do:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It should be fine after that. [/QUOTE]

I tried that, but it didn't work as there was "no sda6 partition". Apparently now the live CD Ubuntu named the SATA disk "sdb" and "sda" the IDE one. Or maybe the script named them differently?

Anyway, I changed the name and it installed correctly. Now I have GRUB working, and I can also enter into Windows 7 and XP. So that part is fixed. Thank you both for your help! :D

However... I still can't get into Ubuntu. As it was starting, a message appeared on the startup screen:

[B]The disk drive for /home is not ready yet or not present

Continue to wait; or Press S to skip mounting or M for manual recovery[/B]

So maybe I didn't install Ubuntu right? I had never had a separate partition for /home, so I don't know if I did it right. I just marked one of the partitions to be /home, from the drop down list in the installer.

Waiting didn't seem to work, as nothing happened, and not even the hard drive light was on. Nothing. Pressing S started the system but it couldn't even load the desktop and I had to hit reset to get out of there. And pressing M sent me to the command line, but I didn't know what to do there. I tried mount /dev/sdb7, which I believe is the /home partition, but it said something about it not being in /etc/fstab, even though it was... I don't know if that was even a right command to try. :P

What should I do? :confused:

---

### Post by arrange on 2010-06-10
As the traditional labelling (like */dev/sda6*) is unreliable here, I think you should use UUID in your */etc/fstab* file. Back the file up, and change the lines```
/dev/sdb6       /               ext4    errors=remount-ro 0       1
/dev/sdb7       /home           ext4    defaults        0       2

```

into```
UUID=62a62c0a-a7fb-4795-b5f9-e4cca65d617d       /               ext4    errors=remount-ro 0       1
UUID=77c63b16-4613-4c77-b263-ea4cc102882f       /home           ext4    defaults        0       2

```You should do the same for the *swap* partition, but as there is no UUID label for it in *blkid* now, let's leave it until later, it's not essential.

---

### Post by Ardghal on 2010-06-10
> **arrange said:**
> As the traditional labelling (like */dev/sda6*) is unreliable here, I think you should use UUID in your */etc/fstab* file. Back the file up, and change the lines```
/dev/sdb6       /               ext4    errors=remount-ro 0       1
/dev/sdb7       /home           ext4    defaults        0       2

```

into```
UUID=62a62c0a-a7fb-4795-b5f9-e4cca65d617d       /               ext4    errors=remount-ro 0       1
UUID=77c63b16-4613-4c77-b263-ea4cc102882f       /home           ext4    defaults        0       2

```You should do the same for the *swap* partition, but as there is no UUID label for it in *blkid* now, let's leave it until later, it's not essential.

I did that and it worked. I can finally get into Ubuntu. \\:D/

Thanks! :D

---

### Post by arrange on 2010-06-10
Do you have *swap* enabled?```
swapon -s
```

---

### Post by Ardghal on 2010-06-11
Oh, good catch. It seems swap wasn't even on, either. :(

So, now I just removed the entire OS and installed 9.10. As soon as I can figure out how to get the Internet connection working, I'll upgrade from there and see what happens. 

Just as a comment, none of the problems I had so far with the 10.04 installation, appeared during the 9.10 one. :-s

---

