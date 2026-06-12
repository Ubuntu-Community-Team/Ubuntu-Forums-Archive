---
title: "Invalid EFI File Path"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by Fajner1 on 2012-01-04
Hardware: Intel Core i5-2500K, ASUS P8H67

I recently got a new hard disk for my computer (Seagate Barracuda 2000GB, old one failed), and installed Windows first in a 250GB partition, ran fine. I then went to install Linux Mint 12 (Ubuntu 11.10), making a 1GB FAT16 partition to be the EFI partition as /dev/sda2, and then making an extended partition, in which I put 16GB Swap, 250GB "/," 500GB "/home," and a 750GB NTFS partition.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   512002047   256000000    7  HPFS/NTFS/exFAT
/dev/sda2   *   512002048   514099199     1048576    6  FAT16
/dev/sda3       514101246  3618867199  1552382977    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       514101248   546869247    16384000   82  Linux swap / Solaris
/dev/sda6       546871296  1058871295   256000000   83  Linux
/dev/sda7      1058873344  2082873343   512000000   83  Linux
/dev/sda8      2082875392  3618867199   767995904    7  HPFS/NTFS/exFAT

```


Mint works fine, but when I try to boot Windows, it gives me the following error:

```
error: invalid EFI file path
```


A Google search didn't really help. Any ideas?

---

### Post by oldfred on 2012-01-04
You cannot mix UEFI & BIOS which it looks like you have done.

Windows only boots on gpt formated drives with UEFI. If BIOS Window must have MBR(msdos) formated drive.

Ubuntu will boot from gpt or MBR with BIOS and some have gotten it to boot with UEFI and gpt with Windows. But grub does have a few bugs and/or some motherboard mfgs have only tested with Windows and may not be fully UEFI standard.

You have an extended partition which means your drive is MBR. If you had gpt drive and were booting with UEFI Windows would have created a efi partition. But the UEFI standard requires the efi partition to be the first partition on a drive. Windows then wants another partition for its boot.

Older Windows info on gpt - 2008
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by Fajner1 on 2012-01-05
But then why would it have been working before?

---

### Post by oldfred on 2012-01-05
When you say before. Is this a new install, or did Ubuntu just install in MBR mode before. Now perhaps the UEFI mode is seeing a efi partition and it is not correct so it is not then defaulting to MBR, not sure?

Post this. this is an update/test version that also has some fixes to see efi partitions.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Check if these are installed by trying to install.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Now the older version:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Fajner1 on 2012-01-05
Results.txt:

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/linuxmint/grubx64.efi

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   512,002,047   512,000,000   7 NTFS / exFAT / HPFS
/dev/sda2    *    512,002,048   514,099,199     2,097,152   6 FAT16
/dev/sda3         514,101,246 3,618,867,199 3,104,765,954   5 Extended
/dev/sda5         514,101,248   546,869,247    32,768,000  82 Linux swap / Solaris
/dev/sda6         546,871,296 1,058,871,295   512,000,000  83 Linux
/dev/sda7       1,058,873,344 2,082,873,343 1,024,000,000  83 Linux
/dev/sda8       2,082,875,392 3,618,867,199 1,535,991,808   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        344048CA40489490                       ntfs       
/dev/sda2        0499-8D24                              vfat       
/dev/sda5        d4e96d07-11f7-4b1f-8361-1b8ddf3977cf   swap       
/dev/sda6        ec2a4fa9-f818-418a-8e86-9e3917b9a18a   ext4       Linux
/dev/sda7        fb185620-a6a4-418b-aac4-962e49970e32   ext4       Linux Home
/dev/sda8        1823845B79A501BD                       ntfs       Windows Secondary

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,user_xattr,commit=0)
/dev/sda8        /home/peter/WinD         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

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
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda6)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=ec2a4fa9-f818-418a-8e86-9e3917b9a18a ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda6) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=ec2a4fa9-f818-418a-8e86-9e3917b9a18a ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root ec2a4fa9-f818-418a-8e86-9e3917b9a18a
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 344048CA40489490
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ec2a4fa9-f818-418a-8e86-9e3917b9a18a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=0499-8D24  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda7 during installation
UUID=fb185620-a6a4-418b-aac4-962e49970e32 /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sda5 during installation
UUID=d4e96d07-11f7-4b1f-8361-1b8ddf3977cf none            swap    sw              0       0
# Windows Secondary
UUID=1823845B79A501BD /home/peter/WinD                    ntfs    defaults,uid=1000,gid=1000,auto        0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 374.901565552 = 402.547490816  boot/grub/grub.cfg                             2
 263.648536682 = 283.090460672  boot/initrd.img-3.0.0-12-generic               2
 374.901554108 = 402.547478528  boot/vmlinuz-3.0.0-12-generic                  1
 263.648536682 = 283.090460672  initrd.img                                     2
 374.901554108 = 402.547478528  vmlinuz                                        1


```

---

### Post by oldfred on 2012-01-05
I have no idea if you can get Mint to work with efi on a MBR system, but Windows will only boot with gpt on UEFI. Is your install of Windows the 64 bit version?

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

---

### Post by Fajner1 on 2012-01-05
Yeah, it's Vista 64-bit. Vista was the first OS to touch the disk, and was capable of booting before GRUB was installed, so it can evidently boot from an UEFI-MBR combination. Maybe UEFI didn't detect an EFI partition, so it pretended to be a legacy BIOS, but then when an EFI partition was created by Mint, it started booting the EFI way?

---

### Post by oldfred on 2012-01-05
I do know that new versions of Ubuntu's installer will create a gpt drive if the drive is over 1TB and empty, not sure what it does if you already have Windows in MBR installed? Possibly a bug?

It seems that many have issues with the Ubuntu installer and efi. But you have MBR, so I am not sure why you now would get a efi partition. The efi partition has to be first and you do not have that. Know nothing about reporting bugs against Mint, but a lot of it is Ubuntu based.

---

### Post by Fajner1 on 2012-01-06
I thought one of the advantages of EFI was that the EFI partition can be anywhere?

And would reinstalling/repairing Windows and then restoring GRUB help?

---

### Post by oldfred on 2012-01-06
The Arch site has some good info on efi.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

---

### Post by Fajner1 on 2012-01-08
So would I need to attempt to follow the tutorial on transforming Windows from BIOS/MBR to UEFI/GPT?

---

### Post by oldfred on 2012-01-08
Your choice. UEFI is new, but many of us do not know details, grub seems to have some bugs but some have installed dual boot UEFI.

It may be easier, if Windows is already MBR/BIOS, just to install Ubuntu in MBR/BIOS. I think if you remove efi partition it should install the current standard MBR way.

Either way back up any of your data, and partition in advance. Gparted can do either gpt or MBR (msdos).

I still have BIOS, but am setting up my new drives with 300MB space at the beginning for a future efi partition. Then if I move drive to new UEFI system, I will not have to move a lot of partitions around. Since I use gpt and have no Windows on that new drive, I also create the 1MB bios_grub partition. But bios_grub is only required if using gpt & BIOS with Linux as Windows will not work with gpt unless in UEFI mode.

---

### Post by Fajner1 on 2012-01-08
I've had maybe a bit of a breakthrough. What exactly does "***chainloader +1***" in the GRUB entry do? Because I searched my Windows partition for "*.efi*" and found three "**.efi*" files in "***[Windows Partition]/Windows/Boot/EFI***" directiory. Does "*chainloader +1*" try to boot from "***[Windows directory]/Boot***?" That would explain why it finds an invalid file path - the fields it's looking for don't exist.

I changed the Vista entry from

```
#!/bin/sh -e
echo "Adding Vista"
cat << EOF
menuentry "Vista" {
set root=(hd0,1)
chainloader (hd0,1)+1
}
EOF
```


to

```
#!/bin/sh -e
echo "Adding Vista"
cat << EOF
menuentry "Vista Modifikovane 3" {
set root=(hd0,1)
chainloader (hd0,1)/Windows/Boot/EFI/bootmgfw.efi
}
EOF
```


and now it gives the standard Windows startup error screen (the same style as "*Your computer shut down improperly*"), telling me that BCD is corrupted or missing, and to repair from the DVD. Obviously, if I were to do that, it would erase GRUB, and then reinstalling GRUB would probably erase BCD, so I'd have to do a bootloader recovery every time I wanted to change between Mint and Vista.

As I was typing this, I also found another file, "***[Windows partition]/Windows/System32/winload.efi***," so I'll try directing GRUB to that.

---

### Post by oldfred on 2012-01-08
With MBR a Windows boot loader in the MBR checks some things & jumps to the PBR or partition boot sector. All grub does when it chainloads is jump to that same PBR. 

EFI is different in that the UEFI boot loader reads an efi partition for boot files. You have MBR and no efi partition. Windows may have the files for efi in its MBR install as is may be part of all installs.

Did you run bootinfoscript from the wget download as it now searches for efi files in the locations that you would boot from. Just having them in the Windows system folders does not mean they are used for booting.

If you want to know how Windows boots with MBR this show it with pictures. If you want to know all the details the article is pretty complete.
Multibooters, Pictures here worth 1000+ words 
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

