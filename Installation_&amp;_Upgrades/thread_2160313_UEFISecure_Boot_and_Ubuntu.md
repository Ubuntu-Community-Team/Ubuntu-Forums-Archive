---
title: "UEFI/Secure Boot and Ubuntu"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by Uncle Spellbinder on 2013-07-06
So. I've tried to install Ubuntu (and other distros) on this computer to no avail. 

My computer specs can be found here: [http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03524666&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5295897&prodTypeId=12454](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03524666&lang=en&cc=us&taskId=135&contentType=SupportFAQ&prodSeriesId=5295897&prodTypeId=12454) 

Considering I'm having a ridiculous time installing any Linux OS on this UEFI computer, I was wondering what your thoughts might be on this link: [http://community.linuxmint.com/tutorial/view/858](http://community.linuxmint.com/tutorial/view/858). Geared towards the Linux Mint community, it seems a good fit for any distro. As I would be ditching Windows 8 completely in favor of a 100% Linux box, you think this might do the trick?

---

### Post by fantab on 2013-07-06
Can you tell us more about... why you can't install Ubuntu? what happens when you try to install Ubuntu? Are any Errors reported?

---

### Post by Uncle Spellbinder on 2013-07-06
I get "No OS Found" or something like that. Fast boot was disabled in Windows 8 before attempting installation of Ubuntu. This happens with ALL distros I've tried. 

Still, I'm curious if it's a good thing to convert my harddrive from GPT partition table to MBR partition table (or MSDOS in Linux).

From the link above:
*"Use a distro of your choice in live mode. Find the program GPARTED. Wait until it recognizes all your drives and select your HDD. Right click over it, and choose the option to create a new partition table. Choose MSDOS from the list. Hit ok than apply/commit all changes. ATTENTION this will erase all your data and MS Windows (or any other OS) will disappear. Your HDD is now converted in MSDOS or MBR. You can now boot your preferred distro, create your partition scheme and install Linux."*

---

### Post by Uncle Spellbinder on 2013-07-06
I obviously don't want to try the scenario I posted above unless/until I can get verification that it won't "brick" my computer. 

But, in the BIOS/UEFI settings, I can completely disable Secure Boot and enable Legacy settings. In the Windows 8 power settings, Fast Boot is already disabled. Will this be enough to install Ubuntu and wipe Windows from the drive leaving me a 100% Ubuntu box?

---

### Post by TNFrank on 2013-07-06
I also had a new Windows 8 computer with that stupid UEFI deal and tried a few times to install Linux on it to no avail. Ended up taking the computer back for a full refund and used the money to buy two older non-UEFI computers which I installed Ubuntu on without a hitch.  Sometimes newer isn't necessarily better.

---

### Post by Uncle Spellbinder on 2013-07-06
So, through the BIOS settings, I disabled secure boot, disabled uefi settings, enabled legacy settings and disabled fast boot. Ubuntu 13.04 installed as I remember on previous machines. I chose the "replace windows 8" option. All seems well so far.

---

### Post by fantab on 2013-07-06
If 'replace Windows8' was your goal, Then I am glad you've got it.

FYI, Ubuntu since version 12.04.2 can boot with 'Secure Boot' enabled in UEFI mode with GPT. 
Windows8 has this '[***Fast Startup***]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' feature which won't let the PC 'Shutdown' and keeps it in Hibernation for fast startups. Since PC won't shutdown properly it won't allow any OS to install. This feature needs to be turned off if we want to dual-boot. 'Fast Boot' is a different feature.

[GUID Partition Table]("https://wiki.archlinux.org/index.php/GPT") is both superior and advantageous than 'msdos' partition table. You can search the www to know more. Installing Ubuntu on GPT is recommended. Its the future.

Since you've just installed Ubuntu, I'd suggest you re-install it in UEFI mode with GPT.

My two cents....

---

### Post by Uncle Spellbinder on 2013-07-07
It's a bit confusing. For example, Though Windows 8 is not on this computer any longer, If I enter UEFI settings, there is still a "Windows bootloader" under UEFI settings. How is this possible If I've removed Windows 8?

Is there a good tutorial on how to install Ubuntu alone (no dual-boot) in UEFI mode?

---

### Post by Uncle Spellbinder on 2013-07-07
So, I returned all settings in UEFI to their original state. Tried to install Ubuntu in UEFI mode to no avail. I created a 50mb EFI boot partition as described in several different tutorials. No go.

I still find it odd that an entry for Windows Bootloader is in the UEFI settings when there is no Windows OS on the computer. 

Any guidance appreciated

---

### Post by fantab on 2013-07-08
50 MB is too small make it **300mb FAT32** Partition.

> Though Windows 8 is not on this computer any longer, If I enter UEFI  settings, there is still a "Windows bootloader" under UEFI settings. How  is this possible If I've removed Windows 8?


That is because UEFI booting store some entires in the BIOS. These can be managed/removed later using [efibootmgr]("http://manpages.ubuntu.com/manpages/gutsy/man8/efibootmgr.8.html")...

Boot with Ubuntu LiveDVD/USB and post the output of:

```
sudo parted -l
```

---

### Post by Uncle Spellbinder on 2013-07-08
At work at the moment. I've since gone back to no uefi so I have something on the computer. since this computer has basically turned into my uefi test machine, I'll reinstall Ubuntu in UEFI mode with a 300mb efi boot partition. I'll post back the results this evening.

Truly appreciate the help!

---

### Post by Uncle Spellbinder on 2013-07-08
Should everything be re-enabled? UEFI, Secure Boot, Fast Boot then disable Legacy settings?

---

### Post by deadflowr on 2013-07-08
Have you looked over oldfred's [UEFI Installing -Tips]("http://ubuntuforums.org/showthread.php?t=2147295") thread?

---

### Post by fantab on 2013-07-08
Yes, just keep 'fast boot' and 'Secure boot' disabled. Secure boot is a Microsoft thing.

---

### Post by Uncle Spellbinder on 2013-07-08
@ fantab - Altighty. So all I need to do is enable UEFI and keep fast boot, secure boot and legacy disabled. I'll give it a shot after work.

@ deadflowr - Appreciate the link. I'll have a look after work.

---

### Post by Uncle Spellbinder on 2013-07-08
I'm in live DVD mode at the moment. Tried installing 64bit Ubuntu 13.04 in UEFI mode - No luck. Still says "no boot device found."

Tried ***Boot Repair*** DVD I burned (64 bit) and got an error message as follows:
```
error 0100 reading sector 255186

boot:
could not find kernel image: gfxboot
```

Here is a screenshot of the install screen just before I installed:

[[IMG]http://is100.imagesocket.com/images/2013/07/08/2632517-0cug.png[/IMG]](http://www.imagesocket.com/photos/guest/2632517)

Here is the output of **sudo parted -l**

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  302MB  301MB   fat32           EFI System Partition  boot
 2      302MB   498GB  498GB   ext4
 3      498GB   500GB  2049MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 

```

---

### Post by Uncle Spellbinder on 2013-07-08
AHhhhhh. Installed Boot Repair in the Live DVD session and ran it from within the live DVD session. It worked!

Here's the current output from ***sudo parted -l***

```
unclespellbinder@wombat64:~$ sudo parted -l
[sudo] password for unclespellbinder: 
Model: ATA WDC WD5000AAKX-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  302MB  301MB   fat32           EFI System Partition  boot
 2      302MB   498GB  498GB   ext4
 3      498GB   500GB  2049MB  linux-swap(v1)

unclespellbinder@wombat64:~$ 
```


Here's the report generated by Boot Repair after the repairs were made:

```

============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       589,823       587,776 EFI System partition
/dev/sda2         589,824   972,769,279   972,179,456 Data partition (Windows/Linux)
/dev/sda3     972,769,280   976,771,071     4,001,792 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5794-2BEF                              vfat       
/dev/sda2        696c06a1-845d-4bed-909a-b546130928ee   ext4       
/dev/sda3        3c3bbcb3-e5d2-4a31-989f-054f42e76283   swap       
/dev/sr0                                                iso9660    Ubuntu 13.04 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  696c06a1-845d-4bed-909a-b546130928ee
else
  search --no-floppy --fs-uuid --set=root 696c06a1-845d-4bed-909a-b546130928ee
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-696c06a1-845d-4bed-909a-b546130928ee' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  696c06a1-845d-4bed-909a-b546130928ee
	else
	  search --no-floppy --fs-uuid --set=root 696c06a1-845d-4bed-909a-b546130928ee
	fi
	linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=696c06a1-845d-4bed-909a-b546130928ee ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-19-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-696c06a1-845d-4bed-909a-b546130928ee' {
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-696c06a1-845d-4bed-909a-b546130928ee' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  696c06a1-845d-4bed-909a-b546130928ee
		else
		  search --no-floppy --fs-uuid --set=root 696c06a1-845d-4bed-909a-b546130928ee
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=696c06a1-845d-4bed-909a-b546130928ee ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-696c06a1-845d-4bed-909a-b546130928ee' {
	recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  696c06a1-845d-4bed-909a-b546130928ee
		else
		  search --no-floppy --fs-uuid --set=root 696c06a1-845d-4bed-909a-b546130928ee
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=696c06a1-845d-4bed-909a-b546130928ee ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=696c06a1-845d-4bed-909a-b546130928ee /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=5794-2BEF  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=3c3bbcb3-e5d2-4a31-989f-054f42e76283 none            swap    sw              0       0
UUID=5794-2BEF	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.422660828 = 9.043763200    boot/grub/grub.cfg                             1
   1.087020874 = 1.167179776    boot/vmlinuz-3.8.0-19-generic                  2
   1.087020874 = 1.167179776    vmlinuz                                        2
   1.897861481 = 2.037813248    boot/initrd.img-3.8.0-19-generic               1
   1.897861481 = 2.037813248    initrd.img                                     1

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/11774/mounts) leaked on lvscan invocation. Parent PID 20287: bash
File descriptor 14 (/usr/share/icons/ubuntu-mono-dark/places/16/user-home.svg) leaked on lvscan invocation. Parent PID 20287: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-07-08__23h17 ===================
boot-repair version : 3.199~ppa6~raring
boot-sav version : 3.199~ppa6~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa6~raring
boot-repair is executed in live-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 13.04 (13.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="5794-2BEF" TYPE="vfat"
/dev/sda2: UUID="696c06a1-845d-4bed-909a-b546130928ee" TYPE="ext4"
/dev/sda3: UUID="3c3bbcb3-e5d2-4a31-989f-054f42e76283" TYPE="swap"
/dev/sr0: LABEL="Ubuntu 13.04 amd64" TYPE="iso9660"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== sda2/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda2/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 24 17:05 grub.d
total 72
-rwxr-xr-x 1 root root  7541 Apr  9 09:29 00_header
-rwxr-xr-x 1 root root  5974 Apr  9 08:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9 09:29 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9 09:29 20_linux_xen
-rwxr-xr-x 1 root root  1688 Dec  5  2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 Apr  9 09:29 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9 09:29 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9 09:29 40_custom
-rwxr-xr-x 1 root root   216 Apr  9 09:29 41_custom
-rw-r--r-- 1 root root   483 Apr  9 09:29 README


/boot/efi detected in the fstab of sda2: UUID=5794-2BEF   (sda1)
efibootmgr -v
gui-g2slaunch.sh: line 127: efibootmgr: command not found
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda2.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD5000AAKX-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  302MB  301MB   fat32           EFI System Partition  boot
2      302MB   498GB  498GB   ext4
3      498GB   500GB  2049MB  linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:gpt:ATA WDC WD5000AAKX-6;
1:1049kB:302MB:301MB:fat32:EFI System Partition:boot;
2:302MB:498GB:498GB:ext4::;
3:498GB:500GB:2049MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: Can't have a partition outside the disk!


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1: /*/*/*/*

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 f8 08 00 40 02 00 00  00 00 00 00 02 00 00 00  |....@...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ef 2b 94 57 20  20 20 20 20 20 20 20 20  |..).+.W         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.8G  108M  2.7G   4% /
udev           devtmpfs   2.7G   12K  2.7G   1% /dev
tmpfs          tmpfs      555M  832K  554M   1% /run
/dev/sr0       iso9660    785M  785M     0 100% /cdrom
/dev/loop0     squashfs   738M  738M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      2.8G  1.1M  2.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.8G   80K  2.8G   1% /run/shm
none           tmpfs      100M   36K  100M   1% /run/user
/dev/sda1      vfat       287M  132K  287M   1% /mnt/boot-sav/sda1
/dev/sda2      ext4       457G  3.1G  430G   1% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT


EFI detected. Please check the options.
Partition outside the disk detected.

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub-efi of sda2, using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    backup-and-rename-efi-files


/boot/efi added in sda2/fstab
Mount sda1 on /mnt/boot-sav/sda2/boot/efi
ls /mnt/boot-sav/sda2/boot/efi: /*/*/*/*
Unhide GRUB boot menu in sda2/etc/default/grub
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.

chroot /mnt/boot-sav/sda2 efibootmgr -v
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0012,0021,001A,000A,0003,0004,0011,0019,0009,0002,0010,0018,0000,0001,0013,0017,001F,000F,0006,0020,0014,001C,000C,0005
Boot0000* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0001* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0003* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0004* Windows Boot Manager	HD(2,200000,b4000,1ad47b94-1931-48dd-b9fe-c49d53bf3ae6)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0006  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0009* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot000A* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot000C  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot000F  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0010* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0011* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0012* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0013* CD/DVD Drive 	BIOS(3,0,00)AMGOAMNO........o.h.p. . . . . . .D.V.D. .A. . .D.S.8.A.8.S.H....................A...........................>..Gd-.;.A..MQ..L.9.6.2.7.8.3.4.0.8.4.1.7. . . . . . . . ......AMBO
Boot0014* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0017* Hard Drive	BIOS(2,0,00)AMGOAMNO........o.W.D.C. .W.D.5.0.0.0.A.A.K.X.-.6.0.3.C.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.Y.A.X.U.5.4.4.0.4.3......AMBO
Boot0018* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0019* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot001A* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot001C  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot001F  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0020* Realtek PXE B03 D00	BIOS(6,0,00)AMBO
Boot0021* UEFI: hp      DVD A  DS8A8SH	ACPI(a0341d0,0)PCI(11,0)03120a000200ffff0000CD-ROM(1,6168c,11c0)AMBO

Reinstall the grub-efi of sda2
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi : exit code of grub-install :0
(debug) beglsefi1 ubuntu/grubx64.efi ; ubuntu , /mnt/boot-sav/sda2/boot/efi .
ls /mnt/boot-sav/sda2/boot/efi: /*/*/*/*
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi (& .grb)
ls /mnt/boot-sav/sda2/boot/efi:
Add /mnt/boot-sav/sda2/boot/efi efi entries in /mnt/boot-sav/sda2/etc/grub.d/25_custom

chroot /mnt/boot-sav/sda2 efibootmgr -v
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0012,0021,001A,000A,0003,0004,0011,0019,0009,0002,0010,0018,0000,0001,0013,0017,001F,000F,0006,0020,0014,001C,000C,0005
Boot0000* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0001* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0003* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0004* Windows Boot Manager	HD(2,200000,b4000,1ad47b94-1931-48dd-b9fe-c49d53bf3ae6)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0005  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0006  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0009* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot000A* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot000C  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot000F  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0010* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0011* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0012* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0013* CD/DVD Drive 	BIOS(3,0,00)AMGOAMNO........o.h.p. . . . . . .D.V.D. .A. . .D.S.8.A.8.S.H....................A...........................>..Gd-.;.A..MQ..L.9.6.2.7.8.3.4.0.8.4.1.7. . . . . . . . ......AMBO
Boot0014* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0017* Hard Drive	BIOS(2,0,00)AMGOAMNO........o.W.D.C. .W.D.5.0.0.0.A.A.K.X.-.6.0.3.C.A.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.Y.A.X.U.5.4.4.0.4.3......AMBO
Boot0018* USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0019* USB Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot001A* ATAPI CD-ROM Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot001C  USB Floppy/CD	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot001F  Hard Drive	Vendor(b6fef66f-1495-4584-a836-3492d1984a8d,0200000000)AMBO
Boot0020* Realtek PXE B03 D00	BIOS(6,0,00)AMBO
Boot0021* UEFI: hp      DVD A  DS8A8SH	ACPI(a0341d0,0)PCI(11,0)03120a000200ffff0000CD-ROM(1,6168c,11c0)AMBO

chroot /mnt/boot-sav/sda2 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by oldfred on 2013-07-08
When you say it works it that just Boot-Repair or your entire system?

You still show Windows .efi files in your efi partition. Probably when Ubuntu installed it did not erase those even though the Windows partitions were deleted. If you backed up Windows you may want to back up the Windows files in the efi partition and then delete them.
But UEFI is also smart and saves its own data, so you have still have Windows entries in UEFI also. You have to delete those from your UEFI or with low level 'EFI shell environment' which now is part of many UEFI installs or can be installed.

---

### Post by Uncle Spellbinder on 2013-07-08
The entire system is working. No issues booting into Ubuntu. I overwrote Windows. I have no interest in keeping/using Windows. Any specific advice on how would I go about deleting any Windows files/remnants/entries?


Ahhhh. Just looking at the links in your signature...........

---

### Post by Uncle Spellbinder on 2013-07-08
Nothing in UEFI Boot Manager regarding Windows. But LOTS of entries:

```
unclespellbinder@wombat64:~$ sudo efibootmgr
[sudo] password for unclespellbinder: 
BootCurrent: 0021
Timeout: 2 seconds
BootOrder: 0012,001A,000A,0003,0004,0011,0019,0009,0002,0010,0018,0000,0001,0021,0013,0017,001F,000F,0006,0020,0014,001C,000C,0005
Boot0000* USB Floppy/CD
Boot0001* USB Floppy/CD
Boot0002* USB Hard Drive
Boot0003* ATAPI CD-ROM Drive
Boot0005  USB Floppy/CD
Boot0006  Hard Drive
Boot0009* USB Hard Drive
Boot000A* ATAPI CD-ROM Drive
Boot000C  USB Floppy/CD
Boot000F  Hard Drive
Boot0010* USB Floppy/CD
Boot0011* USB Hard Drive
Boot0012* ATAPI CD-ROM Drive
Boot0013* CD/DVD Drive 
Boot0014* USB Floppy/CD
Boot0017* Hard Drive
Boot0018* USB Floppy/CD
Boot0019* USB Hard Drive
Boot001A* ATAPI CD-ROM Drive
Boot001C  USB Floppy/CD
Boot001F  Hard Drive
Boot0020* Realtek PXE B03 D00
Boot0021* UEFI: WDC WD5000AAKX-603CA0
unclespellbinder@wombat64:~$ 
```

---

### Post by fantab on 2013-07-08
Not really sure how to go about removing Windows entries but got a word about your 498GB '/' partition. Having only one partition that big for '/' is NOT a good idea. It is good for now but in future you should seriously consider splitting that partition into two.

30GB for '/' is plenty. '/' partition stores your System-files and application files.
30GB FREE in case you want to try another distro or another version or flavor of Ubuntu.
All the remaing GB '/home'. /home partition stores your DATA like music, documents etc. so having it separate is a GOOD idea. It will also be very helpful when reinstalling Ubuntu as you can easily format '/' partition clean and install new ubuntu, without worrying too much about loosing data.

Personally, I use a simple Linux, ext4, partition to store my DATA. I don't use /home. My '/' partition is 30GB. A simple DATA partition is excellent for me since I boot multiple Distros and I don't want to share my dotfolder/files (applications data/settings/preferences) between distros.

-- my two cents.

I am glad you got your dual-boot going.

---

### Post by oldfred on 2013-07-08
I do the same as fantab with data partitions, partly because I also have multiple installs. I usually keep old install and put new one in another partition but want the same data in both and maybe be able to boot both with same data and not have any issues of a shared /home.

You should just be able to go into your efi partition and delete the entire Microsoft folder. Boot-Repair may have seen those entries and added them to 25_custom. You can just delete those boot stanza's from 25_custom. See info on housecleaning entries for info on editing 25_custom if desired. Or ask for more info if help still needed.

---

### Post by Uncle Spellbinder on 2013-07-09
Thanks for the info, guys. Until now, a I rarely partitioned manually (unless it was a distro like Manjaro which basically required it via the cli installer). With distros like Ubuntu, I always used the "install alongside" or "replace" options and leg the installer do the work. And fantab - just to clarify, this is a standalone I stall. No dual boot.

So far so good with everything. If I have any further questions, I'll start a new thread or ask in oldfred's thread.

Thanks again, guys.

---

### Post by odysseusjak on 2013-07-16
Uncle Spellbinder,

I have a buddy with the exact same rig. I can install 13.04, but when it reboots, I get a black and white GRUB screen asking if I want to try Ubuntu or install it, etc. I created a 200MB UEFI partition, a 2MB BIOS partion, and then set up manual Ubuntu partition's like I normally do. Mind you, this was *after *doing just a "replace Windows" option, and then a regular manual partition install, then found that I "needed" to have the other two partitions.

What is it I'm missing? Could you detail the steps you took to get Ubuntu installed and running properly?

Thanks for the help!

---

