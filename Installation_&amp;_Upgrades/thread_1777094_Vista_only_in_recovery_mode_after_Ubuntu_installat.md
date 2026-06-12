---
title: "Vista only in recovery mode after Ubuntu installation"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by JGMS on 2011-06-07
Hi all,

I installed Ubuntu 10.04 32 bit on an Acer Aspire 7520 laptop running Vista.
Thereafter, Vista could only be run via the "Windows Recovery Environment" grub menu option, which is on /dev/sda2. However, within Vista than the wireless network is not functioning any more. It has given lot of headaches to find a way out. Unsuccessful, so far.

When I run "sudo fdisk -l"in the terminal then the following information is returned.

[INDENT]Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes
in-/uitvoergrootte (minimaal/optimaal): 512 bytes / 512 bytes
Schijf-ID: 0x6373a96b

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1        1274    10233373+  12  Compaq diagnostiek
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       19458    72892417    5  Uitgebreid
/dev/sda5           10383       19082    69876736   83  Linux
/dev/sda6           19082       19458     3014656   82  Linux wisselgeheugen[/INDENT]

Can anybody please help to get the Windows Vista loader to work again. 
Many thanks ahead.

JGMS

---

### Post by Quackers on 2011-06-07
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by JGMS on 2011-06-07
Thank you for your reply and hints. 
Here is the content of the results.text file.

Kind regards, JaGMS

CODE]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2088.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Schijf /dev/sda: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders, totaal 312581808 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,467,712   166,793,215   146,325,504   6 FAT16
/dev/sda3         166,795,262   312,580,095   145,784,834   5 Extended
/dev/sda5         166,795,264   306,548,735   139,753,472  83 Linux
/dev/sda6         306,550,784   312,580,095     6,029,312  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Schijf /dev/sdb: 8065 MB, 8065646592 bytes
25 koppen, 25 sectoren/spoor, 25205 cilinders, totaal 15753216 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,088    15,753,215    15,751,128   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        92ECE12CE49BED2A                       ntfs       PQSERVICE
/dev/sda2        5278E79078E77161                       ntfs       ACER
/dev/sda5        a80dbebb-d580-4e09-99cd-206168cce6ee   ext4       
/dev/sda6        6530ce57-0c7d-42db-9e09-b0dbff4d401c   swap       
/dev/sdb1        7B03-8EAF                              vfat       Kingston8G

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/Kingston8G        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
menuentry 'Ubuntu, met Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-32-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-32-generic...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-30-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-30-generic...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-29-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-29-generic...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-28-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-28-generic...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-25-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-25-generic...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro  vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, met Linux 2.6.32-21-generic (herstelmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	echo	'Laden van Linux 2.6.32-21-generic...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=a80dbebb-d580-4e09-99cd-206168cce6ee ro single  vga=773
	echo	'Laden van initiële ramdisk...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set a80dbebb-d580-4e09-99cd-206168cce6ee
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 92ece12ce49bed2a
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5278e79078e77161
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a80dbebb-d580-4e09-99cd-206168cce6ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6530ce57-0c7d-42db-9e09-b0dbff4d401c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 119.669277191 = 128.493907968  boot/grub/core.img                             1
  95.728145599 = 102.787313664  boot/grub/grub.cfg                             1
 119.686458588 = 128.512356352  boot/initrd.img-2.6.32-21-generic              1
 119.802284241 = 128.636723200  boot/initrd.img-2.6.32-25-generic              1
 119.854106903 = 128.692367360  boot/initrd.img-2.6.32-28-generic              1
 119.865303040 = 128.704389120  boot/initrd.img-2.6.32-29-generic              1
 119.876502991 = 128.716414976  boot/initrd.img-2.6.32-30-generic              1
 119.883934021 = 128.724393984  boot/initrd.img-2.6.32-32-generic              1
 119.665370941 = 128.489713664  boot/vmlinuz-2.6.32-21-generic                 1
 119.787940979 = 128.621322240  boot/vmlinuz-2.6.32-25-generic                 1
 119.793281555 = 128.627056640  boot/vmlinuz-2.6.32-28-generic                 1
 119.857872009 = 128.696410112  boot/vmlinuz-2.6.32-29-generic                 1
 119.869071960 = 128.708435968  boot/vmlinuz-2.6.32-30-generic                 1
 119.809196472 = 128.644145152  boot/vmlinuz-2.6.32-32-generic                 1
 119.883934021 = 128.724393984  initrd.img                                     1
 119.876502991 = 128.716414976  initrd.img.old                                 1
 119.809196472 = 128.644145152  vmlinuz                                        1
 119.869071960 = 128.708435968  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo0/sda2: apparaat is bezig
        (Welke processen het apparaat gebruiken kan mogelijk
         gevonden worden met behulp van lsof(8) of fuser(1).)[/CODE]

---

### Post by Quackers on 2011-06-07
So from the grub menu you select the Vista Recovery menu entry then Vista boots. Is that correct? That used to be normal for grub - it transposed the actual partition and the recovery partition, but it boots vista properly. Your internet connection in vista may need the diagnostics to be run on it. Mine does it sometimes, if I have used Linux with the same router for a long period. Try that please.

---

### Post by JGMS on 2011-06-07
Yes indeed.

Vista starts about normal via the Recovery Environment grub line. Starting with the "Windows Vista" loader line, which to me appears as the primary entry, does not start Vista but seems to bring the laptop in a sort of restore mode (probably to repair things in the Vista system) and stops at not finding a particular file.

Tomorrow (the laptop is in use at another location now), I will try the wireless diagnostics, as you suggested.

Thank you and kind regards, 

JGMS

---

### Post by Quackers on 2011-06-07
You're welcome.
With slightly older versions of grub this behaviour is absolutely normal. You just need to remember to choose the recovery option when you want to use vista.
The "normal" entry will boot the recovery programme, which, if run to its conclusion, will wipe your hard drive and re-install the OEM version of Vista to the state it was in when you bought the computer. In other words you will lose everything on your system if it is run completely.
Vista may need to reset your router so that it works with Windows. As I said earlier, this happens some times on my laptop. It usually works ok after that.

---

### Post by JGMS on 2011-06-08
OK,

so to minimise confusion for the user (not myself;)), the best thing to do is to edit the grub file: delete the Windows Vista (loader) line and rename the "recovery one" just as "VISTA". Obviously assuming that I can get the wireless lan back to work.
You will hear about that.
Thanks again,

JGMS

---

### Post by JGMS on 2011-06-08
I managed to get the wireless lan functioning by digging a bit in the Windows stuf. Boy, am I glad to use Ubuntu!

Thank you once again for putting me on the right track and sorry for thinking that Ubuntu installation caused the problem.

Regards, JGMS

---

### Post by Quackers on 2011-06-08
You're welcome.
Did you edit grub.cfg file manually? Or did you make changes in /etc/grub.d scripts?
Changes made to grub.cfg directly will be over-written when grub gets updated!
You can edit what you need to using item 7 in the link below

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by JGMS on 2011-06-10
I will surely follow your hint on this to update grub! Besides, the method to reduce the ever extending listing of the grub menu was exactly what I intended to look into next. Great tip! Thanks again.

regards, jgms

---

