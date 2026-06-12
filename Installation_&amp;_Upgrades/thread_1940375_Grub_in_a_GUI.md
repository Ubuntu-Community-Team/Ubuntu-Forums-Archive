---
title: "Grub in a GUI?"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by Aesculus on 2012-03-13
Is there any application about GRUB commands, configurations... similar to GParted for partition commands?
I'm thinking in something that allows you create a backup info useful to recover from disasters. When I upgraded to Ubuntu 11, it took me hours to recover the crash, using several tools, checking versions.... Cause I didn't change the hardware or partitions if I had something like that I could have the system up in minutes, I think.
Regards

---

### Post by oldfred on 2012-03-13
Welcome to the forums.

Not sure what you want to backup. Grub2's boot loader can easily be reinstalled and that is often easier than restoring.

Sometimes having the entire system documented is a good idea. I use the boot info script that we use for debugging boot issues, just to have a document of my boot configuration before & after any major change.

You can also run boot script from Boot-Repair which is handy to have as it can often make repairs and also adds some documentation of its own.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Herman on 2012-03-13
You mean like integrate Super Grub Disk with GParted a lot more?

The last time I checked, Parted Magic Live CD included Super Grub Disk, but as a separate program. At least you could use GParted in the Parted Magic Live CD to take a look at your disks and partition info before you use Super Grub Disk. 
I haven't tried out Super Grub Disk for a long time, so I'm not sure what it can do now.

Integrating Grub commands into GParted might be worth thinking about. It probably would help new users if they could click on the GParted graphical disk and partition representation to tell a program which hard disk's MBR they want to install Grub to, or which partition they want GRUB's boot files created or refreshed in, or a new grub.cfg made. That would be a neat idea. So the commands to be run in the background would be assembled by the mouse clicks in GUI.

There are only two commands we really need, grub-mkconfig and grub-install.

The grub-install command installs GRUB to MBR in a hard disk or whatever kind of disk it is, and it creates or re-creates all the files in the /boot/grub folder in case they are missing or corrupted.

The grub-mkconfig command is the same as update-grub, either of them run grub-mkconfig and other sub-commands and ultimately scan the computer for other operating systems or for scripts to add custom items to the boot menu and create a new grub.cfg. With the grub-mkconfig command it's possible to direct the new config file to a specific location and give it a unique name if you want to for some special reason.

To implement those two commands at present you can use a Live CD and chroot into your stricken operating system first. The chroot process is the part that is kind of hard for new users, I would rather avoid it myself. 
It is possible to run grub-setup to install just the MBR part of GRUB from a Live CD without the need to chroot. (The grub-install command includes grub-setup as a sub-command so a person can get away without learning that one if they want).

The easiest way to fix just about any GRUB problem is to boot a USB drive or any other drive that has another installation of Ubuntu in it and run either update-grub or grub-mkconfig to scan the computer and add the computer's operating systems to the USB Ubuntu installations GRUB Menu.
The reboot the USB again, and stop at the GRUB Menu by pressing any key. 
Choose your computer's internal Ubuntu operating system and after it boots, run the grub-install command.

Windows boot problems are normally quite easily fixed with a Windows installation disk, but this requires the user to have a disk and know how to use it.

If GRUB was integrated into GParted, or some other program similar I wonder how safe that would be in the hands of a practical joker though, or somebody malicious? 
I hesitate here because I'm worried it could be putting too much power into stupid people's hands. It might be best to just leave things as they are.

What to other people think?

---

### Post by YannBuntu on 2012-03-16
Hello, there are 2 useful GUI for GRUB:

**1) [Grub-Customizer]("https://launchpad.net/grub-customizer") :** convenient to play with GRUB (change entries order, hide an entry..). But be careful: playing too much can break your boot.

**2) [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") :** concentrates on fixing boot (access to Ubuntu and other OS). Provides a 1-click "Recommended repair", options to fix GRUB, and useful information to get help on the forum.

---

### Post by Herman on 2012-03-16
Cool!

So I imagine we just open GParted and minimize it to one side of your monitor to see disk and partition info while running Grub-Customaizer or Boot-Repair in the other half of the screen? :)

---

### Post by YannBuntu on 2012-03-18
Hello
> **Herman said:**
> So I imagine we just open GParted and minimize it to one side of your monitor to see disk and partition info while running Grub-Customaizer or Boot-Repair in the other half of the screen? :)

I don't understand. What would you like to do?

---

### Post by Herman on 2012-03-19
It's okay, I'll try them both out and see for myself. I have read the linked web pages and they both look like very nice apps and should be very helpful to people. :)

---

### Post by Herman on 2012-04-21
I'm trying out Grub-Customizer and Boot-Repair and they both work great! 
They're just what has been needed for a long time. Well done! :)

---

### Post by Aesculus on 2012-05-04
First of all, thanks for the information and suggestions provided. I've not marked the thread as solved cause I couldn't solve. Now, I have same problem when change from Ubuntu 11 to 12.

But let's go step by step. First I asked for a GUI interface cause I think see partitions and info in a graphic mode is much easier for me. It's not only see things in windows and buttons, but also in a graphic way. When I run GParted I can see in a snapshot how many disks, partitions with colors, info around the system has. Imagine the same with an icon or a magnified part of the hdd graphic draw, indicating that grub is in the MBR and with a click you could see the version or other useful info. If someone is interested I can only help wit the look&feel part.

About my problem, that as mention before, I have again. I've re-installed grub2 in hda, forcing to reinstall with boot-repair-disk. The process in all cases end without errors but afterwards I get the message "no such partition" after chose any option of grub menu.

I have my configuration saved (you can check with log of boot-repair-disk) 
hdd1
primary  120GB /dev/sda1 ext4 bootable
(g: )extended 81 GB /dev/sda2 w95 
             4,3 swap /dev/sda7          
             2   swap /dev/sda6
             74  NTFS /dev/sda5
hdd2
(c: )primary 105 GB /dev/sdb1 NTFS bootable
(d: )primary 895 GB /dev/sdb2 NTFS

And I get this results using Hiren's CD to boot.

HDD1 MBR error, no possible to boot from here
HDD1 Partition 1, starts Win
HDD2 MBR grub menu works and I can start the OS I prefer
HDD2 Partition 1, error. "chainloader +1 is not an executable format...."

For me this is weird cause Win system (c: ) is in HDD2 partition 1, meanwhile Partition 1 of HDD1 is for Ubuntu. I recognize that I have few knowledge about this.

Thanks for any help before insert log from boot-repair-disk:
```

                 Boot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390719855 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   233,461,759   233,459,712  83 Linux
/dev/sda2         233,463,806   390,700,799   157,236,994   f W95 Extended (LBA)
/dev/sda5         245,762,433   390,700,799   144,938,367   7 NTFS / exFAT / HPFS
/dev/sda6         241,846,272   245,762,047     3,915,776  82 Linux swap / Solaris
/dev/sda7         233,463,808   241,844,223     8,380,416  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 NTFS / exFAT / HPFS
/dev/sdb2         204,796,620 1,953,520,064 1,748,723,445   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        555252df-082a-4386-ae8c-0c10974ecc5a   ext4       
/dev/sda5        1440E6FC40E6E408                       ntfs       Fortusr
/dev/sda6        153dcfab-20b3-4241-891e-e93349fb2b9e   swap       
/dev/sda7        9896a02a-c2a0-4f34-8a3b-5178a5cfdfb2   swap       
/dev/sdb1        263C65E13C65AD0D                       ntfs       PROGRAMAS
/dev/sdb2        06E4DBEFE4DBDF4D                       ntfs       DATOS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	echo	'Loading Linux 3.2.0-24-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	linux	/boot/vmlinuz-3.0.0-19-generic-pae root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.0.0-19-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	echo	'Loading Linux 3.0.0-19-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-19-generic-pae root=UUID=555252df-082a-4386-ae8c-0c10974ecc5a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 555252df-082a-4386-ae8c-0c10974ecc5a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 263C65E13C65AD0D
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=555252df-082a-4386-ae8c-0c10974ecc5a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9896a02a-c2a0-4f34-8a3b-5178a5cfdfb2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.0.0-19-generic-pae           2
            ?? = ??             boot/initrd.img-3.2.0-24-generic               2
            ?? = ??             boot/initrd.img-3.2.0-24-generic-pae           1
            ?? = ??             boot/vmlinuz-3.0.0-19-generic-pae              1
            ?? = ??             boot/vmlinuz-3.2.0-24-generic                  1
            ?? = ??             boot/vmlinuz-3.2.0-24-generic-pae              1
            ?? = ??             vmlinuz                                        1
            ?? = ??             vmlinuz.old                                    1

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
cat: write error: Broken pipe
File descriptor 7 (pipe:[5872]) leaked on lvscan invocation. Parent PID 6233: bash
File descriptor 8 (pipe:[5872]) leaked on lvscan invocation. Parent PID 6233: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-05-04__12h18 ****************
boot-repair version : 3.16-0ppa10~lucid
boot-sav version : 3.17-0ppa18~lucid
/usr/share/boot-sav/gui-update.sh: line 31: hash: glade2script: not found
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
internet: connected
File descriptor 7 (pipe:[5872]) leaked on lvs invocation. Parent PID 3319: /bin/sh
File descriptor 8 (pipe:[5872]) leaked on lvs invocation. Parent PID 3319: /bin/sh
No volume groups found
LIVESESSION is : yes (Debian GNU/Linux 6.0.3 (squeeze) , squeeze , Debian , i686  )
BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.
BYTES_BEFORE_PART[2] (sdb) = 63 sectors * 512 bytes = 32256 bytes.

OSPROBER:
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain

BLKID:
/dev/sda1: UUID="555252df-082a-4386-ae8c-0c10974ecc5a" TYPE="ext4"
/dev/sda5: LABEL="Fortusr" UUID="1440E6FC40E6E408" TYPE="ntfs"
/dev/sda6: UUID="153dcfab-20b3-4241-891e-e93349fb2b9e" TYPE="swap"
/dev/sda7: UUID="9896a02a-c2a0-4f34-8a3b-5178a5cfdfb2" TYPE="swap"
/dev/sdb1: LABEL="PROGRAMAS" UUID="263C65E13C65AD0D" TYPE="ntfs"
/dev/sdb2: LABEL="DATOS" UUID="06E4DBEFE4DBDF4D" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"

1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
Total of 1 OS detected on sdb disk.
TABLE_TYPE of sda is MSDos
TABLE_TYPE of sdb is MSDos
sda1 : sda, not-sepboot, grub-install, grub2 , update-grub, apt-get, 32, with boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, fstab-without-efi.
sda5 : sda, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda5, no-os, no-gpt, notEFItable, no-fstab.
sdb1 : sdb, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb1, with-os, no-gpt, notEFItable, no-fstab.
sdb2 : sdb, is-maybe-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sdb2, no-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA ST3200822AS (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  120GB  120GB   primary   ext4            boot
2      120GB   200GB  80.5GB  extended                  lba
7      120GB   124GB  4291MB  logical   linux-swap(v1)
6      124GB   126GB  2005MB  logical   linux-swap(v1)
5      126GB   200GB  74.2GB  logical   ntfs


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type     File system  Flags
1      32.3kB  105GB   105GB  primary  ntfs         boot
2      105GB   1000GB  895GB  primary  ntfs



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


MOUNT:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,allow_other,blksize=4096)


/sys/block/sda:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd full fuse hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sda2 sda5 sda6 sda7 sdb sdb1 sdb2 sdc sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 stderr stdin stdout urandom vga_arbiter xconsole zero

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.8G  8.3M  1.8G   1% /
tmpfs        tmpfs    1.8G     0  1.8G   0% /lib/init/rw
udev         tmpfs    1.8G  192K  1.8G   1% /dev
tmpfs        tmpfs    1.8G     0  1.8G   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    1.8G  8.3M  1.8G   1% /live/cow
tmpfs        tmpfs    1.8G     0  1.8G   0% /live
tmpfs        tmpfs    1.8G  8.0K  1.8G   1% /tmp
/dev/sda1     ext4    110G   19G   86G  18% /mnt/boot-sav/sda1
/dev/sda5  fuseblk     70G   15G   55G  21% /mnt/boot-sav/sda5
/dev/sdb1  fuseblk     98G   28G   71G  29% /mnt/boot-sav/sdb1
/dev/sdb2  fuseblk    834G  170G  665G  21% /mnt/boot-sav/sdb2

FDISK:

Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390719855 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8deb8de

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   233461759   116729856   83  Linux
/dev/sda2       233463806   390700799    78618497    f  W95 Ext'd (LBA)
/dev/sda5       245762433   390700799    72469183+   7  HPFS/NTFS
/dev/sda6       241846272   245762047     1957888   82  Linux swap / Solaris
/dev/sda7       233463808   241844223     4190208   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b964b95

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdb2       204796620  1953520064   874361722+   7  HPFS/NTFS



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, reinstall, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda1, PART_TO_REINSTALL_GRUB_PURGE sda1, FORCE_GRUB all (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: connected

************************Actions
FSCK_ACTION no PASTEBIN_ACTION yes
bootinfo, nombraction, REINSTALL_POSSIBLE yes PURGE_POSSIBLE yes
UNHIDEBOOT_ACTION no (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB sda1, PART_TO_REINSTALL_GRUB_PURGE sda1, FORCE_GRUB all (sda) REMOVABLEDISK no
USE_SEPARATEBOOTPART no (sda5) grub2 (sda1)
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 1)
internet: connected

```

---

### Post by YannBuntu on 2012-05-04
Please first make sure your BIOS is setup to boot on your Ubuntu disk first.
If still not good, please try the "Purge GRUB" option of Boot-Repair (and indicate the new URL that will appear).

---

### Post by grahammechanical on 2012-05-04
I am not an expert on this either but I see two Linux swap partitions and you only need one. Even with more than one Ubuntu version installed you only need one as each Ubuntu will use the same swap partition.

Windows XP is on sdb1.

Here is something else that I have noticed. You first start a discussion about having a GUI application to restore a broken Grub but now it seems that you are having problems booting.

So, which do you want help with?

Regards.

---

### Post by Aesculus on 2012-05-04
Thanks for your answer.

> **grahammechanical said:**
> I am not an expert on this either but I see two Linux swap partitions and you only need one. Even with more than one Ubuntu version installed you only need one as each Ubuntu will use the same swap partition.

- Yes, grahammechanical. I only need one. the other is the rest of a previous installation or reinstallation. I think this not affect the system, just waste some megas of disk.

> 
Windows XP is on sdb1.
- It's what I think also, but I don't understand why booting from HDD1 partition1 starts Windows. In this case no grub is being used or at least no signs that grub is running. I will try YannBuntu advice and maybe the key is there.

> 
Here is something else that I have noticed. You first start a discussion about having a GUI application to restore a broken Grub but now it seems that you are having problems booting.

So, which do you want help with?

Regards.

It's my fault mix both things. One problem I have is how to fix the booting with grub to the mode I had. The other is a suggestion cause I thought that a grub software with a real graphic interface would be helpful to better understand how to use grub. It's my opinion of course, and as you can see I'm far to be an expert in grub.

BR.

---

### Post by Aesculus on 2012-05-04
YannBuntu, thanks for your help. You are a genius.

The problem is solved and it was caused by BIOS. I had the following sequence:

1. removable device. (for USB's)
2. CD ROM
3. 4S Samsung (my /dev/sdb)

Apparently I could change order of devices or eliminate but not change the hard drive.
However in other menu of BIOS, there were the possibility to change which one was 1st and 2nd had drive. I modified to the correct one and automatically the boot sequence changed to:

1. removable device. (for USB's)
2. CD ROM
3. 3S ST (my /dev/sda)

And all works properly now.
Thanks to all of you for your goals and specially YannBuntu for the solution.

BR.
PS:Now I have to find the way to mark this as solved :)

---

### Post by YannBuntu on 2012-05-04
Good job :)

---

