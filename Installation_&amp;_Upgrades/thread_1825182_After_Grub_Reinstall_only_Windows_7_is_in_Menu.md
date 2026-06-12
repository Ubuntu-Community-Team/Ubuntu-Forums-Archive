---
title: "After Grub Reinstall only Windows 7 is in Menu"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by green112 on 2011-08-14
Hi guys. I have a questioon that I can't find the answer to after a week of reading and trying many things.

I was triple booting windows 7 with ubuntu and fedora. Took me a long time to get them installed correctly, those live CDs are very unreliable, after downloading many copies and burning to both cd and dvd, very unreliable.

But my question is this.

I had them booting fine until I ran a grub update and windows 7 disappeared. I tried many things to get it back but in the end gave up and reinstalled it. Doing that caused grub to disappear and windows 7 to boot automatically as expected.
So I ran the ubuntu live cd, reinstalled grub and rebooted. Now grub appears but only shows windows 7, no other operating systems.
I have read and tried many things on here about how to fix it but none work.
I have downloaded boot repair from the live cd but that doesn't work, tried statrup mnager, and tried quite a number of different commands in the terminal that I cannot remember now.

So basically the situation is: After a reinstall of grub, only windows 7 shows in the grub menu. I cannot find anyway to get Ubuntu and fedora back into the grub menu. So if anyone has any ideas please help.

Thank you.

---

### Post by garvinrick4 on 2011-08-14
I would imagine that all three operating systems have a different boot manager.
The one you need to be in charge is Ubuntu's grub2 not fedora's grub legacy and Windows boot manager will only boot windows. 
It can be done with a Ubuntu live cd and code to put in a terminal. First download this script to DESKTOP.  Make sure it is on Desktop:
then follow easy instructions below.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
                                 [FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Open a Terminal and use these four commands one at a time. copy and paste:[/SIZE][/FONT]
 ```
cd Desktop
``` ```
unzip boot_info_script060.zip
``` ```
chmod +x boot_info_script.sh
``` ```
sudo ./boot_info_script.sh
``` [FONT=Times New Roman][SIZE=3]There will now be a file called RESULTS  on Desktop copy and paste to this Thread:[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Use code tags and will be easier to read: (Highlight all text after pasting and click on # sign in upper right of message box)[/SIZE][/FONT]

---

### Post by garvinrick4 on 2011-08-14
If the above post is to difficult to understand for a new user please let me know.

---

### Post by green112 on 2011-08-14
Thank you.

There's only one way to learn and that's by doing.

I've just booted into the live cd and have started by downloading the sourceforge file. It's saved in the archive manager.
I have ran 'cd Desktop' successfully but the next bit, the unzipping cannot complete.

This is the terminal readout:

ubuntu@ubuntu:~$ cd desktop
bash: cd: desktop: No such file or directory
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ unzip boot_info_script060.zip
unzip:  cannot find or open boot_info_script060.zip, boot_info_script060.zip.zip or boot_info_script060.zip.ZIP.
ubuntu@ubuntu:~/Desktop$ 

I'm guessing I haven't got the file saved in the correct location?

Thanks again.

---

### Post by garvinrick4 on 2011-08-14
Right it just has to be on the Desktop so look in Downloads or where ever you normally
download things to and find it and drag and drop it to Desktop and all else should run fine.

##Notice the first command is "cd Desktop" that means the file has to be on Desktop because
we are changing directories to Desktop "cd Desktop.
If it was in Downloads we could start by going 'cd Downloads" and then we could finish the other
three commands because we are in the same Directory as what we want to run. 
If it was in Documents we could start commands with "cd Documents" get it. Just be in same directory
as the file we want to work with.
I choose just to have users download to DESKTOP and if not downloaded to desktop can drag and drop there after download.
Users with Boot or grub problems tend to be new linux users or new to grub usage.

---

### Post by green112 on 2011-08-14
I just had a look at the file in the archive manager, in the title it says read only. That may be the problem.

---

### Post by green112 on 2011-08-14
> **garvinrick4 said:**
> Right it just has to be on the Desktop so look in Downloads or where ever you normally
download things to and find it and drag and drop it to Desktop and all else should run fine.
Sorry, didn't see this message. 

Doing it now.

---

### Post by green112 on 2011-08-14
```
    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
```

---

### Post by garvinrick4 on 2011-08-14
Ok you did it, now copy and paste the whole thing it should be quite long I can then tell
what you have to do to boot.

---

### Post by green112 on 2011-08-14
Sorry, thought that was it all, I didn't see the rest. 

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'swsuspend'

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.conf

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,804,094   337,922,047   133,117,954   5 Extended
/dev/sda5         204,804,096   206,032,895     1,228,800  83 Linux
/dev/sda6         206,034,944   226,514,943    20,480,000  83 Linux
/dev/sda7         226,516,992   318,676,991    92,160,000  83 Linux
/dev/sda8         318,679,040   322,775,039     4,096,000  83 Linux
/dev/sda9         322,777,088   337,922,047    15,144,960  82 Linux swap / Solaris
/dev/sda3         337,922,048   338,946,047     1,024,000  83 Linux
/dev/sda4         338,946,048   482,306,047   143,360,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   102,402,047   102,400,000  83 Linux
/dev/sdb2         102,402,048   106,498,047     4,096,000  83 Linux
/dev/sdb3         106,498,048   488,275,967   381,777,920   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BA4845F04845AC47                       ntfs       
/dev/sda3        b3db49c2-cd8b-41f1-ac5b-a79690f8a83a   ext4       
/dev/sda4        e5435277-e193-4250-998c-40a5bffd128e   ext4       _Fedora-15-x86_6
/dev/sda5        cf743064-2410-46f5-aa11-91728555f14d   ext4       
/dev/sda6        5ce62fbe-4a8e-4029-93af-6943f3f630a9   ext4       
/dev/sda7        becb6216-c60e-45ce-81a5-26c21952dfca   ext4       
/dev/sda8        e8c85ae4-d574-4fe5-acd2-6aa97fbd905e   ext4       
/dev/sda9        22873e76-7e70-4a35-994b-c491435d45a0   swsuspend  swap
/dev/sdb1        790f87ca-0115-4d9f-a021-885e78a9b82f   ext4       
/dev/sdb2        1faa571b-c173-499c-81c3-4c486fc44c8c   ext4       
/dev/sdb3        DEC23899C23877BB                       ntfs       Windows Backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 1101DC963B1A55AF
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

  97.795089722 = 105.006678016  grub/core.img                                  1
  97.824226379 = 105.037963264  grub/grub.cfg                                  1
  97.850166321 = 105.065816064  initrd.img-2.6.38-10-generic                   1
  97.811065674 = 105.023832064  initrd.img-2.6.38-8-generic                    1
  97.818672180 = 105.031999488  vmlinuz-2.6.38-10-generic                      1
  97.791263580 = 105.002569728  vmlinuz-2.6.38-8-generic                       1

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA4845F04845AC47
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
UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=cf743064-2410-46f5-aa11-91728555f14d /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=becb6216-c60e-45ce-81a5-26c21952dfca /home           ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=e8c85ae4-d574-4fe5-acd2-6aa97fbd905e /tmp            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=22873e76-7e70-4a35-994b-c491435d45a0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 102.569133759 = 110.132768768  boot/grub/core.img                             1
 102.564800262 = 110.128115712  boot/grub/grub.cfg                             1

============================= sda3/grub/grub.conf: =============================

--------------------------------------------------------------------------------
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/sda4
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.40-4.fc15.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.40-4.fc15.x86_64 ro root=UUID=e5435277-e193-4250-998c-40a5bffd128e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.40-4.fc15.x86_64.img
title Fedora (2.6.38.6-26.rc1.fc15.x86_64)
    root (hd0,2)
    kernel /vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 ro root=UUID=e5435277-e193-4250-998c-40a5bffd128e rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
title Other
    rootnoverify (hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 161.155276299 = 173.039160320  grub/grub.conf                                 2
 161.155276299 = 173.039160320  grub/menu.lst                                  2
 161.148504257 = 173.031888896  grub/stage2                                    1
 161.164980888 = 173.049580544  initramfs-2.6.38.6-26.rc1.fc15.x86_64.img      2
 161.194789886 = 173.081587712  initramfs-2.6.40-4.fc15.x86_64.img             2
 161.142071724 = 173.024982016  initrd-plymouth.img                            1
 161.145948410 = 173.029144576  vmlinuz-2.6.38.6-26.rc1.fc15.x86_64            1
 161.171101570 = 173.056152576  vmlinuz-2.6.40-4.fc15.x86_64                   1

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sun Aug  7 01:52:35 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e5435277-e193-4250-998c-40a5bffd128e /                       ext4    defaults        1 1
UUID=b3db49c2-cd8b-41f1-ac5b-a79690f8a83a /boot                   ext4    defaults        1 2
UUID=790f87ca-0115-4d9f-a021-885e78a9b82f /home                   ext4    defaults        1 2
UUID=1faa571b-c173-499c-81c3-4c486fc44c8c /tmp                    ext4    defaults        1 2
UUID=22873e76-7e70-4a35-994b-c491435d45a0 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```

---

### Post by garvinrick4 on 2011-08-14
You do seem to have grub files in a lot of partitions:
sda3 has the fedora boot files, /boot partion
sda5 has grub files no operating system. /boot/partition
sda9 unknown to me says swap but awful big.

sda6 has ubuntu 11.04 file system
sda4 has fedora 15 no boot files that is ok we will use grub2 in Ubuntu to boot.


## Ok put in a live cd and copy and paste these in a terminal.
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --boot-directory=/mnt/boot /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Now boot into Ubuntu and open a terminal and:
```
sudo update-grub
```Should put Windows and fedora in as menuentry and in grub config file and then you can
clean up partitions that are not in use when you want.
Let me know how it comes out.

---

### Post by green112 on 2011-08-14
I've tried what you say twice and everything seems to complete ok but after reboot it still only shows windows 7. I've tried the grub update comand just now from within the live CD but it says 

```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
ubuntu@ubuntu:~$ 
```


this code does nothing after I run it. Is that normal?
```
sudo umount /mnt
```

---

### Post by garvinrick4 on 2011-08-14
OK I will give you more commands in live cd, just a second.
Hold down shift while is booting into hard drive does it show a grub menu?

## cannot update-grub in live cd unless use different type of mounting.
# Yes, nothing after sudo umount /mnt is good.

---

### Post by green112 on 2011-08-14
Sorry, this command also does nothing after I enter it:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$
```Here is the entire terminal readout:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$
```Next thing to do is enter the reboot comand, but I've done that twice and it didn't work.

---

### Post by green112 on 2011-08-14
There is no ubuntu in the grub for me to boot into after the reboot, still only windows 7.

---

### Post by green112 on 2011-08-14
This may or may not be of help... On the grub screen it says window 7 (on /dev /sda1)

---

### Post by garvinrick4 on 2011-08-14
Ok in a live CD copy and paste these two are long.
```
sudo mkdir /mnt/boot
``````
sudo mount /dev/sda6 /mnt && sudo mount /dev/sda5 /mnt/boot && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt  
 
``````
grub-install /dev/sda
``````
update-grub
``````

sudo umount /mnt/boot && sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt

```Now reboot and hopefully Ubuntu. 
##New code including /boot in sda5

---

### Post by green112 on 2011-08-14
Sorry, I keep trying those commands and rebooting and I'm missing your messages, that why I keep posting :) 

I just tried holding shift while booting into hard drives. Nothing but the same grub screen with only Windows

---

### Post by green112 on 2011-08-14
Gonna try the latest commands now. Thanks.

---

### Post by garvinrick4 on 2011-08-14
> Here is the entire terminal readout:
 	Code:
 	ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/mnt/boot /dev/sda Installation finished. No error reported. ubuntu@ubuntu:~$ sudo umount /mnt ubuntu@ubuntu:~$ 
Next thing to do is enter the reboot comand, but I've done that twice and it didn't 
work.
That all looked good to me The only thing is if you have grub 1.98 instead of 1.99 and that is a different piece of code. The previous post of instructions should cure that.

---

### Post by green112 on 2011-08-14
OK I just ran that last code. I'm gonna reboot now and let you no what happened but before I do I want to post the terminal readout.

Seems like it has found Fedora and Win7 but no Ubuntu. I'll reboot now and let you no what has happened. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
root@ubuntu:/# sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
sudo: unable to resolve host ubuntu
umount: /mnt/dev/pts: not found
root@ubuntu:/# 
```

---

### Post by green112 on 2011-08-14
Ok I just rebooted. After that terminal readout I thought it would have atleast had decorative in grub with win 7 now but it didn't.

Upon reboot grub still on had win 7 present, nothing else.

---

### Post by green112 on 2011-08-14
> **green112 said:**
> Ok I just rebooted. After that terminal readout I thought it would have atleast had decorative in grub with win 7 now but it didn't.

Upon reboot grub still on had win 7 present, nothing else.
Decorative is fedora... Predictive text on my phone got it wrong.

---

### Post by garvinrick4 on 2011-08-14
:Looks like we got Windows and Fedora in there now.
Let me know, I just noticed that sda5 was set up as a boot partition for ubuntu
and fedora has a seperate boot partition also. At least I see why now. If does not
boot we have to get rid of or mount at install of grub.

---

### Post by green112 on 2011-08-14
> **garvinrick4 said:**
> :Looks like we got Windows and Fedora in there now.
Let me know, I just noticed that sda5 was set up as a boot partition for ubuntu
and fedora has a seperate boot partition also. At least I see why now. If does not
boot we have to get rid of or mount at install of grub.
No fedora... Still only windows.

---

### Post by garvinrick4 on 2011-08-14
Ok Ubuntu and fedora both have /boot partitions Ubuntu is sda5 and fedora sda3 I believe
I have to look again. I have to think rather to just delete the 2 boot partitions or use them
which is not normal. There is no need for the /boot partitions. Grub is where it is suppose
to be and making a config file but the /boot partitions want to be mounted when installing
grub. Let me think one minute. Be right back.

---

### Post by green112 on 2011-08-15
Yes, I gave each os it's own boot partition. I thought that was how it was supposed to be :(

When it did triple boot for me, it first showed the fedora boot screen with fedora 15 and 'other' ... 'Other' would take me to the Ubuntu grub2 screen with two kernel versions of ubuntu in it plus win 7.

The fedora grub was on a far back partition of the drive and the ununtu boot i think was initially sda1... "I think' not 100% sure.

---

### Post by garvinrick4 on 2011-08-15
Ok going to add a couple of lines of code to the last string of code I gave you to mount
sda5 also and that should pick up Ubuntu if not we will delete it all together.
Run the code in the Live Cd and let me know.

---

### Post by garvinrick4 on 2011-08-15
Ok post #17 I changed to include the /boot partition is sda5 lets give her a whirl. let me know. We will get this right.

---

### Post by green112 on 2011-08-15
OK, here's the terminal readout before I reboot. Found I few more things this time. Rebooting now, will let you know how it goes.

```
ubuntu@ubuntu:~$ sudo mkdir /mnt/boot
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount /dev/sda5 /mnt/boot && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
root@ubuntu:/# sudo umount /mnt/boot && sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
sudo: unable to resolve host ubuntu
umount: /mnt/boot: not found
root@ubuntu:/# 
```

---

### Post by garvinrick4 on 2011-08-15
Looks like that should do it. reboot and choose ubuntu.

---

### Post by garvinrick4 on 2011-08-15
> **green112 said:**
> Yes, I gave each os it's own boot partition. I thought that was how it was supposed to be :(

When it did triple boot for me, it first showed the fedora boot screen with fedora 15 and 'other' ... 'Other' would take me to the Ubuntu grub2 screen with two kernel versions of ubuntu in it plus win 7.

The fedora grub was on a far back partition of the drive and the ununtu boot i think was initially sda1... "I think' not 100% sure. If was working with 3 different types of
grub at one time so it was OK.

---

### Post by green112 on 2011-08-15
Ok, worked great except it cannot find fedora.

Upon first reboot the grub menu had current versions of Ubuntu plus previous kernel versions of ubuntu plus both mem tests and win7.

I first booted into ubnuntu but it failed, showed a corrupted ubuntu live cd screen with an error saying ubiquity failed. But I rebooted and ubuntu did a disk check the next time I booted it and it worked fine. Booted into it a few times to check it and it's working fine now. Windows is still working fine too as are the other kernels, booted them all just to be sure.

Like I say the only thing not right yet is it can't find fedora.

---

### Post by garvinrick4 on 2011-08-15
Yea I figured that it has its own /boot partition also with a different version of grub.
grub-legacy which I am going to think lets get rid of the /boot partition for fedora and
let Ubuntu's grub2 find fedora's operating system. Will only be able to boot from Ubuntu's
grub into all three Operating Systems but that is cool. Does that sound Ok to you.

---

### Post by green112 on 2011-08-15
Sounds perfect. Will be glad to have them all working again :)

Thank you very much for the help.

---

### Post by garvinrick4 on 2011-08-15
You are welcome but lets hope we can get Grub2 to find Fedora. Going to remove
fedoras /boot partition and see if grub2 will point to fedora instead of its boot partition.
Should not need any boot files because Ubuntu is going to handle. Anyway when I use
anaconda installer (fedora's installer) I just choose not to install grub at install and then
update-grub in Ubuntu after installing fedora and all is fine: So lets go.

In a live cd open a package called gparted 
Right click on sda3 and delete that partition:
Then hit apply arrow on top. Should make it unallocated space.
Close gparted and reboot into Ubuntu on Hard drive and:
```
sudo update-grub
```Should pick up fedora and can reboot into Windows, Ubuntu or Fedora.
Make sure you focus while using gparted it is a partition tool and powerful, do not
want to delete anything except sda3. 
Hope this solves it now for all 3 installs.

---

### Post by green112 on 2011-08-15
1

---

### Post by green112 on 2011-08-15
Ok partition has been deleted, terminal commands entered but no fedora in menu.

Here's the terminal output:
```

stephen@stephen-Dell-DXP061:~$ sudo update-grub
[sudo] password for stephen: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$ 
```

I've rebooted twice but no fedora.

---

### Post by garvinrick4 on 2011-08-15
Shows Fedora but not there:
```
grep menuentry /boot/grub/grub.cfg
```
Run that in Ubuntu and see if fedora is listed in there;

---

### Post by green112 on 2011-08-15
No it isn't there.

```
stephen@stephen-Dell-DXP061:~$ grep menuentry /boot/grub/grub.cfg
[COLOR=DarkRed]menuentry[/COLOR] 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
[COLOR=DarkRed]menuentry[/COLOR] 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
[COLOR=DarkRed]menuentry[/COLOR] 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
[COLOR=DarkRed]menuentry[/COLOR] 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
[COLOR=DarkRed]menuentry[/COLOR] "Memory test (memtest86+)" {
[COLOR=DarkRed]menuentry[/COLOR] "Memory test (memtest86+, serial console 115200)" {
[COLOR=DarkRed]menuentry[/COLOR] "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by garvinrick4 on 2011-08-15
Lets see if it will update from chroot still . Can use cd or ubuntu install. If both the same 32 or 64 bit. Make sure internet is working.
                          ```
sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt  
 
``````
yum update
```     ```
exit
```                      ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
 

```

---

### Post by green112 on 2011-08-15
Thank you, rebooting now.

Terminal readout:
```

stephen@stephen-Dell-DXP061:~$ sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for stephen: 
bash-4.2# yum update
Loaded plugins: langpacks, presto, refresh-packagekit
adobe-linux-i386                                         |  951 B     00:00     
adobe-linux-i386/primary                                 |  12 kB     00:00     
fedora/metalink                                          |  32 kB     00:00     
updates/metalink                                         |  28 kB     00:00     
updates                                                  | 4.7 kB     00:00     
updates/primary_db                                       | 3.9 MB     00:03     
adobe-linux-i386                                                          18/18
Setting up Update Process
Resolving Dependencies
--> Running transaction check
---> Package PackageKit.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-command-not-found.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-command-not-found.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-device-rebind.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-device-rebind.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-glib.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-glib.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-gstreamer-plugin.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-gstreamer-plugin.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-gtk-module.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-gtk-module.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-gtk3-module.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-gtk3-module.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-yum.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-yum.x86_64 0:0.6.17-1.fc15 will be an update
---> Package PackageKit-yum-plugin.x86_64 0:0.6.16-1.fc15 will be updated
---> Package PackageKit-yum-plugin.x86_64 0:0.6.17-1.fc15 will be an update
---> Package bind-libs.x86_64 32:9.8.0-7.P4.fc15 will be updated
---> Package bind-libs.x86_64 32:9.8.0-9.P4.fc15 will be an update
---> Package bind-libs-lite.x86_64 32:9.8.0-7.P4.fc15 will be updated
---> Package bind-libs-lite.x86_64 32:9.8.0-9.P4.fc15 will be an update
---> Package bind-license.noarch 32:9.8.0-7.P4.fc15 will be updated
---> Package bind-license.noarch 32:9.8.0-9.P4.fc15 will be an update
---> Package bind-utils.x86_64 32:9.8.0-7.P4.fc15 will be updated
---> Package bind-utils.x86_64 32:9.8.0-9.P4.fc15 will be an update
---> Package cifs-utils.x86_64 0:5.0-1.fc15 will be updated
---> Package cifs-utils.x86_64 0:5.0-2.fc15 will be an update
---> Package curl.x86_64 0:7.21.3-8.fc15 will be updated
---> Package curl.x86_64 0:7.21.3-9.fc15 will be an update
---> Package glibc.x86_64 0:2.14-4 will be updated
---> Package glibc.x86_64 0:2.14-5 will be an update
---> Package glibc-common.x86_64 0:2.14-4 will be updated
---> Package glibc-common.x86_64 0:2.14-5 will be an update
---> Package ibus.x86_64 0:1.3.99.20110419-12.fc15 will be updated
---> Package ibus.x86_64 0:1.3.99.20110419-13.fc15 will be an update
---> Package ibus-gtk2.x86_64 0:1.3.99.20110419-12.fc15 will be updated
---> Package ibus-gtk2.x86_64 0:1.3.99.20110419-13.fc15 will be an update
---> Package ibus-gtk3.x86_64 0:1.3.99.20110419-12.fc15 will be updated
---> Package ibus-gtk3.x86_64 0:1.3.99.20110419-13.fc15 will be an update
---> Package ibus-hangul.x86_64 0:1.3.1-3.fc15 will be updated
---> Package ibus-hangul.x86_64 0:1.3.1-6.fc15 will be an update
---> Package ibus-libs.x86_64 0:1.3.99.20110419-12.fc15 will be updated
---> Package ibus-libs.x86_64 0:1.3.99.20110419-13.fc15 will be an update
---> Package ibus-pinyin.x86_64 0:1.3.99.20110520-1.fc15 will be updated
---> Package ibus-pinyin.x86_64 0:1.3.99.20110706-2.fc15 will be an update
---> Package ibus-pinyin-db-android.noarch 0:1.3.99.20110520-1.fc15 will be updated
---> Package ibus-pinyin-db-android.noarch 0:1.3.99.20110706-2.fc15 will be an update
---> Package libcurl.x86_64 0:7.21.3-8.fc15 will be updated
---> Package libcurl.x86_64 0:7.21.3-9.fc15 will be an update
---> Package lm_sensors-libs.x86_64 0:3.3.0-2.fc15 will be updated
---> Package lm_sensors-libs.x86_64 0:3.3.1-1.fc15 will be an update
---> Package logrotate.x86_64 0:3.7.9-13.fc15 will be updated
---> Package logrotate.x86_64 0:3.7.9-14.fc15 will be an update
---> Package mesa-dri-drivers.x86_64 0:7.11-0.16.20110709.0.fc15 will be updated
---> Package mesa-dri-drivers.x86_64 0:7.11-1.fc15 will be an update
--> Processing Dependency: libLLVM-2.8.so()(64bit) for package: mesa-dri-drivers-7.11-1.fc15.x86_64
---> Package mesa-dri-filesystem.x86_64 0:7.11-0.16.20110709.0.fc15 will be updated
---> Package mesa-dri-filesystem.x86_64 0:7.11-1.fc15 will be an update
---> Package mesa-libGL.x86_64 0:7.11-0.16.20110709.0.fc15 will be updated
---> Package mesa-libGL.x86_64 0:7.11-1.fc15 will be an update
---> Package mesa-libGLU.x86_64 0:7.11-0.16.20110709.0.fc15 will be updated
---> Package mesa-libGLU.x86_64 0:7.11-1.fc15 will be an update
---> Package perl.x86_64 4:5.12.4-159.fc15 will be updated
---> Package perl.x86_64 4:5.12.4-160.fc15 will be an update
---> Package perl-Module-Pluggable.noarch 1:3.90-159.fc15 will be updated
---> Package perl-Module-Pluggable.noarch 1:3.90-160.fc15 will be an update
---> Package perl-Pod-Escapes.noarch 1:1.04-159.fc15 will be updated
---> Package perl-Pod-Escapes.noarch 1:1.04-160.fc15 will be an update
---> Package perl-Pod-Simple.noarch 1:3.13-159.fc15 will be updated
---> Package perl-Pod-Simple.noarch 1:3.13-160.fc15 will be an update
---> Package perl-libs.x86_64 4:5.12.4-159.fc15 will be updated
---> Package perl-libs.x86_64 4:5.12.4-160.fc15 will be an update
---> Package ql2500-firmware.noarch 0:5.03.16-1.fc15 will be updated
---> Package ql2500-firmware.noarch 0:5.06.00-1.fc15 will be an update
---> Package shadow-utils.x86_64 2:4.1.4.2-12.fc15 will be updated
---> Package shadow-utils.x86_64 2:4.1.4.2-13.fc15 will be an update
---> Package system-config-printer.x86_64 0:1.3.3-1.fc15 will be updated
---> Package system-config-printer.x86_64 0:1.3.5-3.fc15 will be an update
---> Package system-config-printer-libs.x86_64 0:1.3.3-1.fc15 will be updated
---> Package system-config-printer-libs.x86_64 0:1.3.5-3.fc15 will be an update
---> Package system-config-printer-udev.x86_64 0:1.3.3-1.fc15 will be updated
---> Package system-config-printer-udev.x86_64 0:1.3.5-3.fc15 will be an update
---> Package vlgothic-fonts.noarch 0:20110414-1.fc15 will be updated
---> Package vlgothic-fonts.noarch 0:20110722-1.fc15 will be an update
---> Package vlgothic-fonts-common.noarch 0:20110414-1.fc15 will be updated
---> Package vlgothic-fonts-common.noarch 0:20110722-1.fc15 will be an update
---> Package wget.x86_64 0:1.12-3.fc15 will be updated
---> Package wget.x86_64 0:1.12-4.fc15 will be an update
--> Running transaction check
---> Package llvm-libs.x86_64 0:2.8-11.fc15 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package                       Arch    Version                   Repository
                                                                           Size
================================================================================
Updating:
 PackageKit                    x86_64  0.6.17-1.fc15             updates  563 k
 PackageKit-command-not-found  x86_64  0.6.17-1.fc15             updates   46 k
 PackageKit-device-rebind      x86_64  0.6.17-1.fc15             updates   36 k
 PackageKit-glib               x86_64  0.6.17-1.fc15             updates  138 k
 PackageKit-gstreamer-plugin   x86_64  0.6.17-1.fc15             updates   36 k
 PackageKit-gtk-module         x86_64  0.6.17-1.fc15             updates   35 k
 PackageKit-gtk3-module        x86_64  0.6.17-1.fc15             updates   35 k
 PackageKit-yum                x86_64  0.6.17-1.fc15             updates  101 k
 PackageKit-yum-plugin         x86_64  0.6.17-1.fc15             updates   32 k
 bind-libs                     x86_64  32:9.8.0-9.P4.fc15        updates  842 k
 bind-libs-lite                x86_64  32:9.8.0-9.P4.fc15        updates  611 k
 bind-license                  noarch  32:9.8.0-9.P4.fc15        updates   67 k
 bind-utils                    x86_64  32:9.8.0-9.P4.fc15        updates  178 k
 cifs-utils                    x86_64  5.0-2.fc15                updates   45 k
 curl                          x86_64  7.21.3-9.fc15             updates  227 k
 glibc                         x86_64  2.14-5                    updates  3.3 M
 glibc-common                  x86_64  2.14-5                    updates   11 M
 ibus                          x86_64  1.3.99.20110419-13.fc15   updates  393 k
 ibus-gtk2                     x86_64  1.3.99.20110419-13.fc15   updates   30 k
 ibus-gtk3                     x86_64  1.3.99.20110419-13.fc15   updates   30 k
 ibus-hangul                   x86_64  1.3.1-6.fc15              updates   42 k
 ibus-libs                     x86_64  1.3.99.20110419-13.fc15   updates  134 k
 ibus-pinyin                   x86_64  1.3.99.20110706-2.fc15    updates  501 k
 ibus-pinyin-db-android        noarch  1.3.99.20110706-2.fc15    updates  950 k
 libcurl                       x86_64  7.21.3-9.fc15             updates  183 k
 lm_sensors-libs               x86_64  3.3.1-1.fc15              updates   36 k
 logrotate                     x86_64  3.7.9-14.fc15             updates   57 k
 mesa-dri-drivers              x86_64  7.11-1.fc15               updates  9.5 M
 mesa-dri-filesystem           x86_64  7.11-1.fc15               updates   20 k
 mesa-libGL                    x86_64  7.11-1.fc15               updates  130 k
 mesa-libGLU                   x86_64  7.11-1.fc15               updates  173 k
 perl                          x86_64  4:5.12.4-160.fc15         updates   11 M
 perl-Module-Pluggable         noarch  1:3.90-160.fc15           updates   40 k
 perl-Pod-Escapes              noarch  1:1.04-160.fc15           updates   33 k
 perl-Pod-Simple               noarch  1:3.13-160.fc15           updates  210 k
 perl-libs                     x86_64  4:5.12.4-160.fc15         updates  594 k
 ql2500-firmware               noarch  5.06.00-1.fc15            updates  110 k
 shadow-utils                  x86_64  2:4.1.4.2-13.fc15         updates  869 k
 system-config-printer         x86_64  1.3.5-3.fc15              updates  268 k
 system-config-printer-libs    x86_64  1.3.5-3.fc15              updates  856 k
 system-config-printer-udev    x86_64  1.3.5-3.fc15              updates   81 k
 vlgothic-fonts                noarch  20110722-1.fc15           updates  2.1 M
 vlgothic-fonts-common         noarch  20110722-1.fc15           updates   16 k
 wget                          x86_64  1.12-4.fc15               updates  478 k
Installing for dependencies:
 llvm-libs                     x86_64  2.8-11.fc15               fedora   4.9 M

Transaction Summary
================================================================================
Install       1 Package(s)
Upgrade      44 Package(s)

Total download size: 51 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
updates/prestodelta                                      | 645 kB     00:00     
fedora/prestodelta                                       | 2.5 MB     00:03     
Processing delta metadata
Download delta size: 16 M
(1/39): PackageKit-0.6.16-1.fc15_0.6.17-1.fc15.x86_64.dr | 188 kB     00:00     
(2/39): PackageKit-glib-0.6.16-1.fc15_0.6.17-1.fc15.x86_ |  40 kB     00:00     
(3/39): PackageKit-gtk-module-0.6.16-1.fc15_0.6.17-1.fc1 |  31 kB     00:00     
(4/39): PackageKit-gtk3-module-0.6.16-1.fc15_0.6.17-1.fc |  31 kB     00:00     
(5/39): PackageKit-yum-0.6.16-1.fc15_0.6.17-1.fc15.x86_6 |  35 kB     00:00     
(6/39): bind-libs-9.8.0-7.P4.fc15_9.8.0-9.P4.fc15.x86_64 |  69 kB     00:00     
(7/39): bind-libs-lite-9.8.0-7.P4.fc15_9.8.0-9.P4.fc15.x |  68 kB     00:00     
(8/39): bind-utils-9.8.0-7.P4.fc15_9.8.0-9.P4.fc15.x86_6 |  68 kB     00:00     
(9/39): cifs-utils-5.0-1.fc15_5.0-2.fc15.x86_64.drpm     |  32 kB     00:00     
(10/39): curl-7.21.3-8.fc15_7.21.3-9.fc15.x86_64.drpm    | 104 kB     00:00     
(11/39): glibc-2.14-4_2.14-5.x86_64.drpm                 | 586 kB     00:00     
(12/39): glibc-common-2.14-4_2.14-5.x86_64.drpm          |  10 MB     00:09     
(13/39): ibus-1.3.99.20110419-12.fc15_1.3.99.20110419-13 | 165 kB     00:00     
(14/39): ibus-gtk2-1.3.99.20110419-12.fc15_1.3.99.201104 |  21 kB     00:00     
(15/39): ibus-gtk3-1.3.99.20110419-12.fc15_1.3.99.201104 |  21 kB     00:00     
(16/39): ibus-hangul-1.3.1-3.fc15_1.3.1-6.fc15.x86_64.dr |  20 kB     00:00     
(17/39): ibus-libs-1.3.99.20110419-12.fc15_1.3.99.201104 |  45 kB     00:00     
(18/39): ibus-pinyin-1.3.99.20110520-1.fc15_1.3.99.20110 | 104 kB     00:00     
(19/39): ibus-pinyin-db-android-1.3.99.20110520-1.fc15_1 | 7.8 kB     00:00     
(20/39): libcurl-7.21.3-8.fc15_7.21.3-9.fc15.x86_64.drpm |  44 kB     00:00     
(21/39): lm_sensors-libs-3.3.0-2.fc15_3.3.1-1.fc15.x86_6 |  15 kB     00:00     
(22/39): logrotate-3.7.9-13.fc15_3.7.9-14.fc15.x86_64.dr |  42 kB     00:00     
(23/39): mesa-dri-drivers-7.11-0.16.20110709.0.fc15_7.11 | 1.2 MB     00:02     
(24/39): mesa-dri-filesystem-7.11-0.16.20110709.0.fc15_7 |  11 kB     00:00     
(25/39): mesa-libGL-7.11-0.16.20110709.0.fc15_7.11-1.fc1 |  17 kB     00:00     
(26/39): mesa-libGLU-7.11-0.16.20110709.0.fc15_7.11-1.fc |  12 kB     00:00     
(27/39): perl-5.12.4-159.fc15_5.12.4-160.fc15.x86_64.drp | 668 kB     00:01     
(28/39): perl-Module-Pluggable-3.90-159.fc15_3.90-160.fc |  24 kB     00:00     
(29/39): perl-Pod-Escapes-1.04-159.fc15_1.04-160.fc15.no |  23 kB     00:00     
(30/39): perl-Pod-Simple-3.13-159.fc15_3.13-160.fc15.noa |  32 kB     00:00     
(31/39): perl-libs-5.12.4-159.fc15_5.12.4-160.fc15.x86_6 |  24 kB     00:00     
(32/39): ql2500-firmware-5.03.16-1.fc15_5.06.00-1.fc15.n |  35 kB     00:00     
(33/39): shadow-utils-4.1.4.2-12.fc15_4.1.4.2-13.fc15.x8 | 236 kB     00:01     
(34/39): system-config-printer-1.3.3-1.fc15_1.3.5-3.fc15 | 100 kB     00:00     
(35/39): system-config-printer-libs-1.3.3-1.fc15_1.3.5-3 | 499 kB     00:01     
(36/39): system-config-printer-udev-1.3.3-1.fc15_1.3.5-3 |  75 kB     00:00     
(37/39): vlgothic-fonts-20110414-1.fc15_20110722-1.fc15. | 466 kB     00:00     
(38/39): vlgothic-fonts-common-20110414-1.fc15_20110722- | 9.8 kB     00:00     
(39/39): wget-1.12-3.fc15_1.12-4.fc15.x86_64.drpm        | 181 kB     00:00     
Finishing rebuild of rpms, from deltarpms
<delta rebuild>                                          |  45 MB     00:29     
Presto reduced the update size by 66% (from 45 M to 16 M).
Package(s) data still to download: 5.1 M
(1/6): PackageKit-command-not-found-0.6.17-1.fc15.x86_64 |  46 kB     00:00     
(2/6): PackageKit-device-rebind-0.6.17-1.fc15.x86_64.rpm |  36 kB     00:00     
(3/6): PackageKit-gstreamer-plugin-0.6.17-1.fc15.x86_64. |  36 kB     00:00     
(4/6): PackageKit-yum-plugin-0.6.17-1.fc15.x86_64.rpm    |  32 kB     00:00     
(5/6): bind-license-9.8.0-9.P4.fc15.noarch.rpm           |  67 kB     00:00     
(6/6): llvm-libs-2.8-11.fc15.x86_64.rpm                  | 4.9 MB     00:07     
--------------------------------------------------------------------------------
Total                                           611 kB/s | 5.1 MB     00:08     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Updating   : glibc-common-2.14-5.x86_64                                  1/89 
  Updating   : glibc-2.14-5.x86_64                                         2/89 
  Updating   : ibus-libs-1.3.99.20110419-13.fc15.x86_64                    3/89 
  Updating   : ibus-gtk2-1.3.99.20110419-13.fc15.x86_64                    4/89 
  Updating   : ibus-1.3.99.20110419-13.fc15.x86_64                         5/89 
  Updating   : ibus-gtk3-1.3.99.20110419-13.fc15.x86_64                    6/89 
  Updating   : PackageKit-yum-0.6.17-1.fc15.x86_64                         7/89 
  Updating   : PackageKit-0.6.17-1.fc15.x86_64                             8/89 
  Updating   : PackageKit-glib-0.6.17-1.fc15.x86_64                        9/89 
  Updating   : system-config-printer-libs-1.3.5-3.fc15.x86_64             10/89 
  Updating   : 32:bind-license-9.8.0-9.P4.fc15.noarch                     11/89 
  Updating   : 32:bind-libs-9.8.0-9.P4.fc15.x86_64                        12/89 
  Updating   : mesa-libGL-7.11-1.fc15.x86_64                              13/89 
  Updating   : libcurl-7.21.3-9.fc15.x86_64                               14/89 
  Installing : llvm-libs-2.8-11.fc15.x86_64                               15/89 
  Updating   : 1:perl-Pod-Escapes-1.04-160.fc15.noarch                    16/89 
  Updating   : 4:perl-libs-5.12.4-160.fc15.x86_64                         17/89 
  Updating   : 1:perl-Pod-Simple-3.13-160.fc15.noarch                     18/89 
  Updating   : 1:perl-Module-Pluggable-3.90-160.fc15.noarch               19/89 
  Updating   : 4:perl-5.12.4-160.fc15.x86_64                              20/89 
  Updating   : ibus-pinyin-db-android-1.3.99.20110706-2.fc15.noarch       21/89 
  Updating   : mesa-dri-filesystem-7.11-1.fc15.x86_64                     22/89 
  Updating   : vlgothic-fonts-common-20110722-1.fc15.noarch               23/89 
  Updating   : vlgothic-fonts-20110722-1.fc15.noarch                      24/89 
  Updating   : mesa-dri-drivers-7.11-1.fc15.x86_64                        25/89 
  Updating   : ibus-pinyin-1.3.99.20110706-2.fc15.x86_64                  26/89 
  Updating   : curl-7.21.3-9.fc15.x86_64                                  27/89 
  Updating   : mesa-libGLU-7.11-1.fc15.x86_64                             28/89 
  Updating   : 32:bind-utils-9.8.0-9.P4.fc15.x86_64                       29/89 
  Updating   : 32:bind-libs-lite-9.8.0-9.P4.fc15.x86_64                   30/89 
  Updating   : system-config-printer-udev-1.3.5-3.fc15.x86_64             31/89 
  Updating   : system-config-printer-1.3.5-3.fc15.x86_64                  32/89 
  Updating   : PackageKit-gstreamer-plugin-0.6.17-1.fc15.x86_64           33/89 
  Updating   : PackageKit-command-not-found-0.6.17-1.fc15.x86_64          34/89 
  Updating   : PackageKit-gtk3-module-0.6.17-1.fc15.x86_64                35/89 
  Updating   : PackageKit-device-rebind-0.6.17-1.fc15.x86_64              36/89 
  Updating   : PackageKit-gtk-module-0.6.17-1.fc15.x86_64                 37/89 
  Updating   : PackageKit-yum-plugin-0.6.17-1.fc15.x86_64                 38/89 
  Updating   : ibus-hangul-1.3.1-6.fc15.x86_64                            39/89 
  Updating   : cifs-utils-5.0-2.fc15.x86_64                               40/89 
  Updating   : logrotate-3.7.9-14.fc15.x86_64                             41/89 
  Updating   : 2:shadow-utils-4.1.4.2-13.fc15.x86_64                      42/89 
  Updating   : lm_sensors-libs-3.3.1-1.fc15.x86_64                        43/89 
  Updating   : wget-1.12-4.fc15.x86_64                                    44/89 
  Updating   : ql2500-firmware-5.06.00-1.fc15.noarch                      45/89 
  Cleanup    : 32:bind-utils-9.8.0-7.P4.fc15.x86_64                       46/89 
  Cleanup    : ibus-pinyin-1.3.99.20110520-1.fc15.x86_64                  47/89 
  Cleanup    : ibus-hangul-1.3.1-3.fc15.x86_64                            48/89 
  Cleanup    : ibus-gtk2-1.3.99.20110419-12.fc15.x86_64                   49/89 
  Cleanup    : ibus-gtk3-1.3.99.20110419-12.fc15.x86_64                   50/89 
  Cleanup    : ibus-1.3.99.20110419-12.fc15.x86_64                        51/89 
  Cleanup    : PackageKit-command-not-found-0.6.16-1.fc15.x86_64          52/89 
  Cleanup    : PackageKit-gstreamer-plugin-0.6.16-1.fc15.x86_64           53/89 
  Cleanup    : curl-7.21.3-8.fc15.x86_64                                  54/89 
  Cleanup    : mesa-libGLU-7.11-0.16.20110709.0.fc15.x86_64               55/89 
  Cleanup    : mesa-dri-drivers-7.11-0.16.20110709.0.fc15.x86_64          56/89 
  Cleanup    : 32:bind-libs-9.8.0-7.P4.fc15.x86_64                        57/89 
  Cleanup    : 32:bind-libs-lite-9.8.0-7.P4.fc15.x86_64                   58/89 
  Cleanup    : 4:perl-libs-5.12.4-159.fc15.x86_64                         59/89 
  Cleanup    : 1:perl-Pod-Escapes-1.04-159.fc15.noarch                    60/89 
  Cleanup    : 1:perl-Pod-Simple-3.13-159.fc15.noarch                     61/89 
  Cleanup    : 4:perl-5.12.4-159.fc15.x86_64                              62/89 
  Cleanup    : 1:perl-Module-Pluggable-3.90-159.fc15.noarch               63/89 
  Cleanup    : vlgothic-fonts-20110414-1.fc15.noarch                      64/89 
  Cleanup    : system-config-printer-1.3.3-1.fc15.x86_64                  65/89 
  Cleanup    : PackageKit-yum-plugin-0.6.16-1.fc15.x86_64                 66/89 
  Cleanup    : PackageKit-gtk-module-0.6.16-1.fc15.x86_64                 67/89 
  Cleanup    : PackageKit-device-rebind-0.6.16-1.fc15.x86_64              68/89 
  Cleanup    : PackageKit-gtk3-module-0.6.16-1.fc15.x86_64                69/89 
  Cleanup    : PackageKit-yum-0.6.16-1.fc15.x86_64                        70/89 
  Cleanup    : PackageKit-glib-0.6.16-1.fc15.x86_64                       71/89 
  Cleanup    : PackageKit-0.6.16-1.fc15.x86_64                            72/89 
  Cleanup    : system-config-printer-udev-1.3.3-1.fc15.x86_64             73/89 
  Cleanup    : mesa-libGL-7.11-0.16.20110709.0.fc15.x86_64                74/89 
  Cleanup    : libcurl-7.21.3-8.fc15.x86_64                               75/89 
  Cleanup    : ibus-libs-1.3.99.20110419-12.fc15.x86_64                   76/89 
  Cleanup    : wget-1.12-3.fc15.x86_64                                    77/89 
  Cleanup    : lm_sensors-libs-3.3.0-2.fc15.x86_64                        78/89 
  Cleanup    : 2:shadow-utils-4.1.4.2-12.fc15.x86_64                      79/89 
  Cleanup    : logrotate-3.7.9-13.fc15.x86_64                             80/89 
  Cleanup    : cifs-utils-5.0-1.fc15.x86_64                               81/89 
  Cleanup    : system-config-printer-libs-1.3.3-1.fc15.x86_64             82/89 
  Cleanup    : vlgothic-fonts-common-20110414-1.fc15.noarch               83/89 
  Cleanup    : 32:bind-license-9.8.0-7.P4.fc15.noarch                     84/89 
  Cleanup    : mesa-dri-filesystem-7.11-0.16.20110709.0.fc15.x86_64       85/89 
  Cleanup    : ibus-pinyin-db-android-1.3.99.20110520-1.fc15.noarch       86/89 
  Cleanup    : ql2500-firmware-5.03.16-1.fc15.noarch                      87/89 
  Cleanup    : glibc-common-2.14-4.x86_64                                 88/89 
  Cleanup    : glibc-2.14-4.x86_64                                        89/89 
Unable to connect to dbus

Dependency Installed:
  llvm-libs.x86_64 0:2.8-11.fc15                                                

Updated:
  PackageKit.x86_64 0:0.6.17-1.fc15                                             
  PackageKit-command-not-found.x86_64 0:0.6.17-1.fc15                           
  PackageKit-device-rebind.x86_64 0:0.6.17-1.fc15                               
  PackageKit-glib.x86_64 0:0.6.17-1.fc15                                        
  PackageKit-gstreamer-plugin.x86_64 0:0.6.17-1.fc15                            
  PackageKit-gtk-module.x86_64 0:0.6.17-1.fc15                                  
  PackageKit-gtk3-module.x86_64 0:0.6.17-1.fc15                                 
  PackageKit-yum.x86_64 0:0.6.17-1.fc15                                         
  PackageKit-yum-plugin.x86_64 0:0.6.17-1.fc15                                  
  bind-libs.x86_64 32:9.8.0-9.P4.fc15                                           
  bind-libs-lite.x86_64 32:9.8.0-9.P4.fc15                                      
  bind-license.noarch 32:9.8.0-9.P4.fc15                                        
  bind-utils.x86_64 32:9.8.0-9.P4.fc15                                          
  cifs-utils.x86_64 0:5.0-2.fc15                                                
  curl.x86_64 0:7.21.3-9.fc15                                                   
  glibc.x86_64 0:2.14-5                                                         
  glibc-common.x86_64 0:2.14-5                                                  
  ibus.x86_64 0:1.3.99.20110419-13.fc15                                         
  ibus-gtk2.x86_64 0:1.3.99.20110419-13.fc15                                    
  ibus-gtk3.x86_64 0:1.3.99.20110419-13.fc15                                    
  ibus-hangul.x86_64 0:1.3.1-6.fc15                                             
  ibus-libs.x86_64 0:1.3.99.20110419-13.fc15                                    
  ibus-pinyin.x86_64 0:1.3.99.20110706-2.fc15                                   
  ibus-pinyin-db-android.noarch 0:1.3.99.20110706-2.fc15                        
  libcurl.x86_64 0:7.21.3-9.fc15                                                
  lm_sensors-libs.x86_64 0:3.3.1-1.fc15                                         
  logrotate.x86_64 0:3.7.9-14.fc15                                              
  mesa-dri-drivers.x86_64 0:7.11-1.fc15                                         
  mesa-dri-filesystem.x86_64 0:7.11-1.fc15                                      
  mesa-libGL.x86_64 0:7.11-1.fc15                                               
  mesa-libGLU.x86_64 0:7.11-1.fc15                                              
  perl.x86_64 4:5.12.4-160.fc15                                                 
  perl-Module-Pluggable.noarch 1:3.90-160.fc15                                  
  perl-Pod-Escapes.noarch 1:1.04-160.fc15                                       
  perl-Pod-Simple.noarch 1:3.13-160.fc15                                        
  perl-libs.x86_64 4:5.12.4-160.fc15                                            
  ql2500-firmware.noarch 0:5.06.00-1.fc15                                       
  shadow-utils.x86_64 2:4.1.4.2-13.fc15                                         
  system-config-printer.x86_64 0:1.3.5-3.fc15                                   
  system-config-printer-libs.x86_64 0:1.3.5-3.fc15                              
  system-config-printer-udev.x86_64 0:1.3.5-3.fc15                              
  vlgothic-fonts.noarch 0:20110722-1.fc15                                       
  vlgothic-fonts-common.noarch 0:20110722-1.fc15                                
  wget.x86_64 0:1.12-4.fc15                                                     

Complete!
bash-4.2# exit
exit
stephen@stephen-Dell-DXP061:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by green112 on 2011-08-15
Still wasn't in the menu after restart.

---

### Post by garvinrick4 on 2011-08-15
So everything is there just cannot get grub2 in Ubuntu to find it? Going to think this out
for a minute.

---

### Post by garvinrick4 on 2011-08-15
If you have any data you want to get safe in /home in fedora copy it to Ubuntu partition.
```
sudo mkdir /media/fedora
``````
sudo mount /dev/sda4 /media/fedora
```Will be on desktop, open and copy any thing of value to your ubuntu home or backup drive
whatever you use.
```
sudo umount /media/fedora
```Just incase want to have all your stuff safe.

---

### Post by green112 on 2011-08-15
Thanks for that. 
But the strange thing is, that partition was always accessible from my home folder. It always shows on the left hand bar. I can't access fedora from the grub screen but I can access all it's files from within ubuntu, strange :)

---

### Post by garvinrick4 on 2011-08-15
I found a link from a reputable source and has the same problem. From Ubuntu:
```
sudo apt-get install --reinstall libdebian-installer4
``````
sudo os-prober
``````
sudo update-grub
```

---

### Post by green112 on 2011-08-15
Let's hope it works this time, if not it's fine. I'll use ubuntu for now and access my fedora files from the home folder. Thank you again for the help. You've been very kind, it's much appreciated.

Terminal readout:

```
stephen@stephen-Dell-DXP061:~$ sudo apt-get install --reinstall libdebian-installer4
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libdebian-installer4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.3 kB of archives.
After this operation, 119 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ natty/main libdebian-installer4 amd64 0.77ubuntu2 [25.3 kB]
Fetched 25.3 kB in 0s (153 kB/s)                
Selecting previously deselected package libdebian-installer4.
(Reading database ... 172196 files and directories currently installed.)
Unpacking libdebian-installer4 (from .../libdebian-installer4_0.77ubuntu2_amd64.deb) ...
Setting up libdebian-installer4 (0.77ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
stephen@stephen-Dell-DXP061:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda4:Fedora release 15 (Lovelock):Fedora:linux
stephen@stephen-Dell-DXP061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by green112 on 2011-08-15
I've just rebooted and it wasn't there. 
I feel like I'm wasting your time. I'll do some more reading myself and if I can't get it to work I'll come back to you again :) Thank you very much.

---

### Post by garvinrick4 on 2011-08-15
Do not go yet one more try you are not wasting my time:
From your Ubuntu install"
                          ```
sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt  
 
``````
yum install grub
```                                  Tell it to go into sda4 not sda but in sda4 (might have to use tab key to toggle)

                           ```

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt

```                                  boot into ubuntu and  
 ```
sudo update-grub
```

---

### Post by green112 on 2011-08-15
I don't mind staying to get this fixed.

This is the latest readout. I don't think it went a s planned, says grub was already installed. Should we try reinstalling grub?
```

stephen@stephen-Dell-DXP061:~$ sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for stephen: 
bash-4.2# yum install grub
Loaded plugins: langpacks, presto, refresh-packagekit
Setting up Install Process
Package 1:grub-0.97-71.fc15.x86_64 already installed and latest version
Nothing to do
bash-4.2# exit
exit
stephen@stephen-Dell-DXP061:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
stephen@stephen-Dell-DXP061:~$ sudo update grub
sudo: update: command not found
stephen@stephen-Dell-DXP061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by garvinrick4 on 2011-08-15
You want to make another boot script. It showed no grub in sda4? If all else fails
I know installing Fedora in sda4 and choosing not to install grub at all when it asks about
grub and then booting into Ubuntu and updating-grub works 100% of the time. But
I sure would like to see why it is not seeing it at all. When it had a /boot partition
it would not see it and now it won't either. There is a reason, me taking away the /boot
partition might have not helped but I do not know was not working then either. You can
make a custom entry for it. I know a user who is good at it, I am not just have not gotten
into it. One more boot script just to take a look. We might find it in there, the answer.

## Well see's it now in config file but will not make it a menu entry:

---

### Post by garvinrick4 on 2011-08-15
> Should we try reinstalling grub?Hey that is a good idea. Like post 50 just add the yum remove grub before the yum install grub
Same as before and then while in sda4
```
yum remove grub
``````
yum install grub
```
Do not forget when it asks put in sda4 not sda

---

### Post by green112 on 2011-08-15
This is what it's showing me so far.

I've tried hitting tab so I can select sda4 but it brings up no options, it just tabs across. Shall it enter y and let it install or is there another why to select the partition?

```
stephen@stephen-Dell-DXP061:~$ sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for stephen: 
bash-4.2# yum remove grub
Loaded plugins: langpacks, presto, refresh-packagekit
Setting up Remove Process
Resolving Dependencies
--> Running transaction check
---> Package grub.x86_64 1:0.97-71.fc15 will be erased
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package  Arch       Version             Repository                        Size
================================================================================
Removing:
 grub     x86_64     1:0.97-71.fc15      @koji-override-0/$releasever     2.3 M

Transaction Summary
================================================================================
Remove        1 Package(s)

Installed size: 2.3 M
Is this ok [y/N]: y
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Erasing    : 1:grub-0.97-71.fc15.x86_64                                   1/1 
Unable to connect to dbus

Removed:
  grub.x86_64 1:0.97-71.fc15                                                    

Complete!
bash-4.2# yum install grub
Loaded plugins: langpacks, presto, refresh-packagekit
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package grub.x86_64 1:0.97-71.fc15 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package       Arch            Version                    Repository       Size
================================================================================
Installing:
 grub          x86_64          1:0.97-71.fc15             fedora          656 k

Transaction Summary
================================================================================
Install       1 Package(s)

Total download size: 656 k
Installed size: 2.3 M
Is this ok [y/N]: 
```

---

### Post by garvinrick4 on 2011-08-15
Hit yes.

---

### Post by green112 on 2011-08-15
Ok I've completed that. I'm rebooting now.

Here's the readout:

```
stephen@stephen-Dell-DXP061:~$ sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for stephen: 
bash-4.2# yum remove grub
Loaded plugins: langpacks, presto, refresh-packagekit
Setting up Remove Process
Resolving Dependencies
--> Running transaction check
---> Package grub.x86_64 1:0.97-71.fc15 will be erased
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package  Arch       Version             Repository                        Size
================================================================================
Removing:
 grub     x86_64     1:0.97-71.fc15      @koji-override-0/$releasever     2.3 M

Transaction Summary
================================================================================
Remove        1 Package(s)

Installed size: 2.3 M
Is this ok [y/N]: y
Downloading Packages:
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Erasing    : 1:grub-0.97-71.fc15.x86_64                                   1/1 
Unable to connect to dbus

Removed:
  grub.x86_64 1:0.97-71.fc15                                                    

Complete!
bash-4.2# yum install grub
Loaded plugins: langpacks, presto, refresh-packagekit
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package grub.x86_64 1:0.97-71.fc15 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

================================================================================
 Package       Arch            Version                    Repository       Size
================================================================================
Installing:
 grub          x86_64          1:0.97-71.fc15             fedora          656 k

Transaction Summary
================================================================================
Install       1 Package(s)

Total download size: 656 k
Installed size: 2.3 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 656 k
grub-0.97-71.fc15.x86_64.rpm                             | 656 kB     00:01     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : 1:grub-0.97-71.fc15.x86_64                                   1/1 
Unable to connect to dbus

Installed:
  grub.x86_64 1:0.97-71.fc15                                                    

Complete!
bash-4.2# sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
umount: /mnt/dev/pts: not found
bash-4.2# exit
exit
stephen@stephen-Dell-DXP061:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
stephen@stephen-Dell-DXP061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by green112 on 2011-08-15
:) I had my hopes up about that one fixing it.

I just rebooted and it's still not in the menu.

Any ideas :)

---

### Post by green112 on 2011-08-15
> **green112 said:**
> :) I had my hopes up about that one fixing it.

I just rebooted and it's still not in the menu.

Any ideas :)
I've noticed that it keeps saying 'Unable to connect to dbus' after these terminal installs. Might that be a clue?

---

### Post by garvinrick4 on 2011-08-15
#Do the bootscript so I can find a user that can make a custom entry to put in
as menu entry and leave it on this thread with instructions for you. 
# We got Windows and Ubuntu I cannot believe cannot get Fedora it shows in config
file.
# Do not go away let me take one look at new boot script so in case something hits
me in the face while i am looking at it. Just might be something overlooked, most likely.
We can hope. I will still be here. bootscript please.

---

### Post by garvinrick4 on 2011-08-15
> I've noticed that it keeps saying 'Unable to connect to dbus' after these terminal installs. Might that be a clue? Na, but wish it was a clue.

---

### Post by green112 on 2011-08-15
lol what's a bootscript and how do I create one?

I'm an extreme novice :)

---

### Post by garvinrick4 on 2011-08-15
Remember what we did at the beginning where you downloaded.
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
To DESKTOP and then ran the 4 lines I gave you.

---

### Post by green112 on 2011-08-15
It's not working for me, I'm reading up now on how to unzip.

```
stephen@stephen-Dell-DXP061:~$ unzip boot_info_script060.zip
unzip:  cannot find or open boot_info_script060.zip, boot_info_script060.zip.zip or boot_info_script060.zip.ZIP.
stephen@stephen-Dell-DXP061:~$ Desktop
Desktop: command not found
stephen@stephen-Dell-DXP061:~$ sudo Desktop
[sudo] password for stephen: 
sudo: Desktop: command not found
stephen@stephen-Dell-DXP061:~$ sudo apt-get install unzip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unzip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stephen@stephen-Dell-DXP061:~$ unzip boot_info_script060.zip
unzip:  cannot find or open boot_info_script060.zip, boot_info_script060.zip.zip or boot_info_script060.zip.ZIP.
stephen@stephen-Dell-DXP061:~$ 
```

---

### Post by garvinrick4 on 2011-08-15
[FONT=Times New Roman][SIZE=3]Remember at the start when you downloaded to desktop and then ran these 4 pieces of code:


Open a Terminal and use these four commands one at a time. copy and paste:[/SIZE][/FONT]
      Code:
    ```
 cd Desktop 
```      Code:
     ```
unzip boot_info_script060.zip 
```      Code:
    ```
 chmod +x boot_info_script.sh 
```      Code:
    ```
 sudo ./boot_info_script.sh 
``` [FONT=Times New Roman][SIZE=3]There will now be a file called RESULTS  on Desktop copy and paste to this Thread:[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Use code tags and will be easier to read: (Highlight all text after pasting and click on # sign in upper right of message box)[/SIZE][/FONT]

---

### Post by garvinrick4 on 2011-08-15
Going to see if we put a custom entry in as a menu entry if it will boot from there.
Maybe. Got it written already just want to check the boot script. All you will have to
do is copy and paste it.

---

### Post by green112 on 2011-08-15
Sorry about that, I thought 'cd Desktop' could only be used from within the Live CD. I was trying to just use 'Desktop'. 

Here's the result:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,804,094   337,922,047   133,117,954   5 Extended
/dev/sda5         204,804,096   206,032,895     1,228,800  83 Linux
/dev/sda6         206,034,944   226,514,943    20,480,000  83 Linux
/dev/sda7         226,516,992   318,676,991    92,160,000  83 Linux
/dev/sda8         318,679,040   322,775,039     4,096,000  83 Linux
/dev/sda9         322,777,088   337,922,047    15,144,960  82 Linux swap / Solaris
/dev/sda4         338,946,048   482,306,047   143,360,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   102,402,047   102,400,000  83 Linux
/dev/sdb2         102,402,048   106,498,047     4,096,000  83 Linux
/dev/sdb3         106,498,048   488,275,967   381,777,920   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BA4845F04845AC47                       ntfs       
/dev/sda4        e5435277-e193-4250-998c-40a5bffd128e   ext4       _Fedora-15-x86_6
/dev/sda5        cf743064-2410-46f5-aa11-91728555f14d   ext4       
/dev/sda6        5ce62fbe-4a8e-4029-93af-6943f3f630a9   ext4       
/dev/sda7        becb6216-c60e-45ce-81a5-26c21952dfca   ext4       
/dev/sda8        e8c85ae4-d574-4fe5-acd2-6aa97fbd905e   ext4       
/dev/sda9        22873e76-7e70-4a35-994b-c491435d45a0   swap       swap
/dev/sdb1        790f87ca-0115-4d9f-a021-885e78a9b82f   ext4       
/dev/sdb2        1faa571b-c173-499c-81c3-4c486fc44c8c   ext4       
/dev/sdb3        DEC23899C23877BB                       ntfs       Windows Backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /boot                    ext4       (rw,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sda8        /tmp                     ext4       (rw,commit=0)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA4845F04845AC47
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

  97.797218323 = 105.008963584  grub/core.img                                  1
  97.832042694 = 105.046355968  grub/grub.cfg                                  1
  97.850166321 = 105.065816064  initrd.img-2.6.38-10-generic                   1
  97.811065674 = 105.023832064  initrd.img-2.6.38-8-generic                    1
  97.818672180 = 105.031999488  vmlinuz-2.6.38-10-generic                      1
  97.791263580 = 105.002569728  vmlinuz-2.6.38-8-generic                       1

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA4845F04845AC47
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
UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=cf743064-2410-46f5-aa11-91728555f14d /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=becb6216-c60e-45ce-81a5-26c21952dfca /home           ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=e8c85ae4-d574-4fe5-acd2-6aa97fbd905e /tmp            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=22873e76-7e70-4a35-994b-c491435d45a0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.384132385 = 105.639157760  boot/grub/core.img                             1
  98.418956757 = 105.676550144  boot/grub/grub.cfg                             1
  98.437080383 = 105.696010240  boot/initrd.img-2.6.38-10-generic              1
  98.397979736 = 105.654026240  boot/initrd.img-2.6.38-8-generic               1
  98.405586243 = 105.662193664  boot/vmlinuz-2.6.38-10-generic                 1
  98.378177643 = 105.632763904  boot/vmlinuz-2.6.38-8-generic                  1
  98.437080383 = 105.696010240  initrd.img                                     1
  98.397979736 = 105.654026240  initrd.img.old                                 1
  98.405586243 = 105.662193664  vmlinuz                                        1
  98.378177643 = 105.632763904  vmlinuz.old                                    1

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sun Aug  7 01:52:35 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=e5435277-e193-4250-998c-40a5bffd128e /                       ext4    defaults        1 1
UUID=b3db49c2-cd8b-41f1-ac5b-a79690f8a83a /boot                   ext4    defaults        1 2
UUID=790f87ca-0115-4d9f-a021-885e78a9b82f /home                   ext4    defaults        1 2
UUID=1faa571b-c173-499c-81c3-4c486fc44c8c /tmp                    ext4    defaults        1 2
UUID=22873e76-7e70-4a35-994b-c491435d45a0 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
```

---

### Post by garvinrick4 on 2011-08-15
```
gksudo gedit /etc/grub.d/40_custom
```Now add this below after last line and save up on top: then sudo update-grub


menuentry "Fedora release 15" {
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root e5435277-e193-4250-998c-40a5bffd128e 
linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=/dev/sda4 ro quiet splash
initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img
}

---

### Post by green112 on 2011-08-15
That's what the terminal came back with after I saved the file

```
stephen@stephen-Dell-DXP061:~$ gksudo gedit /etc/grub.d/40_custom

(gedit:4145): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.T572ZV': No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.1TMF0V': No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.N6ZWZV': No such file or directory

(gedit:4145): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
stephen@stephen-Dell-DXP061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$
```

---

### Post by green112 on 2011-08-15
Fedora 15 now appears in the grub menu.

But when I select it I get this error:

```
error: no argument specified
error: file not found
error: you need to load the kernel first

press any key to continue....
```

When I press a key it brings me back to the main grub menu. I selected fedora 15 a few times and each time it brought up that error.

Atleast we're getting closer :)

---

### Post by garvinrick4 on 2011-08-15
Ok we are inching closer and closer to this:
I have got to look at these errors and see what has to be added to custum entry:
I have not used custom entries so a bit out of my pay grade. Will add to this post
when I know. And will send you a message when I do so you know to look. Or maybe
another user will help us out on this entry. I know we can reinstall anytime and take
 an hour and be fine but this is a mission now. Keep an eye out and can message me
anytime at garvinrick4 here in Ubuntu Forums. Will get on this after a bit of sleep. take care.

## You are going to make one fine Ubuntu linux user, you catch on so much faster than must new users.
Believe you that I work with new users everyday, good job today. We got just about it all done and you were easy to work with.
Did not get frusted and throw in the towl, went the whole distance.

---

### Post by green112 on 2011-08-15
Sounds like a plan. Thanks very much for the help. Have a good rest, you deserve it :)

---

### Post by garvinrick4 on 2011-08-15
In /etc/grub.d/40_custom
copy and paste as per below and delete the previous on we used. boot into Ubuntu and update-grub.

Code:
     ```
gksudo gedit /etc/grub.d/40_custom
```Now add this below after last line and save up on top: then sudo update-grub


menuentry "Fedora release 15" {
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root e5435277-e193-4250-998c-40a5bffd128e
linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=e5435277-e193-4250-998c-40a5bffd128e ro quiet splash
initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img
}

---

### Post by green112 on 2011-08-15
Good afternoon :) I hope you had a good rest. Let's see if it's working now. Here's the terminal readout, I'm rebooting now.

```
stephen@stephen-Dell-DXP061:~$ gksudo gedit /etc/grub.d/40_custom

(gedit:3936): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.HBCG0V': No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.3T20ZV': No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.T5C4ZV': No such file or directory

(gedit:3936): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
stephen@stephen-Dell-DXP061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Fedora release 15 (Lovelock) on /dev/sda4
done
stephen@stephen-Dell-DXP061:~$ 

```

---

### Post by garvinrick4 on 2011-08-15
New custom entry on post 67 and post 72, one uses sda4 fedora's partition number and the
other uses fedora's UUID number.

So open the file:
gksudo gedit /etc/grub.d/40_custom.
Delete what is below this in red, DO NOT delete the red: Now add now one written in 67 or 72 and save then sudo update-grub, reboot and see if Fedora will now boot. If does then fine, if does not,  do the same delete old and add the other custom entry save, sudo update-grub and reboot and see if will now boot. Hope it works, it is all I got green112
I am beyond paygrade right now, if you know what I mean. 
[COLOR=Red]
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

[/COLOR]

---

### Post by green112 on 2011-08-15
Ok I just rebooted. It's still not working but this time when I selected fedora it gave me one less error.

It only said this time: 

```
error: file not found
error: you need to load the kernel first

press any key to continue...
```

You may know this already, but I believe grub needs to be told where to find the different kernel versions of fedora or how to differentiate between them. I am right?

---

### Post by garvinrick4 on 2011-08-15
Good morning green112

---

### Post by garvinrick4 on 2011-08-15
If both the custom menu entrys fail to find I believe it needs a new "initramfs" so it can boot, in Ubuntu it is a breeze. sudo update-initramfs -u
But I have found no way I can in Fedora then again I have used Fedora and OpenSuse, Redhat
and such but did not get into it. I seem to have been using Ubuntu now all the time. How did the custom entry with sda4 instead of UUID number do Post 67?

---

### Post by green112 on 2011-08-15
Neither of those two worked.

What if I tried:

```
sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```
```
su - update-initramfs -u
```

Does that make any sense to you?

---

### Post by garvinrick4 on 2011-08-15
> **green112 said:**
> Neither of those two worked.

What if I tried:

```
sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``````
su - update-initramfs -u
```Does that make any sense to you?
You are getting the hang of it:
update-initramfs -u is debian code though, the apt-gets and Fedora is in the yums started by Redhat. 
I was looking for Fedora's equivalent but have not found. I am 99% sure that is what it needs.
Go ahead and get into chroot of Fedora and give me: 
```
uname -a
```Just to check the kernel vesion.

---

### Post by green112 on 2011-08-15
I having a look myself for some codes.

When I ran the uname -a code this is what I got

```
stephen@stephen-Dell-DXP061:~$ sudo mount /dev/sda4 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for stephen: 
bash-4.2# uname -a
Linux stephen-Dell-DXP061 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
bash-4.2# su -
[root@stephen-Dell-DXP061 ~]# uname -a
Linux stephen-Dell-DXP061 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
[root@stephen-Dell-DXP061 ~]# 
```

Seems like it's only giving me the Ubuntu kernel and not the fedora.

---

### Post by green112 on 2011-08-15
I got this of the Fedora website. Is it relevant to us...

```
** 6. Preparing for reboot **

 Before booting you should usually install the bootloader from your new grub by running 
 [CODE]/sbin/grub-install BOOTDEVICE
```  - where BOOTDEVICE is usually /dev/sda (If you get an error '/dev/sda does not have any corresponding BIOS drive' from that, then try /sbin/grub-install --recheck /dev/sda.) 
Also, the order of init scripts could have changed from the previous version. A command to reset the order is: 
 ```
cd /etc/rc.d/init.d; for f in *; do /sbin/chkconfig $f resetpriorities; done
```  Again, run package-cleanup --orphans to find packages that haven't been upgraded. 
[/CODE]

---

### Post by garvinrick4 on 2011-08-15
#Yea that is the Ubuntu kernel that is what is booted now, thinking has gone sour. 
## I just do not have the Fedora skills to fix, tried but no good.
## You got Windows and Ubuntu going now and better off in a fedora forum for the rest.
Are some users in these Forums that have both set of skills. 
#If you cannot get to ever boot and have to reinstall just do not install grub or /boot partition
and go into Ubuntu and update-grub and will put as menuentry and config file and boot properly using Ubuntu's grub2, I know that works 100% of time from first hand experience.
If you do find a solution please send me a personal message and let me know, post it here
so others may see the fix. 

## As per your previous post I have never used those sets of code in the Redhat cousins such
as Fedora so cannot give you an answer. I wish you the best of luck and Sorry I could not get
all three booting for you. Having Windows, Ubuntu and a /boot partition, fedora and its /boot partition was challenging for me but could not finish with Fedora booting also. Good luck to you
green112.

---

### Post by green112 on 2011-08-15
No problem. Thank you very much. I'm gonna try one more thing and if it doesn't work I'll just reinstall. I just had a look at the results file again and I think the kernels are on sda3 so I'm gonna try directing grub to look there. If it doesn't work I'll just reinstall. Anyway, thank you again, you've been very helpful. Have a good day.

---

### Post by YesWeCan on 2011-08-15
This is an epic sized thread. :) I haven't really read anything but the last few posts. I have got a Ubuntu/fedora dual boot working. I'll dig out the details for you.

---

### Post by oldfred on 2011-08-15
Some info on booting Fedora. But as long as Fedora uses grub legacy, you can install grub legacy to the Fedora boot partition and then use a simple chainload entry in 40_custom. Then you chain boot and get the standard Fedora menu to boot from. Example only, you would have to adjust to your versions:

HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27 chainload
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by garvinrick4 on 2011-08-15
There is no sda3 anymore, but in hindsite if I would have left it be and made a custom menu
entry for grub2 to look at Fedoras sda3 /boot  as I did for Ubuntu's sda5 /boot we just might have got Fedora in sda4 to boot. Do not really know if grub2 looking at a grub-legacy boot partition would have booted fedora like sda5 /boot partition did for sda6 where ubuntu was installed all could have been feasable sure would have liked to have found out, but to late now.
Lots of /boot partitions, would still have been nice to make it work properly. 2 operating systems out of 3 booted would sure have been nice to get all 3 working. Just burns me up when cannot figure something out and maybe my in hindsite would have worked. Just flat to bad we will never know. Take care green112, hope you learned something in this long thread, I did. Contact me anytime you want. Enjoy your Ubuntu.

---

### Post by garvinrick4 on 2011-08-15
oldfred,
OP can install the custom entry, can you look at the custom entrys in I believe post 67 and 72 
I believe one with UUID and one with sda4 and see what can be done. It is long thread but
would really like to know if I could have added a line to make grub2 "chainloading" that
would have worked. We tried both entry's and results were posted.
# Reinstalling is no problem can make that work all day long, it is the custom entry that would
like to work or see the errors of my ways.

---

### Post by YesWeCan on 2011-08-15
So I installed fedora first. Then I installed Natty. I made no customisations to Grub in Natty or fedora and my grub.cfg has this OS-prober stanza:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 11.04 (11.04) (on /dev/md5p2)" --class gnu-linux --class gnu --class os {

    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/md5p2
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Fedora (2.6.38.6-26.rc1.fc15.i686) (on /dev/mapper/vg_fedora-lv_root)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 016c5ce4-8031-40da-9631-c0a913bf8a7b
    linux /vmlinuz-2.6.38.6-26.rc1.fc15.i686 ro root=/dev/mapper/vg_fedora-lv_root rd_LVM_LV=vg_fedora/lv_root rd_LVM_LV=vg_fedo
ra/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYTABLE=uk rhgb quiet
    initrd /initramfs-2.6.38.6-26.rc1.fc15.i686.img
}
### END /etc/grub.d/30_os-prober ###
```Now you will notice that it boots fedora 15  directly...it does not chain-load fedora via fedora's legacy grub. This was all auto-detected by update-grub.

What you will also notice is that fedora is installed in LVM partitions. Natty does not come with LVM installed. So you need to install it and actvate the LVM volumes before running update-grub:
[COLOR=Navy]sudo apt-get install lvm2
sudo vgchange -a y
[/COLOR] 
It will list the volumes it has activated and you should see the fedora ones.

Then run
[COLOR=Navy]sudo update-grub[/COLOR]
and see that it adds fedora to the menu.

---

### Post by garvinrick4 on 2011-08-15
> Now you will notice that it boots fedora directly...it does not  chain-load fedora via fedora's legacy grub. This was all auto-detected  by update-grub.Hi, YesWeCan you kind of have to look at original bootscript from getgo. It had 3 installs
1 Windows, 1 UBuntu with separate /boot partition and 1 Fedora with seperate /boot paritition.
Could only boot Windows.
We could get Windows and Ubuntu to boot as is with With Windows in sda1 and Ubuntu /boot partition in sda5 and / in sda6 it was the Fedora in sda4 and it having a /boot partition in sda3
that was the hangup.
#Reinstalling any grub-legacy O.S. using anaconda installer not installing grub at all and then booting into Ubuntu and updating-grub works 100% of time for me so no problem reinstalling.
#It was the multiple /boot partitions and me not knowing quite how to update initramfs in Fedora
install was problem I believe.
#Tried writing custom menuentry twice post 67 and 72 I believe that would not work either put in as menuentry but not bootable.
#Was out of my pay grade I guess trying to use 2 /boot partitions that were installed using grub2 and grub-legacy one being apt-get and one being a yum install. O.P. was up to the task so we gave her a go.

---

### Post by oldfred on 2011-08-15
As YesWeCan says you need the lvm2 drivers to see the Fedora partitions. Some posted to create partitions in advance and install Fedora to the partition so it does not use LVM.

When you have /boot the search line has to refer to the UUID of the /boot partition but the linux line has to refer to the UUID of the / partition. I think that was all that was wrong with post 72 unless it is a lvm install. 

You can only chain boot if you have grub legacy installed to the Fedora partition. It can be /boot or / if there is no /boot. I used to chain boot everything (from a grub only partition) when I only had grub legacy and initially did not like grub2 as it did not like to be installed to a partition. But grub2 os-prober is so good, you usually do not need to chain boot.

---

### Post by YesWeCan on 2011-08-15
I think fedora has only started installing itself to LVM in 15. So I guess guides still talk about messing with legacy grub and chain-loading. I think LVM makes things a lot simpler for adding to Ubuntu's Grub2 menu. I haven't followed this thread but I think if the OP has no data to lose I'd advise deleting sda3 and sda4 and reinstalling fedora **without grub** and without a separate boot partition.

This is not strictly necessary, but to avoid potential problems in the future I would suggest installing Grub to sdb and then restoring the Windows MBR in sda. This will allow a direct boot of Win7 should Grub/Ubuntu go wrong in the future and will avoid potential MBR conflicts that can sometimes arise between Windows and Grub. In this arrangement the bios would be set to boot from sdb.

---

### Post by YesWeCan on 2011-08-15
> **garvinrick4 said:**
> Hi, YesWeCan you kind of have to look at original bootscript from getgo. It had 3 installs
1 Windows, 1 UBuntu with separate /boot partition and 1 Fedora with seperate /boot paritition.
Could only boot Windows.
We could get Windows and Ubuntu to boot as is with With Windows in sda1 and Ubuntu /boot partition in sda5 and / in sda6 it was the Fedora in sda4 and it having a /boot partition in sda3
that was the hangup.
#Reinstalling any grub-legacy O.S. using anaconda installer not installing grub at all and then booting into Ubuntu and updating-grub works 100% of time for me so no problem reinstalling.
#It was the multiple /boot partitions and me not knowing quite how to update initramfs in Fedora
install was problem I believe.
#Tried writing custom menuentry twice post 67 and 72 I believe that would not work either put in as menuentry but not bootable.
#Was out of my pay grade I guess trying to use 2 /boot partitions that were installed using grub2 and grub-legacy one being apt-get and one being a yum install. O.P. was up to the task so we gave her a go.
I'm sure what you had in mind would work fine. I agree with oldfred that you got the UUID wrong for the grub root (sda3). Easy mistake to make and very hard to spot.
You know what linux is like, there are many ways to skin a cat and often it is a matter of trying to keep it as simple as possible to avoid spending too much time on it! Not always easy to do, tho. :)

---

### Post by garvinrick4 on 2011-08-15
oldfred thank you for looking at custom entry. 
I do not use LVM so do make my partitions and then install.

YesWeCan thanks for input about using LVM and posting your os-prober output.
I believe earlier we made sure to backup anything out of fedora's /home.
O.P. is reinstalling without /boot hopefully back into sda4 and
all should be fine.
O.P. will still have a /boot in sda5 for his Ubuntu install so just has to mount
 /boot in sda5 and / in sda6 when reinstalling grub2.

---

### Post by green112 on 2011-08-15
Ok guys, here's an update.

Gavin I took your advice and reinstalled Fedora. I chose not to install a bootloader/grub image and did not have a separate /boot partition made. Fedora was again installed in sda4 and everything went well.

I booted into Ubuntu and ran sudo update-grub and rebooted... NO fedora in grub menu. My heart sank.

So I rebooted Ubuntu and followed all the steps in the previous posts. I did everything again update yum, remove & reinstall grub, os-prober etc. everything that was done before, each time running sudo update-grub but still no fedora in grub. I check the meuentry file and it wasn't there eitheir.

So I created this and saved it to the 40_custom file:
```

menuentry "Fedora release 15" {
insmod ext4
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root 5d0a4eed-b60f-46cc-b160-dc1ffd49ed23
linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 ro quiet splash
initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img
}
```I updated grub, rebooted and fedora appeared. I selected it and it said 
```

error: file not found  
press any key to continue....
```

I didn't expect much since I had written it, but to my surprise, after pressing a key it booted fedora!! I went throught the remaining install setup, password, username. And then the screen went black many times with white writing on it and the fedora log in screen came up. I entered the password but the screen again went black with white writing and then returned to the log in screen again. I keep entering the password and it kept doing that.
I'm guessing the missing file is my /home folder and /tmp folder. It can't find them. It can boot the kernel now but after password entry it cannot enter my /home partition.

So I'll keep looking for a way to elaborate upon the code, but if anyone has any ideas, please share. 

Here is the boot info script results:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   204,802,047   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda2         204,804,094   337,922,047   133,117,954   5 Extended
/dev/sda5         204,804,096   206,032,895     1,228,800  83 Linux
/dev/sda6         206,034,944   226,514,943    20,480,000  83 Linux
/dev/sda7         226,516,992   318,676,991    92,160,000  83 Linux
/dev/sda8         318,679,040   322,775,039     4,096,000  83 Linux
/dev/sda9         322,777,088   337,922,047    15,144,960  82 Linux swap / Solaris
/dev/sda4         338,946,048   482,306,047   143,360,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   102,402,047   102,400,000  83 Linux
/dev/sdb2         102,402,048   106,498,047     4,096,000  83 Linux
/dev/sdb3         106,498,048   488,275,967   381,777,920   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BA4845F04845AC47                       ntfs       
/dev/sda4        5d0a4eed-b60f-46cc-b160-dc1ffd49ed23   ext4       _Fedora-15-x86_6
/dev/sda5        cf743064-2410-46f5-aa11-91728555f14d   ext4       
/dev/sda6        5ce62fbe-4a8e-4029-93af-6943f3f630a9   ext4       
/dev/sda7        becb6216-c60e-45ce-81a5-26c21952dfca   ext4       
/dev/sda8        e8c85ae4-d574-4fe5-acd2-6aa97fbd905e   ext4       
/dev/sda9        22873e76-7e70-4a35-994b-c491435d45a0   swap       swap
/dev/sdb1        095e36a2-ee2e-4ccc-ae4a-e0997045e2e5   ext4       
/dev/sdb2        44906bec-5762-4d52-8181-f951af09f912   ext4       
/dev/sdb3        DEC23899C23877BB                       ntfs       Windows Backup

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /boot                    ext4       (rw,commit=0)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)
/dev/sda8        /tmp                     ext4       (rw,commit=0)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA4845F04845AC47
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora release 15" {
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root e5435277-e193-4250-998c-40a5bffd128e
linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=e5435277-e193-4250-998c-40a5bffd128e ro quiet splash
initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  97.797218323 = 105.008963584  grub/core.img                                  1
  97.832042694 = 105.046355968  grub/grub.cfg                                  1
  97.929126740 = 105.150599168  initrd.img-2.6.38-10-generic                   2
  97.811065674 = 105.023832064  initrd.img-2.6.38-8-generic                    1
  97.818672180 = 105.031999488  vmlinuz-2.6.38-10-generic                      1
  97.791263580 = 105.002569728  vmlinuz-2.6.38-8-generic                       1

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 5ce62fbe-4a8e-4029-93af-6943f3f630a9
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
set locale_dir=($root)/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /vmlinuz-2.6.38-10-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro  vga=769  quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 ro single  vga=769
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root cf743064-2410-46f5-aa11-91728555f14d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root BA4845F04845AC47
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora release 15" {
insmod ext2
set root='(/dev/sda,msdos4)'
search --no-floppy --fs-uuid --set=root e5435277-e193-4250-998c-40a5bffd128e
linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=e5435277-e193-4250-998c-40a5bffd128e ro quiet splash
initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img
}
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
UUID=5ce62fbe-4a8e-4029-93af-6943f3f630a9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=cf743064-2410-46f5-aa11-91728555f14d /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=becb6216-c60e-45ce-81a5-26c21952dfca /home           ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=e8c85ae4-d574-4fe5-acd2-6aa97fbd905e /tmp            ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=22873e76-7e70-4a35-994b-c491435d45a0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.384132385 = 105.639157760  boot/grub/core.img                             1
  98.418956757 = 105.676550144  boot/grub/grub.cfg                             1
  98.516040802 = 105.780793344  boot/initrd.img-2.6.38-10-generic              2
  98.397979736 = 105.654026240  boot/initrd.img-2.6.38-8-generic               1
  98.405586243 = 105.662193664  boot/vmlinuz-2.6.38-10-generic                 1
  98.378177643 = 105.632763904  boot/vmlinuz-2.6.38-8-generic                  1
  98.516040802 = 105.780793344  initrd.img                                     2
  98.397979736 = 105.654026240  initrd.img.old                                 1
  98.405586243 = 105.662193664  vmlinuz                                        1
  98.378177643 = 105.632763904  vmlinuz.old                                    1

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Tue Aug 16 00:18:50 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 /                       ext4    defaults        1 1
UUID=095e36a2-ee2e-4ccc-ae4a-e0997045e2e5 /home                   ext4    defaults        1 2
UUID=44906bec-5762-4d52-8181-f951af09f912 /tmp                    ext4    defaults        1 2
UUID=22873e76-7e70-4a35-994b-c491435d45a0 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 163.877632141 = 175.962267648  boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
 164.778320312 = 176.929374208  boot/initramfs-2.6.40-4.fc15.x86_64.img        2
 162.767604828 = 174.770384896  boot/initrd-plymouth.img                       1
 162.776073456 = 174.779478016  boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1
 164.731967926 = 176.879603712  boot/vmlinuz-2.6.40-4.fc15.x86_64              1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
  No volume groups found
```

---

### Post by Haneef Mubarak on 2011-08-15
No offense intended, but just wondering?

What's a "questioon"?

---

### Post by green112 on 2011-08-15
> **Haneef Mubarak said:**
> No offense intended, but just wondering?

What's a "questioon"?
It's called a typo... I'm pretty sure you could've figured that out yourself.

---

### Post by oldfred on 2011-08-15
Ubuntu's os-prober primarily looks for grub entries from the other installs. So when you did not install any grub, I do not see any menu.lst or grub.conf. If you had installed to /boot or / then it would have created a menu and Ubuntu would have found the entry. You still can install grub legacy to the partition, but I am not sure if in Fedora it is the same as in Ubuntu.

---

### Post by garvinrick4 on 2011-08-15
Take out the custom entry you made for fedora same as you deleted others:

You have a /boot partition in Ubuntu that is still in play in sda5 (pain in rear but there this does have to do with our troubles here.)
This is mounting sda5 and sda6 in chroot installing grub and updating-grub if it is going to
find Fedora this will do it. The only thing different about your partition table than 50 fedora
openSuse, Redhat installs of mine that I have done is that you have a Linux /boot partition thrown in, in the
middle of partition table sda5. I have never had a problem booting any of them. So lets see
mounting this /boot partition straightens this out.

```
sudo mkdir /mnt/boot
``````
sudo mount /dev/sda6 /mnt && sudo mount /dev/sda5 /mnt/boot
```                                 ```
sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo chroot /mnt
``` ```
grub-install /dev/sda
``````
update-grub
``````
grub-mkconfig
```Should see a entry in os-prober for fedora if you want to watch the config file being made, same as update-grub but visual.```
exit
``````
sudo umount /mnt/boot
```                           ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo reboot
```Could have done without all the chroot bit in shorter code but wanted to make sure it all is done while in root.

---

### Post by green112 on 2011-08-15
Ok, I've changed this:

menuentry "Fedora release 15" { insmod ext4 set root='(/dev/sda,msdos4)' search --no-floppy --fs-uuid --set=root 5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 ro quiet splash initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img }

To this:

menuentry "Fedora release 15" { insmod ext2 set root='(/dev/sda,msdos4)' search --no-floppy --fs-uuid --set=root 5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 linux /boot/vmlinuz-2.6.40-4.fc15.x86_64 root=UUID=5d0a4eed-b60f-46cc-b160-dc1ffd49ed23 ro quiet splash initrd /boot/initramfs-2.6.40-4.fc15.x86_64.img }

And now Fedora boots perfectly from grub to the fedora password screen. Still has the problem entering when the password. Screen goes black, white writing on it, then back to the password screen. Over and over again.
I'll have it fixed soon ;) I'll keep youse updated.

---

### Post by green112 on 2011-08-15
> **garvinrick4 said:**
> Take out the custom entry you made for fedora same as you deleted others:

You have a /boot partition in Ubuntu that is still in play in sda5 (pain in rear but there this does have to do with our troubles here.)
This is mounting sda5 and sda6 in chroot installing grub and updating-grub if it is going to
find Fedora this will do it. The only thing different about your partition table than 50 fedora
openSuse, Redhat installs of mine that I have done is that you have a Linux /boot partition thrown in, in the
middle of partition table sda5. I have never had a problem booting any of them. So lets see
mounting this /boot partition straightens this out.

```
sudo mkdir /mnt/boot
``````
sudo mount /dev/sda6 /mnt && sudo mount /dev/sda5 /mnt/boot
```                                 ```
sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo chroot /mnt
``` ```
grub-install /dev/sda
``````
update-grub
``````
grub-mkconfig
```Should see a entry in os-prober for fedora if you want to watch the config file being made, same as update-grub but visual.```
exit
``````
sudo umount /mnt/boot
```                           ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo reboot
```Could have done without all the chroot bit in shorter code but wanted to make sure it all is done while in root.
Gavin, thanks again. I did exactly what you said but fedora was not present in the menu when I rebooted.

I think I should just reformat the drives and do a fresh install of windows, ubuntu and fedora using everything I've learned from you guys. Better to just remove all the mistakes and start fresh.

---

### Post by garvinrick4 on 2011-08-15
> And now Fedora boots perfectly from grub to the fedora password screen.

Hey if you stated a few minutes earlier while I was typing that you got a custom menu entry
to boot into the fedora login screen you have accomplished it, it has booted.

---

### Post by garvinrick4 on 2011-08-15
I am going to install a Fedora 15 myself in a partition and see if any reproduction of your problem. I have a Windows and 6 linux, will see, I will post my bootscript. If it go's fine
then the only difference will be the sda5 /boot for ubuntu of yours. (just so we know)
 ##If you are going to reinstall no reason to format your Windows partition is a good install.

## Is a pity you booted into fedora and got to your login screen.

---

### Post by green112 on 2011-08-15
> **garvinrick4 said:**
> I am going to install a Fedora 15 myself in a partition and see if any reproduction of your problem. I have a Windows and 6 linux, will see, I will post my bootscript. If it go's fine
then the only difference will be the sda5 /boot for ubuntu of yours. (just so we know)
 ##If you are going to reinstall no reason to format your Windows partition is a good install.

## Is a pity you booted into fedora and got to your login screen.
Ok, I'll hold off on reformatting the linux partitions until you post your boot script.

---

### Post by garvinrick4 on 2011-08-15
#Used Fedora 15 disk I made on 5-24-11 64 bit.
#Made a partition sda14 with gparted: Shrunk sda13 by 10 gig and made new sda14 actually.
#Installed using manual install and choose sda14 with no swap and no grub installed. with ext4 format  and / mount point.
#Installed
#Booted into Ubuntu install and sudo update-grub
#Picked up Fedora 15 as menuentry and in config file.
#Rebooted into Fedora 15 running Gnome shell
#Below is boot_info_script
               ```
   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

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
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu oneiric (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu oneiric (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   256,794,621   256,385,022   7 NTFS / exFAT / HPFS
/dev/sda3         256,799,086   578,433,023   321,633,938   5 Extended
/dev/sda5         342,955,620   366,506,909    23,551,290  83 Linux
/dev/sda6         256,799,088   279,322,154    22,523,067  83 Linux
/dev/sda7         279,322,218   342,955,619    63,633,402  83 Linux
/dev/sda8         366,506,973   407,954,609    41,447,637   7 NTFS / exFAT / HPFS
/dev/sda9         407,954,673   429,047,954    21,093,282  83 Linux
/dev/sda10        429,048,018   472,070,024    43,022,007  83 Linux
/dev/sda11        472,072,192   492,910,591    20,838,400  83 Linux
/dev/sda12        492,922,458   513,951,479    21,029,022  83 Linux
/dev/sda13        513,953,792   558,188,543    44,234,752  83 Linux
/dev/sda14        558,190,592   578,433,023    20,242,432  83 Linux
/dev/sda4         578,436,390   625,137,344    46,700,955   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C6EECCF3EECCDCB5                       ntfs       SYSTEM
/dev/sda10       1911269e-13aa-4206-90e2-621b460e3e63   ext4       natty_classic
/dev/sda11       944a2a72-20ee-4378-8b9a-df22e21392bb   ext4       natty_gnome3
/dev/sda12       6651a770-86e7-4f3e-b090-4bd5e39f1675   ext4       oneiric
/dev/sda13       04282cb8-4baa-4f21-aecd-729df9bc35e2   ext4       maverick
/dev/sda14       7b46f2fd-d71d-4994-bfa0-b568509fc2cb   ext4       _Fedora-15-x86_6
/dev/sda2        66B0BDBFB0BD95D1                       ntfs       OS
/dev/sda4        524C43ED4C43CB05                       ntfs       RECOVERY
/dev/sda5        eb110c40-c8a5-45d3-8b72-8cfb165f9bdb   ext4       natty
/dev/sda6        986ca41f-614c-4d55-9927-e4af5cb7e031   ext4       alpha2
/dev/sda7        0f7c5de9-c3b4-4c50-b288-d34e9ef6e119   ext4       home
/dev/sda8        1927A02F2C3A884A                       ntfs       data
/dev/sda9        e3d9f07a-86ae-4ef6-914e-a3ba9a879f82   ext4       lubuntu

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /media/home              ext4       (rw,commit=0)
/dev/sda8        /media/data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
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
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-0300-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-0300-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 3.0.0-0300-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Fedora release 15 (Lovelock) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos14)'
    search --no-floppy --fs-uuid --set=root 7b46f2fd-d71d-4994-bfa0-b568509fc2cb
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 root=/dev/sda14
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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
UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 167.786207199 = 180.159068160  boot/grub/core.img                             1
 169.292009354 = 181.775910912  boot/grub/grub.cfg                             1
 173.620485306 = 186.423576576  boot/initrd.img-3.0.0-0300-generic            67
 171.366991043 = 184.003905536  boot/initrd.img-3.0.1-030001-generic           4
 174.467576981 = 187.333134336  boot/vmlinuz-3.0.0-0300-generic                2
 167.260957718 = 179.595085824  boot/vmlinuz-3.0.1-030001-generic              2
 171.366991043 = 184.003905536  initrd.img                                     4
 173.620485306 = 186.423576576  initrd.img.old                                67
 167.260957718 = 179.595085824  vmlinuz                                        2
 174.467576981 = 187.333134336  vmlinuz.old                                    2

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/sda,msdos6)'
  search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
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
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux    /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    echo    'Loading Linux 3.0.0-8-generic ...'
    linux    /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux    /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    echo    'Loading Linux 3.0.0-7-generic ...'
    linux    /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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
UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 124.640430450 = 133.831643136  boot/grub/core.img                             1
 124.730575562 = 133.928435712  boot/grub/grub.cfg                             1
 126.331314087 = 135.647215616  boot/initrd.img-3.0.0-7-generic                2
 128.271659851 = 137.730646016  boot/initrd.img-3.0.0-8-generic                2
 130.362602234 = 139.975778304  boot/initrd.img-3.0.1-030001-generic           1
 125.670524597 = 134.937698304  boot/vmlinuz-3.0.0-7-generic                   2
 127.428306580 = 136.825102336  boot/vmlinuz-3.0.0-8-generic                   2
 125.568946838 = 134.828630016  boot/vmlinuz-3.0.1-030001-generic              2
 130.284355164 = 139.891761152  initrd.img.old                                 4
 127.428306580 = 136.825102336  vmlinuz                                        2
 125.568946838 = 134.828630016  vmlinuz.old                                    2

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
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
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-0300rc7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux    /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    echo    'Loading Linux 3.0.0-0300rc7-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300rc7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0


--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 198.778305531 = 213.436580352  boot/grub/core.img                             1
 199.255135059 = 213.948572160  boot/grub/grub.cfg                             1
 197.707634449 = 212.286956032  boot/initrd.img-3.0.0-0300rc7-generic          2
 196.629314899 = 211.129119232  boot/initrd.img-3.0.1-030001-generic           2
 195.583065510 = 210.005717504  boot/vmlinuz-3.0.0-0300rc7-generic             1
 195.797890186 = 210.236383744  boot/vmlinuz-3.0.1-030001-generic              2
 196.629314899 = 211.129119232  initrd.img                                     2
 195.797890186 = 210.236383744  vmlinuz                                        2

========================== sda10/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos10)'
search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
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
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-0300rc6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux    /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    echo    'Loading Linux 3.0.0-0300rc6-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300rc6-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=1911269e-13aa-4206-90e2-621b460e3e63 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 212.779316902 = 228.470051840  boot/grub/core.img                             1
 218.724827766 = 234.853995520  boot/grub/grub.cfg                             1
 205.236927986 = 220.371473408  boot/initrd.img-3.0.0-0300rc6-generic          2
 209.594807625 = 225.050711040  boot/initrd.img-3.0.1-030001-generic           2
 207.977093697 = 223.313703936  boot/vmlinuz-3.0.0-0300rc6-generic             1
 209.309105873 = 224.743941120  boot/vmlinuz-3.0.1-030001-generic              2
 209.594807625 = 225.050711040  initrd.img                                     2
 205.236927986 = 220.371473408  initrd.img.old                                 2
 209.309105873 = 224.743941120  vmlinuz                                        2
 207.977093697 = 223.313703936  vmlinuz.old                                    1

========================== sda11/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos11)'
search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
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
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-0300rc7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux    /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    echo    'Loading Linux 3.0.0-0300rc7-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300rc7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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

=============================== sda11/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=944a2a72-20ee-4378-8b9a-df22e21392bb /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda11: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 231.536464691 = 248.610385920  boot/grub/core.img                             1
 225.472343445 = 242.099085312  boot/grub/grub.cfg                             1
 228.293918610 = 245.128728576  boot/initrd.img-3.0.0-0300rc7-generic          2
 230.356449127 = 247.343353856  boot/initrd.img-3.0.1-030001-generic           2
 225.793399811 = 242.443816960  boot/vmlinuz-3.0.0-0300rc7-generic             2
 230.203536987 = 247.179165696  boot/vmlinuz-3.0.1-030001-generic              1
 230.356449127 = 247.343353856  initrd.img                                     2
 228.293918610 = 245.128728576  initrd.img.old                                 2
 230.203536987 = 247.179165696  vmlinuz                                        1
 225.793399811 = 242.443816960  vmlinuz.old                                    2

========================== sda12/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(/dev/sda,msdos12)'
  search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
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
menuentry 'Ubuntu, with Linux 3.0.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux    /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    echo    'Loading Linux 3.0.0-8-generic ...'
    linux    /boot/vmlinuz-3.0.0-8-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux    /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    echo    'Loading Linux 3.0.0-7-generic ...'
    linux    /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux    /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-6-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    echo    'Loading Linux 3.0.0-6-generic ...'
    linux    /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-6-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-8-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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

=============================== sda12/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,user,locale=en_US.utf8 0 0
--------------------------------------------------------------------------------

=================== sda12: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 239.963524818 = 257.658872832  boot/grub/core.img                             1
 239.606423378 = 257.275438080  boot/grub/grub.cfg                             1
 242.535931587 = 260.420973568  boot/initrd.img-3.0.0-6-generic                3
 242.903119087 = 260.815238144  boot/initrd.img-3.0.0-7-generic                2
 242.178021431 = 260.036670464  boot/initrd.img-3.0.0-8-generic                3
 238.649651527 = 256.248112128  boot/vmlinuz-3.0.0-6-generic                   2
 236.259015083 = 253.681185792  boot/vmlinuz-3.0.0-7-generic                   2
 235.883984566 = 253.278499840  boot/vmlinuz-3.0.0-8-generic                   2
 241.284951210 = 259.077743616  grub/core.img                                  1
 235.883984566 = 253.278499840  vmlinuz                                        2
 236.259015083 = 253.681185792  vmlinuz.old                                    2

========================== sda13/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro   quiet splash
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.1-030001-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    echo    'Loading Linux 3.0.1-030001-generic ...'
    linux    /boot/vmlinuz-3.0.1-030001-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.1-030001-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300rc6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux    /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro   quiet splash
    initrd    /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    echo    'Loading Linux 3.0.0-0300rc6-generic ...'
    linux    /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-0300rc6-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc6-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc6-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc2-generic (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set 1911269e-13aa-4206-90e2-621b460e3e63
    linux /boot/vmlinuz-3.0.0-0300rc2-generic root=UUID=1911269e-13aa-4206-90e2-621b460e3e63 ro single
    initrd /boot/initrd.img-3.0.0-0300rc2-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 944a2a72-20ee-4378-8b9a-df22e21392bb
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=944a2a72-20ee-4378-8b9a-df22e21392bb ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 6651a770-86e7-4f3e-b090-4bd5e39f1675
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=6651a770-86e7-4f3e-b090-4bd5e39f1675 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 524C43ED4C43CB05
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-3.0.0-0300-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-3.0.0-0300-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-7-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.0-6-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 986ca41f-614c-4d55-9927-e4af5cb7e031
    linux /boot/vmlinuz-3.0.0-6-generic root=UUID=986ca41f-614c-4d55-9927-e4af5cb7e031 ro single nomodeset
    initrd /boot/initrd.img-3.0.0-6-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.1-030001-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.1-030001-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.1-030001-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-0300rc7-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set e3d9f07a-86ae-4ef6-914e-a3ba9a879f82
    linux /boot/vmlinuz-3.0.0-0300rc7-generic root=UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 ro single
    initrd /boot/initrd.img-3.0.0-0300rc7-generic
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

=============================== sda13/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0

--------------------------------------------------------------------------------

=================== sda13: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 249.322303772 = 267.707785216  boot/grub/core.img                             1
 250.022125244 = 268.459212800  boot/grub/grub.cfg                             3
 250.882469177 = 269.383000064  boot/initrd.img-2.6.31-wl                      1
 248.423828125 = 266.743054336  boot/initrd.img-3.0.0-0300rc6-generic          3
 251.689453125 = 270.249492480  boot/initrd.img-3.0.1-030001-generic           3
 250.920352936 = 269.423677440  boot/vmlinuz-3.0.0-0300rc6-generic             1
 250.849327087 = 269.347414016  boot/vmlinuz-3.0.1-030001-generic              1
 251.689453125 = 270.249492480  initrd.img                                     3
 248.423828125 = 266.743054336  initrd.img.old                                 3
 250.849327087 = 269.347414016  vmlinuz                                        1
 250.920352936 = 269.423677440  vmlinuz.old                                    1

=============================== sda14/etc/fstab: ===============================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Mon Aug 15 19:36:59 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=7b46f2fd-d71d-4994-bfa0-b568509fc2cb /                       ext4    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda14: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 268.421562195 = 288.215457792  boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
 267.311550140 = 287.023591424  boot/initrd-plymouth.img                       1
 267.320018768 = 287.032684544  boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```@green112
Notice no grub files in sda14 Fedora 15 and picked up by os-prober in grub2 and all is fine: 
#Have to say the /boot partition made for Ubuntu in sda5 and attempting to boot the 3rd install was and is a problem in your partition table, even with custom entrys made.
(at least I could not seem to make it work)
# I have Windows and then a large Extended partition with all my different  /'s and /home and a data in NTFS all in logical partitions.
# I do remember Fedora had a different UID of 500 where Ubuntu was 1000 so using same /home was a pain in fedora with permissions different then Ubuntu for me anyway.
   Never did quite work that out, permission problems tend to be a pain.(**uid=1000** makes the Linux-user with specified uid or username owner of the mounted share, thereby allowing that user to rename files) Fedora was uid=500 I do believe.( in other words using same  /home isn't cool)
#Will show you my partition table in gparted in case it helps you in next post.

---

### Post by garvinrick4 on 2011-08-15
Here it is. If you need anything at all just say so.

---

