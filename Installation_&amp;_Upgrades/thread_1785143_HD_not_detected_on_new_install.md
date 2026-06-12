---
title: "HD not detected on new install"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by ubu nubu on 2011-06-17
Hello,
I am a first time Ubuntu user and I need help.

Ubuntu 11.4 installed on 400GB SATA Drive
I have 2 other SATA HD's and only 1 is being shown in Ubuntu.
The missing drive is Fat 32, and all the drives are visible in bios.
Will you please tell me,
#1 what steps I need to take to find out why Ubuntu is not detecting it?
#2 how to add the drive to Ubuntu? 
Thanks

---

### Post by Quackers on 2011-06-17
Welcome to UF.
Has the "missing" drive been used in a different pc? Did it use raid? Was it a Mac?

---

### Post by ubu nubu on 2011-06-17
Thank you for your reply,
The HD has been in use for a year on this PC.
I reformatted the 400 GB drive that Ubuntu is on and the other 2 drives before this new install.I probably did something wrong when I formatted all the drives, I was very confused by the gparted Ubuntu program. 

Occasionally when I start up the PC there is a Ubuntu screen that pop's up trying to mount a drive.

Occasionally Ubuntu does not recognize either of the drives that Ubuntu in _Not_ installed on.
 

Will you please help me troubleshoot this problem? I'm in over my head.

---

### Post by ubu nubu on 2011-06-17
Sorry,
Forgot to say, if was last used with Windows 7

---

### Post by Quackers on 2011-06-17
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

### Post by ubu nubu on 2011-06-18
[HTML]&#65279;CHANGELOG:
==========

Version 0.60 (2010-05-17)
  * New maintainer: Gert Hulselmans.
  * boot_info_script is now released under the MIT license.
  * Add this CHANGELOG file.
  * Source code changes are now tracked in git:
      http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=summary
  * Big source code reformatting and cleanup of the code and comments.
  * The output file can now be specified by adding the filename as argument:
      bash ./boot_info_script.sh <outputfile>
  * Display help when invoked with the -h, -help or --help switch.
  * Gzip the output file when invoked with the -g or --gzip switch.
    This option will make 2 files: an uncompressed and gzip compressed file.
  * Warn the user if multiple boot_info_script.sh files are found in the same
    directory (file downloaded multiple times with Firefox, Chromium,... ):
      boot_info_script.sh boot_info_script(0).sh boot_info_script(1).sh
  * Add a lot of GUIDs to the GPT Partition type list.
  * Grub support code is rewritten and now handled by one function.
  * Add Grub2 v1.99 support.
  * Display the embedded Grub2/burg config file.
  * Syslinux support added:
      - Check if Syslinux can find its second stage.
      - Display the version number.
      - Display the Syslinux directory in which Syslinux will look first for
        its config file.
      - Display content of Syslinux config file.
      - Display the ADV.
      - List all COM32(R) module files and display the major version number.
  * Support mount paths with spaces.
  * Support more than 26 drives.
  * Add detection for the following MBRs:
      - Different Syslinux MBRs and versions (standard, GPT and ISOhybrid)
      - Diskcryptor
      - FreeDOS
      - SUSE generic MBR
      - Grub4dos
      - WEE
      - XOSL
  * Add detection for grub4dos installed in the PBR.
  * Add detection for FreeDOS PBR code.
  * List additional boot files when found:
      - SYSLINUX/EXTLINUX: ldlinux.sys and extlinux.sys
      - Grub4dos: grldr and grldr.bin
      - burg (Grub2 based): /burg/core.img and /boot/burg/core.img
      - Grub2: added /boot/grub2/core.img as alternative location
      - FreeDOS: kernel.sys
      - DellDiagnostics: dellbio.bin and dellrmk.bin
      - ReactOS: freeldr.sys qnd freeldr.ini
  * Display offset of file on a disk in GB and GiB for Grub(2) and Syslinux.
  * Display embedded config file for Grub4dos/WEE.
  * Add ReactOS support.
  * Most lines in the output file are now 80 characters or less.
  * Prefer gawk above nawk and busybox awk (workaround for bugs in nawk).
  
Version 0.55 (2010-02-15)
  * Show blkid info for all drives.

Version 0.54 (2010-02-14)
  * Display boot_info_script version and release date when invoked with the
    -v, -V or --version switch.
  * Save boot_info_script version and release date in the RESULTS.TXT file.
  * Workaround for blkid -p, when this parameter isn't supported by blkid.

Version 0.53 (2010-02-12)
  * Use "sfdisk -s" instead of "fdisk -s", when available.

Version 0.52 (2010-02-12)
  * Add /wubildr, /ubuntu/winboot/wubildr, /ubuntu/winboot/wubildr.mbr and
    /ubuntu/disks/home.disk to the boot programs list.
  * Handle output of newer versions of filefrag correctly.

Version 0.51 (2010-02-04)
  * Add io.sys, msdos.sys and command.com to the boot programs list.

Version 0.50 (2010-01-29)
  * If a filesystem is already mounted, use the current mountpoint instead of
    creating a new mountpoint.
  * Search all RAID drives detected by dmraid.

Version 0.49 (2010-01-26)
  * Add initramfs to list of files used by grub.
  * Add Acronis SZ PBR detection.
  * Scan also drives without a partition table, but with a filesystem.
  * Display only the mount output for partitions and drives.

Version 0.48 (2010-01-12)
  * Add "ls -R /dev/mapper" output.

Version 0.47 (2010-01-09)
  * Add a separate list for finding config and boot program files on FAT
    partitions.
  * Add Paragon MBR detection.  

Version 0.46 (2010-01-07)

Version 0.45 (2010-01-07)
  * Check if all needed programs are available before running the rest of the
    script.
  * Detect extended partitions linking to another extended partition.

Version 0.44 (2009-12-31)
  * Add Linux Software Raid (dmraid) support.

Version 0.43 (2009-12-30)
  * Rewrite LVM support code.
  * Rewrite Wubi support code.

Version 0.42 (2009-12-20)
  * Add LVM support.
  * Add GUID for BIOS Boot partition.
  
Version 0.41 (2009-12-08)

Version 0.40 (2009-12-07)
  * Display the directory for which core.img of Grub2 looks for its config file
    and module files.

Version 0.39 (2009-12-05)
  * Add support for getting the Slackware version info.

Version 0.38 (2009-12-05)
  * Add support for differenciating between Windows Vista and Windows 7 as OS
    installed on a certain partition.

Version 0.37 (2009-11-28)
  * Small fix for Grub2 v1.97 support.

Version 0.36 (2009-11-19)
  * Add proper Grub2 v1.97 support.

Version 0.35 (2009-11-15)
  * Save the RESULTS.TXT file in the home dir, when the script is located in
    /bin, /sbin, /usr/bin, or other system folders.

Version 0.34 (2009-11-14)
  * Disable some parts of the Grub2 v1.97 support code, which currently doesn't
    work, due missing parts.

Version 0.33 (2009-11-13)
  * Add Grub2 v1.97 support.
  * Add Syslinux, Truecrypt and Master Boot Loader MBR detection.

Version 0.32 (2009-04-17)
  * Add Acer 3 MBR detection.
  * Fix losetup --sizelimit problem (not supported on older versions of losetup).

Version 0.31 (2009-04-14)
  * Some small changes related to BootIt NG.

Version 0.30 (2009-04-10)
  * Only use the first listed mount point when multiple are found by mount for
    the same partition.

Version 0.29 (2009-03-25)
  * Check if /etc exists, instead of /etc/lsb-release, before getting the distro
    version out of /etc/issue.

Version 0.28 (2009-03-22)
  * Add Wubi detection.

Version 0.27 (2009-02-22)
  * Reorganisation of the partition table function.

Version 0.26 (2009-02-20)
  * Add Fat32 PBR detection.

Version 0.25 (2009-02-15)
  * Add /Windows/System32/winload.exe to the boot programs list.
  * Add some missing partition IDs and their full name.
  * Add Solaris MBR detection.

Version 0.24 (2009-02-01)
  * Display full name of partition ID.

Version 0.23 (2009-01-29)
  * Add HFS+ GUID.
  * Add GAG MBR detection.
  * Add BSD 4.4 Fat32 PBR detection.
  * Display fake hard drives.

Version 0.22 (2009-01-25)
  * Unmount partitions afterwards, when they were not mounted before running
    the script.

Version 0.21 (2009-01-23)
  * GPT support added.
  * BootIt NG partition table support added.
  * Check for overlapping partitions.
  * Check if logical partitions are inside the extended partition.
  * Display the location (on the drive) of files read by Grub.

Version 0.11 (2009-01-12)
  * Adds support for reading the partition table.

Version 0.10 (2009-01-09)
  * Initial release by Ulrich Meierfrankenfeld with help from caljohnsmith.
  * The birth of boot_info_script:
    http://ubuntuforums.org/showthread.php?t=837791[/HTML]

---

### Post by ubu nubu on 2011-06-18
```

```[HTML]&#65279;CHANGELOG:
==========

Version 0.60 (2010-05-17)
  * New maintainer: Gert Hulselmans.
  * boot_info_script is now released under the MIT license.
  * Add this CHANGELOG file.
  * Source code changes are now tracked in git:
      http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=summary
  * Big source code reformatting and cleanup of the code and comments.
  * The output file can now be specified by adding the filename as argument:
      bash ./boot_info_script.sh <outputfile>
  * Display help when invoked with the -h, -help or --help switch.
  * Gzip the output file when invoked with the -g or --gzip switch.
    This option will make 2 files: an uncompressed and gzip compressed file.
  * Warn the user if multiple boot_info_script.sh files are found in the same
    directory (file downloaded multiple times with Firefox, Chromium,... ):
      boot_info_script.sh boot_info_script(0).sh boot_info_script(1).sh
  * Add a lot of GUIDs to the GPT Partition type list.
  * Grub support code is rewritten and now handled by one function.
  * Add Grub2 v1.99 support.
  * Display the embedded Grub2/burg config file.
  * Syslinux support added:
      - Check if Syslinux can find its second stage.
      - Display the version number.
      - Display the Syslinux directory in which Syslinux will look first for
        its config file.
      - Display content of Syslinux config file.
      - Display the ADV.
      - List all COM32(R) module files and display the major version number.
  * Support mount paths with spaces.
  * Support more than 26 drives.
  * Add detection for the following MBRs:
      - Different Syslinux MBRs and versions (standard, GPT and ISOhybrid)
      - Diskcryptor
      - FreeDOS
      - SUSE generic MBR
      - Grub4dos
      - WEE
      - XOSL
  * Add detection for grub4dos installed in the PBR.
  * Add detection for FreeDOS PBR code.
  * List additional boot files when found:
      - SYSLINUX/EXTLINUX: ldlinux.sys and extlinux.sys
      - Grub4dos: grldr and grldr.bin
      - burg (Grub2 based): /burg/core.img and /boot/burg/core.img
      - Grub2: added /boot/grub2/core.img as alternative location
      - FreeDOS: kernel.sys
      - DellDiagnostics: dellbio.bin and dellrmk.bin
      - ReactOS: freeldr.sys qnd freeldr.ini
  * Display offset of file on a disk in GB and GiB for Grub(2) and Syslinux.
  * Display embedded config file for Grub4dos/WEE.
  * Add ReactOS support.
  * Most lines in the output file are now 80 characters or less.
  * Prefer gawk above nawk and busybox awk (workaround for bugs in nawk).
  
Version 0.55 (2010-02-15)
  * Show blkid info for all drives.

Version 0.54 (2010-02-14)
  * Display boot_info_script version and release date when invoked with the
    -v, -V or --version switch.
  * Save boot_info_script version and release date in the RESULTS.TXT file.
  * Workaround for blkid -p, when this parameter isn't supported by blkid.

Version 0.53 (2010-02-12)
  * Use "sfdisk -s" instead of "fdisk -s", when available.

Version 0.52 (2010-02-12)
  * Add /wubildr, /ubuntu/winboot/wubildr, /ubuntu/winboot/wubildr.mbr and
    /ubuntu/disks/home.disk to the boot programs list.
  * Handle output of newer versions of filefrag correctly.

Version 0.51 (2010-02-04)
  * Add io.sys, msdos.sys and command.com to the boot programs list.

Version 0.50 (2010-01-29)
  * If a filesystem is already mounted, use the current mountpoint instead of
    creating a new mountpoint.
  * Search all RAID drives detected by dmraid.

Version 0.49 (2010-01-26)
  * Add initramfs to list of files used by grub.
  * Add Acronis SZ PBR detection.
  * Scan also drives without a partition table, but with a filesystem.
  * Display only the mount output for partitions and drives.

Version 0.48 (2010-01-12)
  * Add "ls -R /dev/mapper" output.

Version 0.47 (2010-01-09)
  * Add a separate list for finding config and boot program files on FAT
    partitions.
  * Add Paragon MBR detection.  

Version 0.46 (2010-01-07)

Version 0.45 (2010-01-07)
  * Check if all needed programs are available before running the rest of the
    script.
  * Detect extended partitions linking to another extended partition.

Version 0.44 (2009-12-31)
  * Add Linux Software Raid (dmraid) support.

Version 0.43 (2009-12-30)
  * Rewrite LVM support code.
  * Rewrite Wubi support code.

Version 0.42 (2009-12-20)
  * Add LVM support.
  * Add GUID for BIOS Boot partition.
  
Version 0.41 (2009-12-08)

Version 0.40 (2009-12-07)
  * Display the directory for which core.img of Grub2 looks for its config file
    and module files.

Version 0.39 (2009-12-05)
  * Add support for getting the Slackware version info.

Version 0.38 (2009-12-05)
  * Add support for differenciating between Windows Vista and Windows 7 as OS
    installed on a certain partition.

Version 0.37 (2009-11-28)
  * Small fix for Grub2 v1.97 support.

Version 0.36 (2009-11-19)
  * Add proper Grub2 v1.97 support.

Version 0.35 (2009-11-15)
  * Save the RESULTS.TXT file in the home dir, when the script is located in
    /bin, /sbin, /usr/bin, or other system folders.

Version 0.34 (2009-11-14)
  * Disable some parts of the Grub2 v1.97 support code, which currently doesn't
    work, due missing parts.

Version 0.33 (2009-11-13)
  * Add Grub2 v1.97 support.
  * Add Syslinux, Truecrypt and Master Boot Loader MBR detection.

Version 0.32 (2009-04-17)
  * Add Acer 3 MBR detection.
  * Fix losetup --sizelimit problem (not supported on older versions of losetup).

Version 0.31 (2009-04-14)
  * Some small changes related to BootIt NG.

Version 0.30 (2009-04-10)
  * Only use the first listed mount point when multiple are found by mount for
    the same partition.

Version 0.29 (2009-03-25)
  * Check if /etc exists, instead of /etc/lsb-release, before getting the distro
    version out of /etc/issue.

Version 0.28 (2009-03-22)
  * Add Wubi detection.

Version 0.27 (2009-02-22)
  * Reorganisation of the partition table function.

Version 0.26 (2009-02-20)
  * Add Fat32 PBR detection.

Version 0.25 (2009-02-15)
  * Add /Windows/System32/winload.exe to the boot programs list.
  * Add some missing partition IDs and their full name.
  * Add Solaris MBR detection.

Version 0.24 (2009-02-01)
  * Display full name of partition ID.

Version 0.23 (2009-01-29)
  * Add HFS+ GUID.
  * Add GAG MBR detection.
  * Add BSD 4.4 Fat32 PBR detection.
  * Display fake hard drives.

Version 0.22 (2009-01-25)
  * Unmount partitions afterwards, when they were not mounted before running
    the script.

Version 0.21 (2009-01-23)
  * GPT support added.
  * BootIt NG partition table support added.
  * Check for overlapping partitions.
  * Check if logical partitions are inside the extended partition.
  * Display the location (on the drive) of files read by Grub.

Version 0.11 (2009-01-12)
  * Adds support for reading the partition table.

Version 0.10 (2009-01-09)
  * Initial release by Ulrich Meierfrankenfeld with help from caljohnsmith.
  * The birth of boot_info_script:
    http://ubuntuforums.org/showthread.php?t=837791[/HTML]

---

### Post by oldfred on 2011-06-18
You posted the changelog from the script's zip. You need to extract boot_info_script.sh and run it per instructions on site to get results.txt.

Then post results.txt's contents in code tags.

---

### Post by ubu nubu on 2011-06-18
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 739bd593-9a10-4438-86ca-460f5f9d1eba root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *        206,848 2,930,272,255 2,930,065,408   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   756,258,815   756,256,768  83 Linux
/dev/sdb2         756,260,862   781,422,591    25,161,730   5 Extended
/dev/sdb5         756,260,864   781,422,591    25,161,728  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        600A54303775F517                       ntfs       
/dev/sdb1        0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63   ext4       
/dev/sdb5        a4231d39-af42-4107-8db7-60c24a255d69   swap       
/dev/sdc1        465E09195E090381                       ntfs       2TB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/sdc1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,umask=000   0  0  
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  28.135013580 = 30.209740800   boot/grub/core.img                             1
   6.230705261 = 6.690168832    boot/grub/grub.cfg                             1
   2.037803650 = 2.188075008    boot/initrd.img-2.6.38-8-generic-pae           2
   0.677185059 = 0.727121920    boot/vmlinuz-2.6.38-8-generic-pae              1
   2.037803650 = 2.188075008    initrd.img                                     2
   0.677185059 = 0.727121920    vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by Quackers on 2011-06-18
Which hard drive is set to boot first in your bios?
Presumably Ubuntu is booting OK? 
Currently grub is installed to /dev/sda and /dev/sdc, which are both of your Windows-based drives.
The drive which I would expect to have grub installed on is /dev/sdb, which is your Ubuntu drive. Sadly this drive has no bootloader installed.

---

### Post by ubu nubu on 2011-06-18
Thanks for the reply,

In Bios
IDE Channel 1 master ST31500   " 1.5TB drive"
IDE Channel 1 Slave ST34000     "400GB Drive"
IDE Channel 3 Master ST2000    "2TB Drive"

in Bios
The first boot disc is set to "hard disc" But doesn't have an option for which hard disc.

On startup, Ubuntu is stopping at a page where it is "mounting" a disc. If I press "s" for skip, Ubuntu will load.
Once Ubuntu loads, I am able to access the 400GB drive and the 2TB drive but not the 1.5 TB drive.

I had Windows 7 on this machine prior to this install and I made the rookie mistake of not reformatting the drives in Windows before I started this Ubuntu install.

I could easily be swayed into reformatting all these drives, and reinstalling Ubuntu if you all think my system is beyond repair at this point.

---

### Post by Quackers on 2011-06-18
Are you using SATA ports or IDE? How old is the motherboard?
Are you getting a grub menu with a choice of which operating system to boot?

I would expect your bios to have the ability to boot the separate hard drives. Maybe there is a function that you have missed? If you highlight the hard drive entry do any options appear? Or if you highlight the hard drive and hit enter do any options appear?

---

### Post by ubu nubu on 2011-06-18
all 3 drives at SATA
gigabyte ga-790xta-ud4 MOBO
There is no menu when I turn it on, it goes straight to that "mounting" screen
In the Bios the drives are all set to auto

---

### Post by Quackers on 2011-06-18
I'm having problems :-)
In your message earlier you say
"In Bios
IDE Channel 1 master ST31500 " 1.5TB drive"
IDE Channel 1 Slave ST34000 "400GB Drive"
IDE Channel 3 Master ST2000 "2TB Drive"

but I wasn't aware that you could have 2 masters on IDE (it's been a while since I used them). Is that what you saw in bios or could it be a mistake?

I'm trying to work out which drive it's trying to boot from. I suspect the error message is from /dev/sdc when it's trying to find 
"search.fs_uuid 739bd593-9a10-4438-86ca-460f5f9d1eba root 
    set 
    prefix=($root)/boot/grub"

but that UUID does not seem to exist on your system.
Have you deleted a partition recently?

---

### Post by ubu nubu on 2011-06-18
I probobly did delete a partition, 

The Mobo is only a year or 2 old.
In Bion under "Standard CMOS Features" It shows
IDE Channel 0 Master  [none]
IDE Channel 0 Slave [none]
IDE Channel 1 Master  [ST31500541as]
IDE Channel 1 Slave [ST3400620ns]
IDE Channel 2 Master  [none]
IDE Channel 2 Slave [ATAPI ihas324 y]
IDE Channel 3 Master  [ST2000dl003-9vt166]
IDE Channel 3 Slave [atapi ihas324 y]
IDE Channel 4 Master  [none]
IDE Channel 5 master [none]

Once I selected hard drive as the first boot device, it allowed me to select the 400GB with Ubuntu as the hard disc boot priority.

---

### Post by Quackers on 2011-06-18
Ok, so you selected that and does Ubuntu still boot?

---

### Post by ubu nubu on 2011-06-18
no,
That solved by boot issue,
Now I just need to figure out how to access the 1.5 TB drive while in Ubuntu.

If I can figure that out and find a solid Itunes alternative, I will love Ubuntu.

---

### Post by YesWeCan on 2011-06-18
There are some inconsistencies here. The 1500GB drive is variously called NTFS, fuseblk and is meant to be FAT32. So I think something is not right.

Ubuntu's boot gets stuck because it is unable to mount the sdc1 partition of the 1500GB drive. That's what you are skipping when you press S. The way it tries to mount it is defined in /etc/fstab and it is currently defined to be an NTFS partition.

So you may want to experiment on the command line to see what format specifier will enable it to be mounted. For example,
[COLOR="Navy"]sudo mount -t vfat /dev/sdc1 /mnt[/COLOR]
which I think may be correct for FAT32.

If you want to stop the boot interruptions while you figure this out, comment out the entry in /etc/fstab that mounts sdc1.

---

### Post by Quackers on 2011-06-18
If you set the 400GB drive to boot first, then Ubuntu shouldn't boot. That is to be expected because there is no bootloader in sdb yet :-)

What do you mean that is solved your boot problem? 
Did you change the bios back to what it was before then boot into Ubuntu again?

---

### Post by ubu nubu on 2011-06-18
I mean it solved my boot problem because Ubuntu boots up without stopping at the ...mounting screen that I was having to press "s"-skip to get past.

I'm really scared that I'm going to make things worse if I start adjusting things on the command line. Should I enter the example on my command line?

---

### Post by Quackers on 2011-06-18
Now I'm even more confused :-)
When you changed the boot order in bios nothing booted, is that correct?
So now you've changed the bios back and it boots Ubuntu without the error message. Is that correct?

On a different note, you say that the third hard drive is FAT32 but the boot script output says it is NTFS and so does /etc/fstab file. 
Could you have made a mistake there?

Finally, there doesn't appear to be any Windows boot files at all on your system! That's not good, as far as Windows is concerned.

---

### Post by YesWeCan on 2011-06-18
The mount command won't do any harm.

I am curious as to why you didn't have to press 'S' this time. Did it mount the 1.5TB drive ok this time?

Can you see an icon for the 1.5TB dirve in Places/Computer?

---

### Post by ubu nubu on 2011-06-18
I mean't the example from YesWeCan
"So you may want to experiment on the command line to see what format specifier will enable it to be mounted. For example,
sudo mount -t vfat /dev/sdc1 /mnt
which I think may be correct for FAT32."

I tried it in my terminal and this is what happened

mount: /dev/sdc1 already mounted or /mnt busy
mount: according to mtab, /dev/sdc1 is mounted on /media/sdc1
ubu@ubu-GA-790XTA-UD4:~$

---

### Post by YesWeCan on 2011-06-18
Ok, so it is already mounted.
What is the problem, exactly?

Oh, sorry. I am getting confused too!
It is sda2 that you wish to have mounted, not sdc1. sda is the 1.5TB disk.

Ok, the problem is that you do not have an entry in fstab to mount sda2.
You can mount it from the command line as a test:

make a mount point:
sudo mkdir /media/sda2
sudo mount -t ntfs /dev/sda2 /media/sda2

You need to edit /etc/fstab and copy the line for /dev/sdc1 and change it to /dev/sda1 and change the mount point from /media/sdc1 to /media/sda2

---

### Post by ubu nubu on 2011-06-18
Yes,
I just did a restart and it fired right up, no s screen

My only problem is I cannot access the 1.5 TB Drive.

The 2TB drive is accessible, but not the 1.5 TB Drive.

---

### Post by YesWeCan on 2011-06-18
> **Quackers said:**
> Finally, there doesn't appear to be any Windows boot files at all on your system! That's not good, as far as Windows is concerned.
Indeed. Where is the missing sda1 partition?

---

### Post by ubu nubu on 2011-06-18
I tried this in the terminal, and here was my result.

ubu@ubu-GA-790XTA-UD4:~$ sudo mount -t vfat /dev/sda1 /mnt
mount: special device /dev/sda1 does not exist

---

### Post by YesWeCan on 2011-06-18
sda2 not sda1, and ntfs not vfat

Do this. Make a directory in /media for it. This way when you mount it you will get an icon on your desktop.

[COLOR="Navy"]sudo mkdir /media/sda2[/COLOR]  (you can call it anything you like, /media/Windows if you prefer)
[COLOR="Navy"]sudo mount -t ntfs /dev/sda2 /media/sda2[/COLOR]

---

### Post by ubu nubu on 2011-06-18
ubu@ubu-GA-790XTA-UD4:~$ sudo mount -t vfat /dev/sda2 /mnt
mount: /dev/sda2 already mounted or /mnt busy
mount: according to mtab, /dev/sda2 is already mounted on /mnt

---

### Post by Quackers on 2011-06-18
As YesWeCan says, you don't have an sda1 :-)
Could that be the partition you deleted? It may have been 100MB to 200MB in size. Sadly it is likely to have held your Windows boot files in it (or 2 of them anyway).

---

### Post by ubu nubu on 2011-06-18
I bet I did delete that partition.
I'm not planning on installing Windows on this PC anytime soon. 

Can the 1.5TB drive be accessed or do I need to reformat it?

---

### Post by YesWeCan on 2011-06-18
Ok. Somehow you have mounted sda2 at /mnt.
You can browse it there in your Places menu.

But /mnt is just a temporary place.
So unmount it and create a directory in /media and remount it. Then you will see a handy icon on your desktop

sudo umount /mnt
sudo mkdir /media/sda2
sudo mount -t ntfs /dev/sda2 /media/sda2


I think you're getting the hang of it.

---

### Post by ubu nubu on 2011-06-18
That did it,
All is well
Thanks for your patience.

---

### Post by YesWeCan on 2011-06-18
Good.
Remember that until you add an entry to /etc/fstab the sda2 partition will not be mounted automatically when you reboot.
So you will need to run this command again
[COLOR="DarkSlateBlue"]sudo mount -t ntfs /dev/sda2 /media/sda2[/COLOR]

---

### Post by ubu nubu on 2011-06-18
yep,
I messed up and tried a restart. it locked  up on a screen saying,
"checking for running unintended upgrades"

I unplugged it and restarted it and you were correct, the 1.5 is not accessible again.

What do I need to do to get it to stay accesible after I restart it again?

---

### Post by ubu nubu on 2011-06-18
yep,
I messed up and tried a restart. it locked  up on a screen saying,
"checking for running unintended upgrades"

I unplugged it and restarted it and you were correct, the 1.5 is not accessible again.

What do I need to do to get it to stay accesible after I restart it again?

---

### Post by ubu nubu on 2011-06-19
How do I get the 1.5 TB Drive to stay mounted on a restart?

---

### Post by YesWeCan on 2011-06-19
You need to edit /etc/fstab and make it look like this. You can copy and paste this if you wish.

BE VERY CAREFUL not to make a mistake or you machine may not boot. Make a backup copy of fstab first.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                             <mount point>   <type>  <options>               <dump>  <pass>

proc                                         /proc           proc   nodev,noexec,nosuid        0      0  

# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63    /               ext4   errors=remount-ro          0      1  

# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69    none            swap   sw                         0      0  

/dev/fd0                                     /media/floppy0  auto   rw,user,noauto,exec,utf8   0      0

# Windows NTFS sdc1 
UUID=465E09195E090381                        /media/sdc1     ntfs   nls=iso8859-1,umask=000    0      0 

# Windows NTFS sda2
UUID=600A54303775F517                        /media/sda2     ntfs   nls=iso8859-1,umask=000    0      0 
```

Also, Your Grub boot-loader ought to be installed to the disk that has Ubuntu on it, sdb. At the moment, it is installed to both sda and sdc, which was causing some confusion yesterday.

So once you have got the fstab working, why not run these commands:
sudo update-grub
sudo grub-install /dev/sdb

Then try booting sdb directly with the bios and check it boots ok. This will mean you can remove/reformat sda or sdc without breaking your Grub.

---

### Post by ubu nubu on 2011-06-20
It sounds like I might be better off reformatting all these drives and starting from scratch. 

What do you think of that idea?

---

### Post by YesWeCan on 2011-06-21
Up to you. I see nothing wrong with sdb once you've installed Grub to its MBR.

---

### Post by ubu nubu on 2011-06-21
I backed everything up,and I tried your code. Starting with

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                             <mount point>   <type>  <options>               <dump>  <pass>

proc                                         /proc           proc   nodev,noexec,nosuid        0      0  

# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63    /               ext4   errors=remount-ro          0      1  

# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69    none            swap   sw                         0      0  

/dev/fd0                                     /media/floppy0  auto   rw,user,noauto,exec,utf8   0      0

# Windows NTFS sdc1 
UUID=465E09195E090381                        /media/sdc1     ntfs   nls=iso8859-1,umask=000    0      0 

# Windows NTFS sda2
UUID=600A54303775F517                        /media/sda2     ntfs   nls=iso8859-1,umask=000    0      0

Then,
I added the 1.5TB with

sudo mount -t ntfs /dev/sda2 /media/sda2

Then,
I did the last one,
sudo update-grub
sudo grub-install /dev/sdb

Then,
I tried a restart, and it froze.

I unplugged it and restarted it,
it restarted, but no drives(2tb,1.5tb) were available

Did I do something wrong with the code?
Will you please help me enter the correct code to fix it?

---

### Post by YesWeCan on 2011-06-21
Oh. I must have made a mistake. The fstab file looks ok.

Would you do this?
Reboot (and tell the bios to boot the sdb drive)
note any error messages during boot
In a terminal type
[COLOR="Navy"]sudo mount -a[/COLOR]
and post any error messages (this executes the fstab instructions again)
also please post the output of
[COLOR="Navy"]sudo blkid[/COLOR]

It makes it easier to read if you post things between ```

``` tags (you can highlight the text and click the #)

---

### Post by ubu nubu on 2011-06-21
When I started it up this time it loaded right up, no errors.
The 2TB HD was accesable, but not the 1.5 TB.

I tried the 2 codes you recommended
```
sudo mount -a
```
that one didn't do anything

the second one
```
sudo blkid
```
produced this output

```
/dev/sda2: UUID="600A54303775F517" TYPE="ntfs" 
/dev/sdb1: UUID="0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63" TYPE="ext4" 
/dev/sdb5: UUID="a4231d39-af42-4107-8db7-60c24a255d69" TYPE="swap" 
/dev/sdc1: LABEL="2TB" UUID="465E09195E090381" TYPE="ntfs" 
ubu@ubu-GA-790XTA-UD4:~$ 

```

thanks for sticking with me on this

---

### Post by YesWeCan on 2011-06-21
What's the output of
[COLOR="Navy"]mount[/COLOR]

[edit]
Oh I know what it may be. Did you make a directory under /media for it?
You should have two mount directories:
/media/sdc1
/media/sda2

You may not have the second one. If not, do
[COLOR="Navy"]sudo mkdir /media/sda2
sudo chmod a+rw /media/sda2[/COLOR]

Then do
[COLOR="Navy"]sudo mount -a[/COLOR]

---

### Post by ubu nubu on 2011-06-21
```
ubu@ubu-GA-790XTA-UD4:~$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubu)
ubu@ubu-GA-790XTA-UD4:~$ 
```

---

### Post by ubu nubu on 2011-06-21
```
ubu@ubu-GA-790XTA-UD4:~$ /media/sdc1
bash: /media/sdc1: Is a directory
ubu@ubu-GA-790XTA-UD4:~$ /media/sda2
bash: /media/sda2: Is a directory
ubu@ubu-GA-790XTA-UD4:~$ sudo mkdir /media/sda2
[sudo] password for ubu: 
Sorry, try again.
[sudo] password for ubu: 
mkdir: cannot create directory `/media/sda2': File exists
ubu@ubu-GA-790XTA-UD4:~$ sudo mount -a
ubu@ubu-GA-790XTA-UD4:~$ 


```

---

### Post by YesWeCan on 2011-06-21
Hmm. Would you post
[COLOR="Navy"]sudo mount -av[/COLOR]
(I forgot the v last time, it is verbose mode)

And
[COLOR="Navy"]ls -al /media[/COLOR]

And
[COLOR="Navy"]sudo fdisk -l[/COLOR]

---

### Post by ubu nubu on 2011-06-21
```
ubu@ubu-GA-790XTA-UD4:~$ sudo mount -av
[sudo] password for ubu: 
mount: proc already mounted on /proc
mount: /dev/sdc1 already mounted on /media/sdc1
nothing was mounted
ubu@ubu-GA-790XTA-UD4:~$ ls -al /media
total 32
drwxr-xr-x  5 root root  4096 2011-06-21 10:50 .
drwxr-xr-x 22 root root  4096 2011-06-08 19:46 ..
lrwxrwxrwx  1 root root     7 2011-06-08 19:35 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2011-06-08 19:35 floppy0
drwxr-xr-x  2 root root  4096 2011-06-18 19:13 sda2
drwxrwxrwx  1 root root 16384 2011-06-20 15:54 sdc1
ubu@ubu-GA-790XTA-UD4:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
240 heads, 63 sectors/track, 193801 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6dd4abb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          14      193802  1465032704    7  HPFS/NTFS

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a118

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       47075   378128384   83  Linux
/dev/sdb2           47076       48642    12580865    5  Extended
/dev/sdb5           47076       48642    12580864   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x006fb616

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      243202  1953512448    7  HPFS/NTFS
ubu@ubu-GA-790XTA-UD4:~$ 

```

---

### Post by YesWeCan on 2011-06-21
Everything looks good except for the output of mount -av which makes no mention of sda2. There must be something wrong in the /etc/fstab file.

Would you post the output of
[COLOR="Navy"]cat /etc/fstab[/COLOR]
In code tags this time. Thx.

---

### Post by ubu nubu on 2011-06-21
```
ubu@ubu-GA-790XTA-UD4:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,umask=000   0  0  
ubu@ubu-GA-790XTA-UD4:~$ 


```

---

### Post by YesWeCan on 2011-06-21
That is your old fstab. ;)

Where is the one from post #41?

You need to copy it somewhere as a backup,
[COLOR="Navy"]sudo cp /etc/fstab /etc/fstab-backup[/COLOR]

Then you need to edit it to put in the new content
[COLOR="Navy"]sudo gedit /etc/fstab[/COLOR]

---

### Post by ubu nubu on 2011-06-21
```
ubu@ubu-GA-790XTA-UD4:~$ sudo cp /etc/fstab /etc/fstab-backup
[sudo] password for ubu: 
ubu@ubu-GA-790XTA-UD4:~$ sudo gedit /etc/fstab

(gedit:2821): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.XWKGXV': No such file or directory

(gedit:2821): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc1                                  /media/sdc1     ntfs  nls=iso8859-1,umask=000   0  0  
```

---

### Post by YesWeCan on 2011-06-21
Talk to me. What is the problem?

---

### Post by ubu nubu on 2011-06-21
The computer starts up, but the 1.5 TB drive is not accessible.

If I run the code that makes the 1.5 TB Drive accessible
```
sudo mount -t ntfs /dev/sda2 /media/sda2
```
 That codes makes Both drives accessible, 

When I restart the computer the 1.5 Drive is still not accessible.

My main problem is, 

How to get the 1.5TB drive to stay accessible on restarts.

---

### Post by oldfred on 2011-06-21
You have to have entries for both in your fstab and you have only one now. You did have two before what happened to that one?

Go back to your post #41 and copy the second entry into fstab. You need to unmount your manual mount before adding the entry to fstab.

You should use gksudo for graphical applications.

gksudo gedit /etc/fstab

After any changes to fstab rerun the mount to see if any errrors appear. You need to fix before rebooting if you have errors.

sudo mount -a

If no errors then it just returns.

I think YesWeCan has given you all the necessary instrutions. Basically you have to create a mount point, then mount it to that mount point, and you have to do it for every partition that you want to mount.

---

### Post by YesWeCan on 2011-06-22
It seems like you are having trouble using gedit. Have you used it before?

Here's another way to do it:
Open a terminal window and type [COLOR="Blue"]cd ~[/COLOR]
At the top of the terminal's window click on the Terminal menu and click on 132x43 to make the window bigger.
Copy all the text inside the code area below and then paste it to the terminal window, and press 'return'
This should create a new file called newfstab.
Run [COLOR="Blue"]cat newfstab[/COLOR] to view it and check it looks just like the code below (that is, the text inside the quotation marks " ").
If it is the same do [COLOR="Blue"]sudo cp newfstab /etc/fstab[/COLOR]

Now run [COLOR="Blue"]sudo mount -av[/COLOR] and post the output

```
echo "# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>                             <mount point>   <type>  <options>               <dump>  <pass>

proc                                         /proc           proc   nodev,noexec,nosuid        0      0  

# / was on /dev/sdb1 during installation
UUID=0d4e0ec0-3c5c-4f14-9a77-77cafccd0f63    /               ext4   errors=remount-ro          0      1  

# swap was on /dev/sdb5 during installation
UUID=a4231d39-af42-4107-8db7-60c24a255d69    none            swap   sw                         0      0  

/dev/fd0                                     /media/floppy0  auto   rw,user,noauto,exec,utf8   0      0

# Windows NTFS sdc1 
UUID=465E09195E090381                        /media/sdc1     ntfs   nls=iso8859-1,umask=000    0      0 

# Windows NTFS sda2
UUID=600A54303775F517                        /media/sda2     ntfs   nls=iso8859-1,umask=000    0      0" > newfstab
```

---

