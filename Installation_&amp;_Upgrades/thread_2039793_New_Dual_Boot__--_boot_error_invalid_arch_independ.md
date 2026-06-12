---
title: "New Dual Boot  -- boot error: invalid arch independent ELF magic. grub rescue"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Race577 on 2012-08-09
I am stuck.  Can't boot into anything w/o LiveCd

New HP p7-1108p with Windows 7 already installed.

Setting up Dual Boot w/Ubuntu 12.04.  (Old computer had XP and Ubuntu 10.10)

Resized Window 7 OS partition with GParted, to make room for 12.04.

Could not set up separate / and /home partition because Windows 7 using 3 partitions already, so I just let 12.04 install in new unallocated space.

Initially it worked fine.  After getting most everything tweaked, I made the mistake of using the computer Janitor.  Thought I could clean up the packages that I had loaded and then didn't use.

After reboot, I get: 

```
error: invalid arch independent ELF magic. grub rescue
```Here is what I have done so far.

     Used LiveCD/terminal to try and fix problem. (no success)

At some point I tried to apply this suggestion to my setup:

Used GParted to remove new partitions and reinstalled 12.04
              same result  (did it twice)

Saw [http://askubuntu.com/questions/72003/grub-invalid-arch-independent-elf-magic-after-11-10-install-on-macbook-pro-5/72995#72995](http://askubuntu.com/questions/72003/grub-invalid-arch-independent-elf-magic-after-11-10-install-on-macbook-pro-5/72995#72995)

```
 The solution for me was (and probably for anyone having that problem):

  Boot into the live cd and type into the terminal (of course you must  edit the mounting operations respecting your own partition table):

sudo apt-get install grub-efi-amd64 
sudo mount /dev/sda3 /mnt 
sudo mount /dev/sda1 /mnt/boot  
sudo grub-install --root-directory=/mnt /dev/sda 

Now grubx64.efi should boot without any problems.
```Tried to apply this to my Partition layout, but did not get it to work.

Eventually used GParted to remove HP RECOVERY partition (*I know this is a bad idea, but I made recovery disks before hand.*)

                 Installed 12.04 with / and /home partitions.  

                     Still have same error msg.


ATTACHED is what GParted shows now.



Here is my Boot Info Script (gotten from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/))

```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

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
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   123,086,847   122,880,000   7 NTFS / exFAT / HPFS
/dev/sda3         123,086,848   162,148,351    39,061,504  83 Linux
/dev/sda4         162,150,398 1,953,523,711 1,791,373,314   5 Extended
/dev/sda5       1,933,993,984 1,953,523,711    19,529,728  82 Linux swap / Solaris
/dev/sda6         162,150,400 1,933,633,535 1,771,483,136  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        F45E22585E2213C0                       ntfs       SYSTEM
/dev/sda2        06EA2350EA233AF7                       ntfs       OS
/dev/sda3        ca32f228-8c31-45a8-a895-09d1b3eec52a   ext4       /
/dev/sda5        64f141e3-3959-4649-b8e1-ceeb1dc38afe   swap       
/dev/sda6        ea43b534-bc93-4c1a-8ae3-c9905d6ee955   ext4       /home
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/sda3              ext4       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=ca32f228-8c31-45a8-a895-09d1b3eec52a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=ca32f228-8c31-45a8-a895-09d1b3eec52a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root ca32f228-8c31-45a8-a895-09d1b3eec52a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root F45E22585E2213C0
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 06EA2350EA233AF7
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=ca32f228-8c31-45a8-a895-09d1b3eec52a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ea43b534-bc93-4c1a-8ae3-c9905d6ee955 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=64f141e3-3959-4649-b8e1-ceeb1dc38afe none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```Can someone PLEASE help me? :confused:

---

### Post by oldfred on 2012-08-09
There is a different version of grub2 for UEFI systems that is grub-efi. You do not have efi, so that will not work. And you do not have a separate /boot so you should not mount that.

Your MBR is looking for the rest of grub files in sda5, but that is swap? Your instal is in sda3

sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

Then after you boot into your install 
sudo update-grub

Alternatively you can use Boot-Repair

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Race577 on 2012-08-10
Thank you oldfred, your help and skills are greatly appreciated.

I  had used Boot-Repair earlier, after the initial install and had everything booting up fine, but when I messed it up later, I did not think to use it again.

---

### Post by gordintoronto on 2012-08-10
> **Race577 said:**
> ... Could not set up separate / and /home partition because Windows 7 using 3 partitions already, so I just let 12.04 install in new unallocated space.

You could have set up a fourth partition as an "Extended" partition, and within it, create as many partitions as you need, such as root, home and swap.

---

### Post by anshuhim20 on 2013-07-17
Dear List,
I had re-installed  Ubuntu 12.04 from live CD
This is a dual boot system because I had windows and the newly installed UBUNTU on my system
But Error is 
"Invalid arch independent ELF magic"
For this I had tried both the options 
No. 1
With the Live Ubuntu CD click try Ubuntu
then Connected to "internet"
Then I tried the two commands

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[FONT=inherit][/FONT]sudo apt-get install -y boot-repair && boot-repaireven then I errors with ppa:yannubuntu

No. 2
Using Linux secure remix
But the disk written is not detected by the system and again the error comes
"Invalid arch independent ELF magic"

Please gube WHat to do ?

---

### Post by oldfred on 2013-07-17
Installing Boot-Repair into your live installer should work. If you copy & pasted commands it works. But if typing sometimes even spaces are vital.

Often the ELF magic issue is imcompatible versions of grub. Did you have an old install's grub boot loader in the MBR and not install the new version into the MBR?

---

