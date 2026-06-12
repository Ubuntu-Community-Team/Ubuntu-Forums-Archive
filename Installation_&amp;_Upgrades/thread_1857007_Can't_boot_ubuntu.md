---
title: "Can't boot ubuntu"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Noob_Zaiboot on 2011-10-09
Hi Everyone,

I have recently installed ubuntu 11.4. I installed it beside windows 7. It installed with no problems but then when i restarted my computer it just went straight into windows and didn't even give the option to pick between the two. I used a usb creator to install ubuntu. when i run gparted from the live boot here's what i get:

partition       File System    Label                       Size           Used       Unused          Flags
/dev/sda1    ntfs                 System Reserved  100.00mb  33.59mib  66.41mib       boot
/dev/sda2    ntfs                                                 585gib       49gib        536gib                  
/dev/sda3    extended                                        345gib        --              --
  /dev/sda5  ext4                                                337gib       8gib          329gib
  /dev/sda6  linux-swap                                          8gib       --               --

so its definatly installed

I think the problem may be that grub never installed properly.Here's my grub folder:

ubuntu@ubuntu:/boot/grub$ ls
gfxblacklist.txt  grubenv


I don't have a clue what to do next. I've already tried boot-repair but with no luck.

Any help would be greatly appreciated.

---

### Post by MAFoElffen on 2011-10-09
> **Noob_Zaiboot said:**
> Hi Everyone,

I have recently installed ubuntu 11.4. I installed it beside windows 7. It installed with no problems but then when i restarted my computer it just went straight into windows and didn't even give the option to pick between the two. I used a usb creator to install ubuntu. when i run gparted from the live boot here's what i get:

partition       File System    Label                       Size           Used       Unused          Flags
/dev/sda1    ntfs                 System Reserved  100.00mb  33.59mib  66.41mib       boot
/dev/sda2    ntfs                                                 585gib       49gib        536gib                  
[COLOR=Blue]/dev/sda3    extended                                        345gib        --              --
  /dev/sda5  ext4                                                337gib       8gib          329gib
  /dev/sda6  linux-swap                                          8gib       --               --

[COLOR=Black]so its definatly installed[/COLOR][/COLOR]

I think the problem may be that grub never installed properly.Here's my grub folder:

ubuntu@ubuntu:/boot/grub$ ls
gfxblacklist.txt  grubenv


I don't have a clue what to do next. I've already tried boot-repair but with no luck.

Any help would be greatly appreciated.
Let me understand this... I may be mistaken, but from doing 20+ installs a week, I see a bigger problem that just the grub (someone correct me if they see it diffrently)...

So in gpartted it shows 2 NTFS partions, then an extended partition with 2 logical partitions within it <> ext4 (ubuntu) and your swap? 

I think it should rather end up as:
NTFS primary bootable
NTFS primary
Ext4 primary bootable
Extended 
-->  Linux-Swap  <this will show as same size as extended>

Since it is a new fresh install and nothing is modified and configured yet, I would do a reinstall.  Here is how I would do it:

1. In gparted, delete sda3, sda5 and sda6. Leave the unused space as such.

2. In Windows Disk Manager, move the 2 NTFS partitions back "1 sector" each.  Ends up as 1 sector unallocated before the first partition. Prevents some multi-boot problem crashes that happen on some systems.

3. Reinstall Ubuntu using the installer's disk partitioner (first option that should be on top) "guided- used unused space"...

That should end up with what I thought it should above and it should set the correct flags and types for you...

---

### Post by Noob_Zaiboot on 2011-10-09
Thanks for the fast reply.. 
 
I did the first one deleted the sda3 sda5 and sda6 but i don't know how to move the NTFS partitions back one sector in windows disk manager!!
 
Could ou tell me how to do that please?

---

### Post by Quackers on 2011-10-09
Why do you need to move the NTFS partitions back one sector? It's normal nowadays to have 1MB in between partitions, if that's what you are worried about.

I personally think that your original partition layout was fine. In fact, it left you a "spare" primary partition available for creation, should you need one. I suspect that grub just needed to be installed (although it would be nice to know why grub didn't install normally in the first place).

---

### Post by Noob_Zaiboot on 2011-10-09
Well i was just going by what mafoelffen said as i don't know much at all about partitioning. So as it stands now all i have is the System reserved 100mb and my C: drive. That leaves me two primary partitions i think. 
 
If i install ubuntu now how do i install the grub bootloader and where?

---

### Post by Quackers on 2011-10-09
There could be a couple of reasons why grub did not install properly.
Did you change the default location for grub during the installation?
Did you install via a cd or a usb flash drive?

---

### Post by Noob_Zaiboot on 2011-10-09
When i installed it i just choose to install it alongside windows 7. I didn't change any settings at all just clicked forward the whole way through the installation.

---

### Post by Quackers on 2011-10-09
Did you install via a usb flash drive? Sometimes when a flash drive is plugged in the pc can make that flash drive /dev/sda. This can cause grub to be installed to that flash drive rather than the internal hard drive - as /dev/sda is the default location for grub to be installed.

---

### Post by Noob_Zaiboot on 2011-10-09
Yeah i installed it via a flash drive.

---

### Post by Quackers on 2011-10-09
Ok, can you boot from that flash drive and select "try Ubuntu" from the menu and when the desktop loads open up gparted.
Which drive is shown as /dev/sda in gparted? Is it your flash drive or your internal HDD?

---

### Post by Noob_Zaiboot on 2011-10-09
/dev/sda isn't even there. Its just /dev/sda1 ntfs /dev/sda2 ntfs and then just unallocated space..

---

### Post by Quackers on 2011-10-09
Ok, if it's showing /dev/sda1 and /dev/sda2 that's fine. You should be able to see /dev/sda in a box near the top right with a little drop-down arrow near it.
The important thing is that it is showing the NTFS partitions as /dev/sda1 and /dev/sda2.
If you now click on the installer icon on the desktop and re-install Ubuntu using the option that MAFoElffen recommended (guided - use unused space) you should be good.
Please make a note of any error message, if any.

---

### Post by Noob_Zaiboot on 2011-10-09
Ok but i don't see that option. All there is is "Install ubuntu alongside window7" "Replace windows 7 with ubuntu" or "something else". Which shud i pick? And Sorry for being such a noob Ha.

---

### Post by Quackers on 2011-10-09
Don't worry about that :-) I haven't used option 1 or option 2 before either with the 11-04 installer!
The option mentioned earlier may have finished in an earlier Ubuntu installer.

I would use the "something else" option, then when your current partitions appear in the new window I would double-click on the "unallocated space" after /dev/sda2 and create 2 new partitions.
The first being a swap partition slightly larger than the amount of ram installed (if I intended to use "hibernate"). This partition should be of the type LOGICAL (from the drop down box).
The second partition can be the rest of the available unallocated space if you wish. 
This should also be of type LOGICAL and formatted as type ext4. The mount point should be " / " from the drop-down box.
If you want a separate home partition get back to me.

---

### Post by Noob_Zaiboot on 2011-10-09
Yeah i would like to create a home partition please. Also theres the option for boot loader installation /dev/sda. Will i leave that at its default?

---

### Post by Quackers on 2011-10-09
Ok then, in the "something else" option you can double-click on the unallocated space and create 3 new partitions - ALL LOGICAL, that's important!

The first can be a swap partition of a size chosen by you.
The second can be maybe 12000 or 13000 MB in size (or larger if you wish) and formatted to ext4 with a mount point of " / " from the drop-down menu which will be your Ubuntu root partition.
The third partition can be the rest of the unallocated space (or less if you want) formatted to ext4 with a mount point of "/home" from the drop-down menu.

All the above partitions need to be created one at a time. After each one you will need to double-click on the remaining unallocated space again on the original screen to create the next one.

Once they are created and checked (particularly the LOGICAL part) you can proceed with the installation.
The installer should install grub to the default location (/dev/sda).

---

### Post by Noob_Zaiboot on 2011-10-09
No Luck. It just booted straight into windows again. But there is one thing when the installation finishes and it says to restart the computer. I restart and when it says to take out the flash and press enter i do that but then it just freezes and i hav to hit the reset button to restart it. Maybe thats what causing it? Well anyway i'll try again tomorro. Its getting late now. Thanks for all the help anyway Quackers. i'll try again tomorro and let u know.

---

### Post by Quackers on 2011-10-09
That's unfortunate.
Maybe when you get a minute tomorrow and before trying again you can boot from the flash drive again and choose "try Ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

EDIT  or alternatively have a look at the new method of doing it here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by Hakunka-Matata on 2011-10-09
extracting boot_info_script060.zip to the Downloads directory produces a file named "boot_info_script.sh" with the latest download.  So maybe the first command should be corrected.

---

### Post by Quackers on 2011-10-09
> **Hakunka-Matata said:**
> extracting boot_info_script060.zip to the Downloads directory produces a file named "boot_info_script.sh" with the latest download.  So maybe the first command should be corrected.

Really?  It creates a folder called boot_info_script060 here, inside which is boot_info_script.sh

---

### Post by Hakunka-Matata on 2011-10-09
I'm running Oneiric beta 2, maybe that's the difference that makes the difference?
This is what it looks like here.

I told it to extract to Downloads, and it dropped the .sh script right there, not contained in a separate folder.  Things keep getting moved around, keeps one on ones toes.  It's taking me a while to get used to Gnome3 in 11.10-beta2, but I like it very much so far, it's running really quite smoothly.

---

### Post by Alxl on 2011-10-09
How about this:

[https://help.ubuntu.com/community/Gr...stalling_GRUB2](https://help.ubuntu.com/community/Gr...stalling_GRUB2)

Look for : 'Copy LiveCD Files'

---

### Post by Alxl on 2011-10-09
or this: 

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by Quackers on 2011-10-10
> **Hakunka-Matata said:**
> I'm running Oneiric beta 2, maybe that's the difference that makes the difference?
This is what it looks like here.

I told it to extract to Downloads, and it dropped the .sh script right there, not contained in a separate folder.  Things keep getting moved around, keeps one on ones toes.  It's taking me a while to get used to Gnome3 in 11.10-beta2, but I like it very much so far, it's running really quite smoothly.

I'm using the same version of Ubuntu with gnome-shell. I told the download to save the file in Downloads, right-clicked the zip file and selected "extract here" and the folder appears, inside which is the .sh script.
It seems odd that we aren't finding the same thing :(

---

### Post by Hakunka-Matata on 2011-10-10
> **Quackers said:**
> I'm using the same version of Ubuntu with gnome-shell. I told the download to save the file in Downloads, [COLOR=Red]right-clicked the zip file and selected "extract here"[/COLOR] and the folder appears, inside which is the .sh script.
It seems odd that we aren't finding the same thing :(
you right-clicked, and I double-clicked.  That makes all the difference, if I do it your way, I get the folder also, double clicking and extracting does not produce a folder.  Thanks for discussing this less than critical anomaly.
NOTE: @Noob_Zaiboot:  Apologies for interrupting and going slightly off track.......... and please post the RESULTS.txt file that boot_info_script generates.

---

### Post by Noob_Zaiboot on 2011-10-10
Hey thats no problem.

Here are the results of the scan:

```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

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
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.82 2009-06-09
    Boot sector info:   Syslinux looks at sector 8200 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,228,799,999 1,228,593,152   7 NTFS / exFAT / HPFS
/dev/sda3       1,228,802,046 1,953,523,711   724,721,666   5 Extended
/dev/sda5       1,228,802,048 1,247,354,879    18,552,832  82 Linux swap / Solaris
/dev/sda6       1,247,356,928 1,272,745,983    25,389,056  83 Linux
/dev/sda7       1,272,748,032 1,953,523,711   680,775,680  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     4,030,463     4,030,432   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        84B41D9BB41D9132                       ntfs       System Reserved
/dev/sda2        769E313F9E30F8E7                       ntfs       
/dev/sda5        d25f9789-37a1-4430-91e1-d8972ffad1ff   swap       
/dev/sda6        cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1   ext4       
/dev/sda7        bb596349-e3da-4eb4-bfab-1bfad1ee1763   ext4       
/dev/sdb1        5252-D785                              vfat       JULIE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
set locale_dir=($root)/boot/grub/locale
set lang=en_IE
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 84B41D9BB41D9132
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=cccc18c4-ddc4-4f3b-83e6-0e7dab7b85f1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=bb596349-e3da-4eb4-bfab-1bfad1ee1763 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=d25f9789-37a1-4430-91e1-d8972ffad1ff none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 601.253234863 = 645.590745088  boot/grub/grub.cfg                             1
 596.464435577 = 640.448811008  boot/initrd.img-2.6.38-8-generic               2
 605.290348053 = 649.925562368  boot/vmlinuz-2.6.38-8-generic                  1
 596.464435577 = 640.448811008  initrd.img                                     2
 605.290348053 = 649.925562368  vmlinuz                                        1

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
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0 
include menu.cfg 
default vesamenu.c32 
prompt 0 
timeout 50 
ui gfxboot bootlogo 
--------------------------------------------------------------------------------

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
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

```

---

### Post by user9 on 2011-10-10
Sorry, it is wrong placed comment.

---

### Post by Hakunka-Matata on 2011-10-10
Thanks, Grub did not get installed to the MBR of sda, so you need to do that.  Using the link that Alxl also posted in post# 23.

The link to the Ubuntu Grub2 Documentation page follows.  Go to Reinstalling Grub section, 12.1.2.  (copy live CD files) and do that procedure to install Grub2 to the MBR of sda.  **EDIT: **in step 4. use this command "
**sudo mount /dev/sda6 /mnt**"  sda6 is your Ubuntu system root (/) partition. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Noob_Zaiboot on 2011-10-10
YES!! That worked. Everythings workin fine now. 
 
Big Thanks to all who helped me on this thread. 
 
I'm away now to enjoy ubuntu.:D

---

### Post by Quackers on 2011-10-10
Glad to hear that Noob_Zaiboot :-) I'd still like to know why grub didn't install! Very strange.

Hakunka-Matata, I understand ;)

---

