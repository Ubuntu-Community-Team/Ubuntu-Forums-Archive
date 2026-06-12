---
title: "Boot issues"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by zoboom on 2012-02-06
I'm sorry to steal this thread but I'm having the same problem after installing Linux Mint 12 over Ubuntu 11.10. I chose the option to overwrite Ubuntu (don't worry I'm running it on my laptop now) and after the installation I get the
```

grub rescue>

```prompt. Here is the output of the terminal commands you gave:

                   ```
Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

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
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 12 Lisa
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:  Syslinux looks at sector 30510 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 2,540,150,232 2,539,943,385   7 NTFS / exFAT / HPFS
/dev/sda3       2,540,150,782 2,930,276,351   390,125,570   5 Extended
/dev/sda5       2,540,150,784 2,542,149,631     1,998,848  83 Linux
/dev/sda6       2,542,151,680 2,548,150,271     5,998,592  82 Linux swap / Solaris
/dev/sda7       2,548,152,320 2,588,149,759    39,997,440  83 Linux
/dev/sda8       2,588,151,808 2,930,276,351   342,124,544  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            128     7,831,551     7,831,424   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        047483B37483A5D0                       ntfs       System Reserved
/dev/sda2        62A88600A885D2C9                       ntfs       
/dev/sda5        3e82466f-16ab-4e58-aa69-3e5c3386ebee   ext4       
/dev/sda6        d64f85d6-f890-4017-a828-3d30364c556a   swap       
/dev/sda7        ebfcefdd-399f-48f1-b6c9-560b5f921176   ext4       
/dev/sda8        6d059910-236a-4a27-95cc-250dd88c2e82   ext4       
/dev/sdb1        07E8-182F                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda5/grub/grub.cfg: ==============================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root ebfcefdd-399f-48f1-b6c9-560b5f921176
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 3e82466f-16ab-4e58-aa69-3e5c3386ebee
  set locale_dir=($root)/grub/locale
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
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda5)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3e82466f-16ab-4e58-aa69-3e5c3386ebee
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfcefdd-399f-48f1-b6c9-560b5f921176 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Linux Mint 12 64-bit, 3.0.0-12-generic (/dev/sda5) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3e82466f-16ab-4e58-aa69-3e5c3386ebee
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=ebfcefdd-399f-48f1-b6c9-560b5f921176 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3e82466f-16ab-4e58-aa69-3e5c3386ebee
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 3e82466f-16ab-4e58-aa69-3e5c3386ebee
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 047483B37483A5D0
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1211.367202759 = 1300.695629824 grub/grub.cfg                                  1
1211.386718750 = 1300.716584960 initrd.img-3.0.0-12-generic                    2
1211.391059875 = 1300.721246208 vmlinuz-3.0.0-12-generic                       1

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=ebfcefdd-399f-48f1-b6c9-560b5f921176 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=3e82466f-16ab-4e58-aa69-3e5c3386ebee /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=6d059910-236a-4a27-95cc-250dd88c2e82 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=d64f85d6-f890-4017-a828-3d30364c556a none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=white/light-gray

menuentry "Start Linux Mint" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Start Linux Mint (compatibility mode)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/mint.seed boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
    initrd    /casper/initrd.lz
}
menuentry "Check the integrity of the medium" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
default vesamenu.c32

menu background splash.jpg
menu title Welcome to Linux Mint
menu color border 0 #00eeeeee #00000000
menu color sel 7 #ffffffff #33eeeeee
menu color title 0 #ffeeeeee #00000000
menu color tabmsg 0 #ffeeeeee #00000000
menu color unsel 0 #ffeeeeee #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000

label live
  menu label Start Linux Mint
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash --
menu default
label xforcevesa
  menu label Start Linux Mint (compatibility mode)
  kernel /casper/vmlinuz
  append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper xforcevesa initrd=/casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
label memtest
  menu label Memory Test
  kernel memtest
label local
  menu label Boot from local drive
  localboot 0x80 --------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
```

---

### Post by zoboom on 2012-02-06
Sorry, I just did the script through Boot Repair itself. I got this:
[http://paste.ubuntu.com/830973/](http://paste.ubuntu.com/830973/)

---

### Post by oldfred on 2012-02-06
Please do not highjack another thread, multiple outputs of bootsript start to get confusing especially if issues are similar but still different. Created new thread.

Also added code tags to make first post easier to read. boot script should be the same in link, but Boot-Repair may add some added info.

---

### Post by oldfred on 2012-02-06
Grub Rescue says grub is there but then something is missing to fininsh loading.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

You have a separate /boot partition, which I do not recommend for standard desktop installs. It makes grub repair a bit more difficult and many instructions posted do not include the extra instructions for including the boot partition or just have a footnote somewhere.

From Boot Repair, if you check sda5 as /boot and sda7 as / (root) and run repair what happens?

---

### Post by zoboom on 2012-02-07
I apologize for my ignorance on the thread. Thanks for opening a new one and helping me out.

I've since used ms-sys to repair my Windows MBR and I've reinstalled Linux Mint 12. When I start up my computer, instead of being greeted by the GRUB2 menu I am shot straight into Windows 7 as if GRUB2 was never installed. I remember watching the installation and seeing the GRUB installation at least be printed out.

Assuming that you might ask me for more output I've run Boot Repair again. I should mention that I get this warning after clicking the recommended repair:
> The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, >200Mo, start of the disk, EFI flag). Do you want to continue?Here is the output of the BootInfo Summary:
[http://paste.ubuntu.com/832309/](http://paste.ubuntu.com/832309/)

I've also been looking at this post:
[COLOR=Black][/COLOR][http://ubuntuforums.org/showthread.php?t=1628596](http://ubuntuforums.org/showthread.php?t=1628596)
As I understand it I do not have grub installed on my MBR.

I haven't had any luck with this order of commands:
> #Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sd[COLOR=Red]a[/COLOR]5, if sdb5 change every [COLOR=Red]a[/COLOR] to b.
sudo mount /dev/sd[COLOR=Red]a[/COLOR]5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sd[COLOR=Red]a[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sd[COLOR=Red]a[/COLOR]After running sudo mount /dev/sda5 /mnt I don't receive any feedback and when I try to install grub it tells me that there is no device for /boot. Any suggestions? Do you need more information?

Thanks for your help.

---

### Post by oldfred on 2012-02-07
With grub 1.99 they have changed from root to boot. But I thought the old instructions still worked.

sudo mount /dev/sda5 /mnt
sudo grub-install --[COLOR=Red]root[/COLOR]-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --[COLOR=Red]boot[/COLOR]-directory=/mnt[COLOR=Red]/boot [/COLOR]/dev/sda

New computers with UEFI also work in BIOS/MBR mode. They seem to look for the efi partition which is normally in gpt not MBR(msdos) partitioning. The boot code cannot be set in MBR partitioning.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Windows will only use UEFI if gpt partitioning. Ubuntu can use gpt in BIOS (I use it so I know that works), but has some bugs in installing in dual boot with Windows in UEFI mode. Most seem to say it works if you gpt partition in advance, install Ubuntu, then install Windows which is the opposite order of BIOS/MBR install order.

---

### Post by zoboom on 2012-02-07
Well grub now works. I booted my computer this morning and I was directed to the grub menu. I'm guessing your commands from the old post actually worked, but I'm not sure how. I'm sorry I don't have a more complete answer for you.

Again, if you need more information I'll be glad to provide it. I'll set this thread to [SOLVED].

---

