---
title: "grub2 problem -- can boot from the grub prompt but no automatic boot or menu"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by anotherk on 2012-06-07
Hello, sorry if this is already out there.  I just did a fresh install of 12.04 (had a previous ubuntu install which was broken) on a ~2009 intel imac.    

On boot I fall into the grub prompt (with no apparent error message).  I can boot just fine from the grub prompt, but I can't seem to make grub either automatically boot or show the menu.  (in particular shift doesn't give a menu)      

Most of the other grub2 threads I've seen just say to rerun the config programs.  Both update-grub and update-grub2 find the kernel and initrd correctly and write plausible things in grub.cfg, but I still end up at the prompt.      

I'm a bit unsure where to look next since nothing seems to be giving an error.  Does anyone know how I can either fix this problem or at least get more information -- for example how can I determine if grub is reading its config files?      

One complexity may well be that I am on an imac so rEFIt runs first and thus grub is on /dev/sda3, not on /dev/sda, however since I can boot from the grub prompt I know that the current set up can work -- its just a case of telling grub to do it itself.      

Thanks

---

### Post by darkod on 2012-06-07
Can you run the boot info script from live mode? The link is in my signature. It should show more details.

In general, you need to check if /boot/grub/core.img exists, and you can also try reinstalling grub2 to sda3.

---

### Post by anotherk on 2012-06-07
```
ls -l /boot/grub/core.img 
-rw-r--r-- 1 root root 25982 Jun  7 11:49 /boot/grub/core.img

```
so it exists
```
sudo grub-install /dev/sda3 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```I suppose this is the problem.  My understanding is that installing grub directly to /dev/sda will conflict with rEFIt (though I am not certain about that, so if anyone knows better please let me know).   I have something else I need to do right now, but I will look into blocklists and to the boot info script this afternoon.

---

### Post by wilee-nilee on 2012-06-07
[COLOR=White].[/COLOR]

---

### Post by darkod on 2012-06-07
If installing onto a partition you have to force it with -f. Completely forgot you can boot manually.

Boot once, and try:
sudo grub-install -f /dev/sda3

Then adjust rEFIt (if you need to) to chainload to sda3.

---

### Post by anotherk on 2012-06-07
grub-install -f runs successfully (with the warnings of course), but no change on reboot.   

 I wonder if I have an old grub around as well which rEFIt is chaining to instead.  Do you know how to determine the version from the grub prompt?  In the mean time I still have a number of other ideas to try from your helpful posts.

---

### Post by darkod on 2012-06-07
> **anotherk said:**
> grub-install -f runs successfully (with the warnings of course), but no change on reboot.   

 I wonder if I have an old grub around as well which rEFIt is chaining to instead.  Do you know how to determine the version from the grub prompt?  In the mean time I still have a number of other ideas to try from your helpful posts.

Well, only you know what rEFIt is trying to boot right now. That's why I said it's possible you would need to adjust it. :)

I've never even seen it, so I'm clueless about that. It looks like grub2 is installed on sda3 right now. You need to look into what rEFIt is trying to boot.

EDIT PS: I don't know how to check the version from a grub prompt. The boot info script will (should) show it.

---

### Post by Cavsfan on 2012-06-07
```
sudo grub-install /dev/sda
```The partition is not necessary. I had been doing this command a lot as I installed 12.04 a few times before I got it right.

---

### Post by darkod on 2012-06-07
> **Cavsfan said:**
> ```
sudo grub-install /dev/sda
```The partition is not necessary. I had been doing this command a lot as I installed 12.04 a few times before I got it right.

Did you notice we are talking about an iMac? Would that work on iMac too?

I don't know, that's why I didn't suggest it. Otherwise I always prefer grub2 on the MBR instead of on a partition.

---

### Post by anotherk on 2012-06-07
Yes, that is exactly the problem.   I ran the boot info script and it says that  there is a grub 0.97 on /dev/sda  (as opposed to the grub 1.99 on /dev/sda3 which is the one I'm trying to use.)  The old grub must be left over from my botched old linux install.


This suggests to me (1) there is a cheap solution just by putting and old-style /boot/grub/menu.lst back for the old grub to read. (2) probably I can install the grub2 to /dev/sda itself, since apparently that's how old grub was installed (yikes I don't want to break the efi stuff!). 



Here is the output from boot info script


```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy0.97 is installed in the MBR of /dev/sda and looks at sector 
    176902080 of the same hard drive for the stage2 file.  A stage2 file is at 
    this location on /dev/sda.  Stage2 looks on partition #3 for 
    /boot/grub/menu.lst..

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda3 
                       and looks at sector 91901888 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,gpt3)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       409,639       409,639  ee GPT
/dev/sda2             409,640    84,004,247    83,594,608  af HFS / HFS+
/dev/sda3    *     84,004,248   279,316,748   195,312,501  83 Linux
/dev/sda4         603,135,108   625,142,414    22,007,307  82 Linux swap / Solaris


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2         409,640    84,004,247    83,594,608 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda3      84,004,248   279,316,748   195,312,501 Data partition (Windows/Linux)
/dev/sda4     603,135,108   625,142,414    22,007,307 Swap partition (Linux)
/dev/sda5     279,316,749   603,133,155   323,816,407 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        640B-0804                              vfat       EFI
/dev/sda2        4ff69b4f-cc7c-31ac-9bd0-817e2cd2822d   hfsplus    Macintosh HD
/dev/sda3        20bea385-bb59-4247-91c8-7a6c5a8afeaf   ext3       
/dev/sda4        ba960f9a-a2e6-4814-9c20-15313af09507   swap       
/dev/sda5        36dd09d4-1d22-4eff-ae02-8c5ed79d6e32   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,errors=remount-ro)
/dev/sda5        /home                    ext3       (rw)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt3)'
search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt3)'
  search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  #set timeout=-1
  set timeout=0
else
  #set timeout=0
  set timeout=0
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=20bea385-bb59-4247-91c8-7a6c5a8afeaf ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=20bea385-bb59-4247-91c8-7a6c5a8afeaf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=20bea385-bb59-4247-91c8-7a6c5a8afeaf ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=20bea385-bb59-4247-91c8-7a6c5a8afeaf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    search --no-floppy --fs-uuid --set=root 20bea385-bb59-4247-91c8-7a6c5a8afeaf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 3f764231b7239940
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 3f764231b7239940 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {
    insmod part_gpt
    insmod hfsplus
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root 3f764231b7239940
        load_video
        set do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             set do_resume=1
           fi
        fi
        if [ $do_resume = 0 ]; then
           xnu_uuid 3f764231b7239940 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devprop.bin ]; then
              xnu_devprop_load /Extra/devprop.bin
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
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
UUID=20bea385-bb59-4247-91c8-7a6c5a8afeaf /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=36dd09d4-1d22-4eff-ae02-8c5ed79d6e32 /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=ba960f9a-a2e6-4814-9c20-15313af09507 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             2
               =                boot/initrd.img-3.2.0-23-generic              10
               =                boot/initrd.img-3.2.0-24-generic               7
               =                boot/vmlinuz-3.2.0-23-generic                  3
               =                boot/vmlinuz-3.2.0-24-generic                  4
               =                initrd.img                                     7
               =                initrd.img.old                                10
               =                vmlinuz                                        4
               =                vmlinuz.old                                    3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 04 08 0b 64 45  46 49 20 20 20 20 20 20  |..)...dEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by darkod on 2012-06-07
I haven't worked on a Mac so I can't tell you for sure. But this is my assumption. The key word is ASSUMPTION, follow on your own risk! :)

The EFI boot looks for the EFI system partition, it ignores the bootloader actually on the MBR. In your case, it seems you have an entry in the EFI boot which relates to the bootloader on the MBR, which is a broken grub1 right now.

If this is correct, installing the grub2 on the MBR would solve it since rEFIt will simply call (chain) to the bootloader on the MBR. It shouldn't affect the OSX boot since right now the broken grub1 can't boot it either. I guess the OSX is booted from the EFI system partition, unrelated to the MBR bootloader.

Another option, go into BIOS or rEFIt (or what ever it's called) and try making a new entry chaining to sda3. If that works you can delete the non working ubuntu entry.

From discussions here about the new boards with EFI boot there is an option to add OSs in the EFI boot menu somewhere in the BIOS.

---

### Post by anotherk on 2012-06-07
The reason I thought that with rEFIt and dual booting I couldn't put the bootloader on /dev/sda itself is that a number of folks say that, eg [http://www.noah.org/wiki/Ubuntu_install_on_Apple_Mac_Intel_hardware](http://www.noah.org/wiki/Ubuntu_install_on_Apple_Mac_Intel_hardware) , [http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required](http://lifehacker.com/5531037/how-to-triple+boot-your-mac-with-windows-and-linux-no-boot-camp-required)


It looks to me like most likely this is not actually a problem and I should just install to /dev/sda -- I don't suppose anyone can confirm for me that that will work before I try it?

---

### Post by Cavsfan on 2012-06-07
> **darkod said:**
> Did you notice we are talking about an iMac? Would that work on iMac too?

I don't know, that's why I didn't suggest it. Otherwise I always prefer grub2 on the MBR instead of on a partition.

No, I didn't notice it was an iMac. But, I can attest to the fact that using the partition would not work on my system. 
Drs305 told me not to use the partiton just the drive like I mentioned and it would only work that way too.
My 12.04  grub took over my system a couple of times and I had to go into 10.04 and enter ```
sudo grub-install /dev/sda
```I tried sda3 but, that would not work.
That's my 1 1/2 cents.

---

### Post by anotherk on 2012-06-07
I got impatient and tried (yes my own risk and all of that).  I feared that it would break rEFIt but no problem there -- rEFIt is fine and can boot macos.  The linux install is now completely unreachable. This sort of problem, however, seems to be much easier to find information on, so I should be able to sort this one out.  I'll post my solution once I find it in case anyone with the same problem finds the thread.

---

### Post by anotherk on 2012-06-07
Half way there (and back to apparently being a grub issue rather than a rEFIt issue)  

  After resynching partition tables and rebooting more times than seemed necessary, I can boot ubuntu -- but only on the second try!  First time I select the correct os in rEFIt, I get the black screen with a flashing cursor for a moment (which is grub starting up, I think), then it freezes on a black screen.  Reboot and next time, select in rEFIt, get black screen with flashing cursor for a moment, then get ubuntu.  Also shouldn't grub be giving me a menu now (2 different possible kernels and memtest)?

---

### Post by oldfred on 2012-06-07
I do not know Macs either, but a couple of links.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

---

