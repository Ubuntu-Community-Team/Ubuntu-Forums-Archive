---
title: "HELP!! ubuntu wont boot after upgrading from 10.04 to 10.10 HELP!!!!!!!"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by pinnacle65 on 2010-11-01
Hey guys i was in ubuntu 10.04 and I thought geting the lastest version is the smart thing to do right? so i went to the update manager and upgraded it to 10.10.  but now when i restart the computer all I get is " a black screen with white text that says   

"Gnu Grub Version 1.98+20100804-5ubuntu3
Minimal bash - like editing is supported for the first blah blah, Tab lists possible command completions. Anywher else TAB lists possible device or file completions.

grub> "    

I have a dual boot that has Windows 7 and Ubuntu, Ubuntu being my main OS, I really need to get back on it. I Need help!! why isnt my ubuntu starting up , why am I geting that screen! help!!

---

### Post by garvinrick4 on 2010-11-01
> **pinnacle65 said:**
> Hey guys i was in ubuntu 10.04 and I thought geting the lastest version is the smart thing to do right? so i went to the update manager and upgraded it to 10.10.  but now when i restart the computer all I get is " a black screen with white text that says   

"Gnu Grub Version 1.98+20100804-5ubuntu3
Minimal bash - like editing is supported for the first blah blah, Tab lists possible command completions. Anywher else TAB lists possible device or file completions.

grub> "    

I have a dual boot that has Windows 7 and Ubuntu, Ubuntu being my main OS, I really need to get back on it. I Need help!! why isnt my ubuntu starting up , why am I geting that screen! help!! Do you have a live CD (install cd for Ubuntu) if you do use Try Ubuntu and open a terminal and and Download this script to DESKTOP and then run the code I give you below. Will put a text file on Desktop after running code. Copy and Paste to this Thread, will then be able to tell you code to replace grub2 in mbr.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by pinnacle65 on 2010-11-01
> **garvinrick4 said:**
> Do you have a live CD (install cd for Ubuntu) if you do use Try Ubuntu and open a terminal and and Download this script to DESKTOP and then run the code I give you below. Will put a text file on Desktop after running code. Copy and Paste to this Thread, will then be able to tell you code to replace grub2 in mbr.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh
```


Is it ok if i use the 10.04 Live CD? Thats the one I have, Im going to try it! be right back

---

### Post by garvinrick4 on 2010-11-01
That cd is fine make sure you have your internet connection in the live cd. Network manager upper right.

---

### Post by pinnacle65 on 2010-11-01
> **garvinrick4 said:**
> Do you have a live CD (install cd for Ubuntu) if you do use Try Ubuntu and open a terminal and and Download this script to DESKTOP and then run the code I give you below. Will put a text file on Desktop after running code. Copy and Paste to this Thread, will then be able to tell you code to replace grub2 in mbr.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh
```

[http://i53.tinypic.com/ixgu87.pn](http://i53.tinypic.com/ixgu87.pn)    < --- The Code isnt work! Help! 8:::(

---

### Post by garvinrick4 on 2010-11-01
The Script has to be on the DESKTOP that you downloaded, where did you download it to.
Take it and drag and drop it to the Desktop then run code. Will put a file on Desktop called results. That is what I need to see.
Most likely you downloaded it to downloads instead of Desktop like it needed to be.

---

### Post by Quackers on 2010-11-01
Did you download it to the desktop or the downloads folder. If it's in Downloads just copy/paste it to the desktop then that command will work.

---

### Post by pinnacle65 on 2010-11-01
> **Quackers said:**
> Did you download it to the desktop or the downloads folder. If it's in Downloads just copy/paste it to the desktop then that command will work.


opps sry guys, I didnt see the detail that i had to download the file, There we go , It gave me a Results file. Here is what is says 


> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   323,055,615   302,082,048   7 HPFS/NTFS
/dev/sda3         323,055,616   617,705,471   294,649,856   7 HPFS/NTFS
/dev/sda4         617,705,472   625,139,711     7,434,240  12 Compaq diagnostics


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b59b0456-1dc9-41b5-8bb8-cf3277b4625f   ext4                                     
/dev/sda1        D0EC94FCEC94DE52                       ntfs       PQSERVICE                     
/dev/sda2        584ADE4F4ADE2A10                       ntfs       ACER                          
/dev/sda3        3A9495D5949593CB                       ntfs       DATA                          
/dev/sda4        DE36D89236D86D51                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        0C28404A284034CC                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

================================ sda4/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768 
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

---

### Post by garvinrick4 on 2010-11-01
You have a WUBI install and not a partition install which is quite different.
Here are the links to fix: You are sda2:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

or
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by pinnacle65 on 2010-11-01
> **garvinrick4 said:**
> You have a WUBI install and not a partition install which is quite different.
Here are the links to fix: You are sda2:
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

or
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


There we go! Im back in ubuntu now. Is it just me or is Ubuntu 10.10 a little slower than 10.04?  Anyways who do I get a secondary bootup screen to logon to ubuntu?   First i get a screen that lets me pick weather i want to bootup in Windows 7 or Ubuntu,  but then when i select ubuntu i go to another screen similar , but it says  Ubuntu  and  Ubuntu Recovery mode, a bunch of them, Most of them dont even work.  Cant it just go straight to ubuntu? If not why is there so many ubuntus on that list

---

### Post by garvinrick4 on 2010-11-01
> **pinnacle65 said:**
> There we go! Im back in ubuntu now. Is it just me or is Ubuntu 10.10 a little slower than 10.04?  Anyways who do I get a secondary bootup screen to logon to ubuntu?   First i get a screen that lets me pick weather i want to bootup in Windows 7 or Ubuntu,  but then when i select ubuntu i go to another screen similar , but it says  Ubuntu  and  Ubuntu Recovery mode, a bunch of them, Most of them dont even work.  Cant it just go straight to ubuntu? If not why is there so many ubuntus on that list
They are old kernels of Ubuntu. Write down which ones you do not need like:
2.6.35-19 or something similar. Each one is an older kernel. I am using 2.6.35-22 as the latest. So go into Synaptics. System/admin to Synaptics and in upper right box put in the one you want to be rid of and then remove the generic kernel and headers. Stay focused and remove only older ones. Nice to have two that work in your choices. Or the second way is to use aptitude: Open a terminal:
sudo apt-get install aptitude
sudo aptitude update && sudo aptitude upgrade
Google using aptitude in Ubuntu: It will tell you the difference between apt-get and aptitude:
Enjoy your Ubuntu and go to Original post and edit to Include WUBI Install and then to Thread Tools in upper right and mark as Solved: If your Wubi install works but go's to another screen and you want to be rid of it. Open a new Thread with Wubi and your problem: There are WUBI users out there who may have that fix. I suggest if you have got it working to leave it be. The wubilder addition to Windows boot loader so Ubuntu Wubi will boot is touchy and if you do not know your way around their files in XP can be very confusing. My advice would be to get rid of unused kernels if you want but do not goof around with wubildr (Wubi's boot loader menu entry in Windows).
Oh yes and tell people what fix you used first or second link given to you. Take Care.
 ##I had that particular problem in a WUBI install once and I had two seperate wubilder in a Vista bootloader and had to delete one. I think it would come to no good for you to mess with.

---

### Post by ace101 on 2011-05-10
I have the Results file now. What should be done next ?
Apology I'm a novice.

---

### Post by bcbc on 2011-05-11
> **ace101 said:**
> I have the Results file now. What should be done next ?
Apology I'm a novice.

Create a new thread and post the results (click # sign above and copy and paste the results. If you have a wubi install, check out the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by marcin w on 2011-05-19
please help me with my ubuntu
                  Boot Info Script 0.60    from 17 May 2011


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   307,974,143   307,972,096  83 Linux
/dev/sda2         307,976,190   312,580,095     4,603,906   5 Extended
/dev/sda5         307,976,192   312,580,095     4,603,904  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        47237d74-47db-4dc9-9fde-6da031090e35   ext4       
/dev/sda5        e3337e92-f6f4-446e-88bd-dfe1f223c20f   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
set locale_dir=($root)/boot/grub/locale
set lang=pl_PL
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=47237d74-47db-4dc9-9fde-6da031090e35 ro  quiet  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.38-8-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=47237d74-47db-4dc9-9fde-6da031090e35 ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=47237d74-47db-4dc9-9fde-6da031090e35 ro  quiet  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.35-28-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=47237d74-47db-4dc9-9fde-6da031090e35 ro single  quiet
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 47237d74-47db-4dc9-9fde-6da031090e35
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=47237d74-47db-4dc9-9fde-6da031090e35 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e3337e92-f6f4-446e-88bd-dfe1f223c20f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 108.130027771 = 116.103733248  boot/grub/core.img                             1
 144.240669250 = 154.877239296  boot/grub/grub.cfg                             1
   1.313476562 = 1.410334720    boot/initrd.img-2.6.35-28-generic              2
  31.880104065 = 34.231001088   boot/initrd.img-2.6.38-8-generic               2
 108.140888214 = 116.115394560  boot/vmlinuz-2.6.35-28-generic                 1
 104.458312988 = 112.161259520  boot/vmlinuz-2.6.38-8-generic                  1
  31.880104065 = 34.231001088   initrd.img                                     2
   1.313476562 = 1.410334720    initrd.img.old                                 2
 104.458312988 = 112.161259520  vmlinuz                                        1
 108.140888214 = 116.115394560  vmlinuz.old                                    1
```

---

### Post by bcbc on 2011-05-19
> **marcin w said:**
> please help me with my ubuntu
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98 ) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.


You need grub2 v1.99~rc1 for 11.04. Probably you have to reinstall the grub boot loader from a live cd.

---

### Post by marcin w on 2011-05-20
thanks. do you know how to do this? My knowledge is poor. I rather try solve the problem than install ubuntu again. please help me if you can

---

### Post by bcbc on 2011-05-20
> **marcin w said:**
> thanks. do you know how to do this? My knowledge is poor. I rather try solve the problem than install ubuntu again. please help me if you can
Try this from the grub prompt:
```
set root=(hd0,msdos1)
linux /vmlinuz root=/dev/sda1 ro  quiet splash
initrd /initrd.img
boot

```Then once booted, drop to a terminal (CTRL+ALT+t) and run:
```
sudo grub-install /dev/sda
```

---

### Post by bcbc on 2011-05-20
That last post was if you get dropped to a grub prompt. I don't think you actually said that.

From a live CD (this might be easier if you are currently running one):
```
sudo mount **/dev/sda[COLOR=Red]1[/COLOR]** /mnt
sudo grub-install --root-directory=/mnt **/dev/sda**
```

---

### Post by marcin w on 2011-05-21
I added this comment to terminal (live cd): 
sudo mount **/dev/sda[COLOR=Red]1[/COLOR]** /mnt sudo grub-install --root-directory=/mnt [B]/dev/sda

[/B]and i received that message: Installation finished. No error reported.
Is that mean that the problem is solved? Am I able to run my ubuntu as usual, before update?
Thanks for help

---

### Post by bcbc on 2011-05-21
> **marcin w said:**
> I added this comment to terminal (live cd): 
sudo mount **/dev/sda[COLOR=Red]1[/COLOR]** /mnt sudo grub-install --root-directory=/mnt [B]/dev/sda

[/B]and i received that message: Installation finished. No error reported.
Is that mean that the problem is solved? Am I able to run my ubuntu as usual, before update?
Thanks for help

Those are two separate commands. If you entered them separately, reboot and remove the Ubuntu CD. If you end up at a grub prompt, then use the manual commands I showed to boot.

---

### Post by twodogsdad on 2011-05-21
Hello,
I'm having a similar problem with an upgrade from 10.10 to 11.04. Do you mind if I post my questions here or should I start a new thread?

Thanks,
Cal

---

### Post by marcin w on 2011-05-21
I'm able to run ubuntu after I used this code (no need live cd anymore):
"set root=(hd0,msdos1)
linux /vmlinuz root=/dev/sda1 ro  quiet splash
initrd /initrd.img
boot"
but do I have to do this every time when I want to boot my system? can I go straight to ubuntu when I switch on computer? My life would be easier.
Many thanks for your help so far.

---

### Post by bcbc on 2011-05-21
> **marcin w said:**
> I'm able to run ubuntu after I used this code (no need live cd anymore):
"set root=(hd0,msdos1)
linux /vmlinuz root=/dev/sda1 ro  quiet splash
initrd /initrd.img
boot"
but do I have to do this every time when I want to boot my system? can I go straight to ubuntu when I switch on computer? My life would be easier.
Many thanks for your help so far.

If the grub version at the grub prompt isn't 1.99~rc1... then boot it manually and reinstall grub (I showed you the command above - 'sudo grub-install /dev/sda' )

Try that

---

### Post by marcin w on 2011-05-21
looks like it's not working. what I get after rebooted was black screen with GNU GRUB version 1.99 rc1-13ubuntu3. thanks for your time

---

### Post by bcbc on 2011-05-21
> **marcin w said:**
> looks like it's not working. what I get after rebooted was black screen with GNU GRUB version 1.99 rc1-13ubuntu3. thanks for your time

Looking back at your bootinfoscript, your grub.cfg is at 144GB from the start of the disk. Maybe you have an older bios that can't read files > 137GB
This seems like the most likely reason

How to fix... maybe a separate /boot partition? Maybe separate sda1 so that it within 137GB.
You could try freeing up space and regenerating grub.cfg and see if it creates it in a favourable location.

---

### Post by marcin w on 2011-05-22
ok let's say that I will try this option with separate boot partition, but could you explain me how to do this? thanks a lot

---

### Post by bcbc on 2011-05-22
> **marcin w said:**
> ok let's say that I will try this option with separate boot partition, but could you explain me how to do this? thanks a lot

You should confirm that this is in fact the problem. Check out the  [Grub 2 Basics thread]("http://ubuntuforums.org/showthread.php?t=1195275") and ask *drs305* for recommendations.

PS Any partitioning carries some risks so make sure you back up first. 
Placing a boot partition at the front of the drive using e.g. GParted could take a very long time. If you aren't using > 137GB then you can probably reduce /dev/sda1 so it falls entirely within that limit, and then create a new partition to use the additional space.

---

### Post by marcin w on 2011-05-22
thanks for your help. I try something else. I downloaded latest ubuntu 11.04 and burned live cd. then I chosen option to update ubuntu. finally I have properly booting system. thanks for your help again

---

### Post by bcbc on 2011-05-22
> **marcin w said:**
> thanks for your help. I try something else. I downloaded latest ubuntu 11.04 and burned live cd. then I chosen option to update ubuntu. finally I have properly booting system. thanks for your help again

Okay great - glad to hear you got it sorted. Just be aware the problem could occur again as you use space... whenever you update a kernel the grub.cfg gets regenerated and eventually it could be placed out of range of BIOS.

---

