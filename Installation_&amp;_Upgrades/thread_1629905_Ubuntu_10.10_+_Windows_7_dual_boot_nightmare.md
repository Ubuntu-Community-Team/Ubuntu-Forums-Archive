---
title: "Ubuntu 10.10 + Windows 7 dual boot nightmare"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by Dr.Fuzzy on 2010-11-24
[LEFT]Hi everyone,
[/LEFT]
 
my apologies if this has been answered already somewhere. My Dell laptop came preinstalled with Win7. I installed Ubuntu 10.10 along side, restarted normally, Grub menu OK, Ubuntu working fine, until I chose to boot on Win7 today! Win7 started up normally but when I restarted my laptop I got a message "no module found-press ctrl-alt-del to restart". No matter what i kept getting this message and of course no Grub menu. I then tried to re-install Ubuntu couple of times, but every time I boot into W7 my Grub is destroyed for some reason! Before an hour or so I had the not so smart idea to format the 8MB partition (think is the bootmgr) and re-install Ubuntu. Since then Grub and Ubuntu works fine, but W7 will refuse to boot (grub reloads).

Unfortunately I don't have a cdrom, so any ideas must be based on boot from usb.

my fdisk -l

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       12246    82963073+   7  HPFS/NTFS
/dev/sda4           12246       30402   145833985    5  Extended
/dev/sda5           29659       30402     5962752   82  Linux swap / Solaris
/dev/sda6           12246       29659   139870208   83  Linux

Partition table entries are not in disk order

```

and the boot_info_script

                ```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 385740112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   196,728,066   165,926,147   7 HPFS/NTFS
/dev/sda4         196,728,830   488,396,799   291,667,970   5 Extended
/dev/sda5         476,471,296   488,396,799    11,925,504  82 Linux swap / Solaris
/dev/sda6         196,728,832   476,469,247   279,740,416  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        761CEEBB1CEE7591                       ntfs       RECOVERY                      
/dev/sda3        F480F0C380F08CFC                       ntfs       Windows 7                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f932f059-06e3-45f3-8202-5fb0fe5c27b6   swap                                     
/dev/sda6        5a82e624-7e72-4540-8b00-6e6f89c4419c   ext4       Ubuntu                        
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 761ceebb1cee7591
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f932f059-06e3-45f3-8202-5fb0fe5c27b6 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 173.8GB: boot/grub/core.img
 228.2GB: boot/grub/grub.cfg
 101.6GB: boot/initrd.img-2.6.35-22-generic
 173.8GB: boot/vmlinuz-2.6.35-22-generic
 101.6GB: initrd.img
 173.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

Any help cause I really need to use W7 urgently...

---

### Post by sikander3786 on 2010-11-24
No problems there except that the sda1 partition and some boot files for Windows 7 are missing. You didn't need to delete that for fixing dual boot.

You need a Windows 7 image, burn it to USB and do some startup repair from that. Have you got that on your HDD?

---

### Post by Dr.Fuzzy on 2010-11-25
Exactly as you said, I formatted the bootmgr located on sda1. No, unfortunately I don't have a W7 image, nor I have a cdrom, neither a Windows box handy, just my laptop at the moment. Anything I can do to fix the problem?

By the way, if I do a repair the way you propose, most likely my grub will be wiped off by the W7 bootloader. Or not?

---

### Post by sikander3786 on 2010-11-25
> No, unfortunately I don't have a W7 image, nor I have a cdrom, neither a Windows box handy, just my laptop at the moment. Anything I can do to fix the problem?

If thats the case, there should be some other workaround. Hang in there and some other mate might be able to advise on that. I know lilo used to work with Win XP but can't say if it would work for Windows 7 or not.

> By the way, if I do a repair the way you propose, most likely my grub will be wiped off by the W7 bootloader. Or not?

Yes you'll need to re-install Grub from Ubuntu Live USB but thats not a big deal. Just 2 commands and you'r done.

The problem is to fix Windows 7 bootloader. Wait and see....

---

### Post by Dr.Fuzzy on 2010-11-25
> You need a Windows 7 image, burn it to USB and do some startup repair from that. Have you got that on your HDD?Aaahh, wait a sec, if you mean the recovery partition, yes I left that intact. 

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       12246    82963073+   7  HPFS/NTFS
/dev/sda4           12246       30402   145833985    5  Extended
/dev/sda5           29659       30402     5962752   82  Linux swap / Solaris
/dev/sda6           12246       29659   139870208   83  Linux

Partition table entries are not in disk order

```

I think the recovery partition 16GB is sda2 which I've actually just mount it and has a label RECOVERY.

```

delk@Fermat:~/Downloads$ ll /media/RECOVERY/
total 2158
drwx------ 1 delk delk  12288 2010-11-18 13:31 ./
drwxr-xr-x 5 root root   4096 2010-11-25 06:02 ../
-rw------- 1 delk delk     53 2004-04-30 18:01 AUTORUN.INF
drwx------ 1 delk delk  12288 2010-11-18 13:31 Boot/
-rw------- 1 delk delk 383562 2009-07-13 21:38 bootmgr
drwx------ 1 delk delk   8192 2010-11-18 13:31 dell/
-rw------- 1 delk delk   7450 2009-04-28 18:49 Desktop.ini
-rw------- 1 delk delk  81120 2010-04-20 19:08 Info.exe
-rw------- 1 delk delk    159 2010-11-20 04:49 MASTER.LOG
drwx------ 1 delk delk   8192 2010-11-18 13:31 preload/
-rw------- 2 delk delk  34530 2010-03-19 16:27 protect.arabic
-rw------- 2 delk delk 117133 2009-06-05 13:42 protect.chinese simplified
-rw------- 2 delk delk 117641 2009-06-05 13:42 protect.chinese traditional
-rw------- 2 delk delk 116238 2009-04-16 12:10 protect.danish
-rw------- 2 delk delk 119790 2009-04-16 11:55 protect.dutch
-rw------- 2 delk delk  47233 2009-04-17 13:19 protect.english
-rw------- 2 delk delk 116015 2009-04-16 12:10 protect.french
-rw------- 2 delk delk 116305 2009-04-16 11:58 protect.german
-rw------- 2 delk delk  34476 2010-03-19 16:30 protect.hebrew
-rw------- 2 delk delk 115710 2009-04-16 11:59 protect.italian
-rw------- 2 delk delk 117842 2009-04-16 12:00 protect.japanese
-rw------- 2 delk delk 124495 2009-04-16 12:00 protect.korean
-rw------- 2 delk delk 116195 2009-04-16 12:02 protect.norwegian
-rw------- 2 delk delk 116564 2009-04-16 12:03 protect.portuguese brazilian
-rw------- 2 delk delk 116363 2009-04-16 12:04 protect.spanish
-rw------- 2 delk delk 116404 2009-04-16 12:05 protect.swedish
drwx------ 1 delk delk   8192 2010-11-18 13:31 Recovery/
-rw------- 1 delk delk    192 2010-08-03 11:56 ResSys.ini
-rw------- 2 delk delk    401 2010-08-03 08:14 ST_InstallBackup.ini
drwx------ 1 delk delk      0 2010-08-02 23:48 System Volume Information/

```

---

### Post by rotave on 2010-11-25
try here for help: [http://ubuntuforums.org/showthread.php?t=1519200]("http://ubuntuforums.org/showthread.php?t=1519200")

---

### Post by Dr.Fuzzy on 2010-11-25
That's an excellent resource but in my case I have formated the bootmgr partition and I think it doesn't account for that.

---

### Post by kansasnoob on 2010-11-25
It sounds to me like you might be effected by this:

> "Grub loading. The symbol ' ' not found. Aborted." on Dell machines..
On Dell computers with Dell DataSafe Local Backup (DDSLB) installed, the above message is displayed with a series of characters within the ' ' section. This is a reported bug,
bug [[COLOR="Red"]#482757[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757"). Thanks to [[COLOR="Red"]merry_meercat's post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9081112#post9081112") which details how to fix the problem.

I found that here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Quackers on 2010-11-25
I see a couple of problems.
The first is that sda1 has gone. I don't know if this is significant as all the required Windows boot files appear to be installed (in sda2 and sda3) but Windows can be finicky about it.
The boot flag is set at sda2 so I would expect it to boot Windows ok - unless the installation of grub to sda2 has over-written something.
I would first suggest downloading a Windows 7 repair disc (available by Googling) and burning it to disc. Then I would suggest booting from that disc and running startup repair THREE times, with reboots in between. 
This may be enough to get Windows booting again.
The Windows repair disc is a very useful item to have in your repair arsenal.

---

### Post by Dr.Fuzzy on 2010-11-25
> **rotave said:**
> try here for help: [http://ubuntuforums.org/showthread.php?t=1519200](http://ubuntuforums.org/showthread.php?t=1519200)


Well I just followed that (3rd method "chroot") and now my Ubuntu boots up without a Grub menu. When I do sudo grub-update I get that:

```

delk@Fermat:~$ sudo update-grub
[sudo] password for delk: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

Before I had a windows 7 loader in my grub menu and the grub menu appeared normally...What happened?

---

### Post by sikander3786 on 2010-11-25
> Before I had a windows 7 loader in my grub menu and the grub menu appeared normally...What happened?

Grub menu doesn't appear by default when there is no other operating system besides Ubuntu.

And at the moment, it doesn't recognize your Windows install so it boots directly into Ubuntu.

You need to follow **Quacker's** advice and perform a startup repair using the Windows 7 repair disc/USB and then, re-install Grub.

And recovery option, well that might over-right all your settings including Ubuntu and bring your system back to the factory settings and it would be a lengthy path I believe.

Windows 7 repair disc, absolutely needed here...

---

### Post by efflandt on 2010-11-25
Your problem is that some Dell program (I think Dell DataSafe) stores data in what it "thinks" is an unused part of the mbr.  But grub2 is larger than the Windows mbr, so that steps on grub2, rendering it unbootable.

For my desktop, fixing that was easy because I had put Ubuntu on sda4 (with no swap) and I already had Ubuntu on a USB hard drive.  So I used grub2 on the USB drive to boot Ubuntu on sda4 and did **sudo grub-install --force /dev/sda4**.  Then I did **bootrec /FixMbr** from a Win7 disc and used gparted to mark sda4 as the boot partition.

But you have a number of issues.  Earlier you said you formatted sda1 (which was the Dell Utility partition), but now it is missing.  I don't know what it actually does anyway.  Somehow grub2 ended up in your RECOVERY partition (which is normally  the Dell Win7 boot partition), and your partitions are in the wrong  order (how did sda6 end up before sda5?).

Since sda1 is apparently gone, I guess you could recreate sda1 and install grub2 on that instead of the mbr so Windows programs will not step on it.  This explains how to restore the Windows mbr if you have a bootable live/install iso on USB [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Then you could mark sda1 as the boot partition.  But I have never seen how to fix grub in the boot sector of a Windows partition.

---

### Post by Dr.Fuzzy on 2010-11-25
Thanx for the replies gyes, unfortuantely I don't have a Windows 7 repair disc/USB. Anyone knows how can I get hold of one and how to turn it into a usb boot image. All these without a Win box! Nearly impossible I might guess...

---

### Post by Quackers on 2010-11-25
Here's one guide, but there are others :-)

[http://mintywhite.com/windows-7/7maintenance/create-bootable-windows-7-system-repair-usb-drive-netbooks/](http://mintywhite.com/windows-7/7maintenance/create-bootable-windows-7-system-repair-usb-drive-netbooks/)

---

### Post by Quackers on 2010-11-25
Oops that's a guide for using Windows.
If you download the .iso then use something like unetbootin to make the LiveUSB you should be good.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by kansasnoob on 2010-11-25
Since you've been mucking about in the process of finding the problem it would be best to see a fresh output from the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

As it completes it will show the new file name so you can be sure to post the proper (latest) results.

---

### Post by Dr.Fuzzy on 2010-11-26
Here are the latest results from the boot_info_script.

                ```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 385740112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   196,728,066   165,926,147   7 HPFS/NTFS
/dev/sda4         196,728,830   488,396,799   291,667,970   5 Extended
/dev/sda5         476,471,296   488,396,799    11,925,504  82 Linux swap / Solaris
/dev/sda6         196,728,832   476,469,247   279,740,416  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        761CEEBB1CEE7591                       ntfs       RECOVERY                      
/dev/sda3        F480F0C380F08CFC                       ntfs       Windows 7                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f932f059-06e3-45f3-8202-5fb0fe5c27b6   swap                                     
/dev/sda6        5a82e624-7e72-4540-8b00-6e6f89c4419c   ext4       Ubuntu                        
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 761ceebb1cee7591
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f932f059-06e3-45f3-8202-5fb0fe5c27b6 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 173.8GB: boot/grub/core.img
 228.2GB: boot/grub/grub.cfg
 101.6GB: boot/initrd.img-2.6.35-22-generic
 173.8GB: boot/vmlinuz-2.6.35-22-generic
 101.6GB: initrd.img
 173.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb

```

---

### Post by wilee-nilee on 2010-11-26
Dr. Fuzzy I have asked the mods to code tag your thread this is impossible to read. Look in my signature for instructions on code tags.

---

### Post by Dr.Fuzzy on 2010-11-26
> **wilee-nilee said:**
> Dr. Fuzzy I have asked the mods to code tag your thread this is impossible to read. Look in my signature for instructions on code tags.

Really sorry about that! I've just tagged it myself.

---

### Post by wilee-nilee on 2010-11-26
> **Dr.Fuzzy said:**
> Really sorry about that! I've just tagged it myself. Thanks if you can remove the previous ones and just put a symbol or something it would be helpful or code tag all the read outs.

So
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type: [B] Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and [/B]
                       looks at sector 385740112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

You have grub in your boot follow this link it should clean that up.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Besides that I need to look through the script a little more.

As far as I can tell this is the only problem, but it is always a crap shoot but I think if you run the testdisc following the link to remove grub from sda2 you should be okay with a.
```
sudo update-grub
```

In Ubuntu to reload everything, it may boot W7 any way.
Can you boot into Ubuntu as of now. If you have already stated this sorry but there is just to much text to read through.;)

You are awesome for tagging all that text, I can't thank you enough for that.:popcorn::popcorn::popcorn:

---

### Post by Dr.Fuzzy on 2010-11-26
Corrected all tags. Thanx, I'll try to fix the grub misplacement as you said.

---

### Post by wilee-nilee on 2010-11-26
> **Dr.Fuzzy said:**
> Corrected all tags. Thanx, I'll try to fix the grub misplacement as you said.

Also if you get into windows look for the Dell data safe it would be in the regular remove programs, there is that possibility.

Unless I'm wrong the sda2 partition doesn't show grub along side the /bootmgr /Boot/BCD it says its there though.

---

### Post by Dr.Fuzzy on 2010-11-26
> **wilee-nilee said:**
> 
You have grub in your boot follow this link it should clean that up.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)


testdisk should be run from an Ubuntu live-cd or it's ok to run it within my Ubuntu normal installation? From the Ubuntu live-cd sudo apt-get install testdisk cannot find the package.

---

### Post by wilee-nilee on 2010-11-26
Here is another dell data safe link.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

It may be that you have to reinstall the MS bootloader to get into W7 to remove the dell data safe then reload grub.

---

### Post by wilee-nilee on 2010-11-26
> **Dr.Fuzzy said:**
> testdisk should be run from an Ubuntu live-cd or it's ok to run it within my Ubuntu normal installation? From the Ubuntu live-cd sudo apt-get install testdisk cannot find the package.

You have to have the universe repository ticked open. I think its universe I have never had to use it.

Live or running Ubuntu I don't know, I just see the problems and give the links that are for the problems, I have never had to actually do this fix. People seem to figure it out

I will say though that is is rather strange that three other experienced users in this area especially kansanoob didn't see this so I'm a little in doubt now. Usually you see grub also in the stanzas /bootmgr /Boot/BCD.

You might wait for some feed back tomorrow. I'm getting tired it is about 4am where I am, so I need to crash.

Really in the end my concern is in doing no harm to your OS.;)

---

### Post by Dr.Fuzzy on 2010-11-26
Thanx a million! Really do appreciate all your effort and concern.

---

### Post by Dr.Fuzzy on 2010-11-27
Latest news, after fiddling a bit with my grub (even managed to boot Ubuntu from the awful grub rescue - I'm very proud of that!), I have managed to recover my grub menu, and restore the 16MB (DELLUTILITY) partition (sda1), which I thought I formatted. My grub menu now contains apart from Ubuntu, a 'Windows 7 loader", but unfortunately it doesn't boot on W7, only restarts to grub menu. I even tried to edit it to point to sda3 but no luck.

Follows my fdisk -l:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       12246    82963073+   7  HPFS/NTFS
/dev/sda4           12246       30402   145840023    f  W95 Ext'd (LBA)
/dev/sda5           12246       29659   139870208   83  Linux
/dev/sda6           29659       30402     5962744   82  Linux swap / Solaris

```and the boot_info_script

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 385740112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   196,728,066   165,926,147   7 HPFS/NTFS
/dev/sda4         196,728,830   488,396,799   291,667,970   5 Extended
/dev/sda5         476,471,296   488,396,799    11,925,504  82 Linux swap / Solaris
/dev/sda6         196,728,832   476,469,247   279,740,416  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda2        761CEEBB1CEE7591                       ntfs       RECOVERY                      
/dev/sda3        F480F0C380F08CFC                       ntfs       Windows 7                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f932f059-06e3-45f3-8202-5fb0fe5c27b6   swap                                     
/dev/sda6        5a82e624-7e72-4540-8b00-6e6f89c4419c   ext4       Ubuntu                        
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 5a82e624-7e72-4540-8b00-6e6f89c4419c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 761ceebb1cee7591
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5a82e624-7e72-4540-8b00-6e6f89c4419c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f932f059-06e3-45f3-8202-5fb0fe5c27b6 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 173.8GB: boot/grub/core.img
 228.2GB: boot/grub/grub.cfg
 101.6GB: boot/initrd.img-2.6.35-22-generic
 173.8GB: boot/vmlinuz-2.6.35-22-generic
 101.6GB: initrd.img
 173.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```Now the problem that remains is how to fix W7 boot.

---

### Post by Dr.Fuzzy on 2010-11-28
Choosing "Windows 7 loader" drops me into "error: unknown filesystem" and the Grub rescue prompt. Tried to edit with "e" the bootloader by choosing either sda1 (dellutility), sda2 (RECOVERY), sda3 (Windows 7) but no success, same thing. 
grub-update by default assigns "Window 7 loader to sda2). Please any help how to resolve this...it's really driving me crazy!

---

### Post by Dr.Fuzzy on 2010-11-29
At last I managed to fix it! OK, these couple few days I was stuck at the point where choosing "Windows 7 loader" form grub simply restarted my laptop. Then I realized that W7 points to sda2 (msdos2) or RECOVERY and I manually edited with 'e' to point to sda3 (msdos3) or Windows 7 partition. Unfortunately nothing, until I had the bright idea to remove the uuid line from the bootloader (since this uuid was for sda2), and voila, I got the message "bootmgr is missing...". What I did next was to boot to Ubuntu and simply copy from the RECOVERY partition the /Boot folder and bootmgr file to my Windows 7 partition. I've also did a update-grub, but this might not be necessary. 
Right after I restarted my laptop, edited again the W7 loader, and this time YES!!!! W7 booted!!!! Of course immediately after restart I lost again my grub menu (no module found...blah), so I boot from a live usb Ubuntu and reinstalled grub. I repeated the same process but this time removed "dell safe..." from W7 which seems to be the Grub overwrite problem!:D

I much thank all you guys for your valuable help!

---

### Post by Quackers on 2010-11-29
Well done :-)
Your system should have booted W7 when the boot flag was on sda2, because that's where your first 2 boot files were (are).

---

### Post by Dr.Fuzzy on 2010-11-29
Well, no I've tried that and it didn't work. Now /Boot and bootmgr reside in sda3 (Windows 7) apart from sda2 (RECOVERY). 

update-grub discovers two "Windows 7 loader", the first on sda2 and the second on sda3. Second one works fine now and loads W7 but the first one which is supposed to start the recovery process, simply halts. 

Any ideas of how I may improve the current situation to resolve the recovery option as well?

---

### Post by Quackers on 2010-11-29
I suspect there is a problem with one or both of the boot files in sda2. W7 can be a bit fussy about them not being on sda1 sometimes.
They will do the job just fine in sda3 though.
Your 2 Windows loader entries are probably grub picking up the 2 boot files in sda2 and sda3.
These files would not normally refer to the recovery partition (although they may be in it). You would normally boot to the recovery partition by tapping a key at startup (F11 or similar - your manual should give details).

If you make a note of which one actually boots Windows 7 you can delete (or effectively delete) the other from the grub menu using drs305's guide below. (But in all honesty it would be easier to just live with it :-) ).

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Dr.Fuzzy on 2010-11-29
Well sda1 is named after "DellUtility" 41MB FAT partition, and contains the /Boot folder, but not the bootmgr file. I have no idea what this partition is there for! So, you assume I should move the bootmgr file in sda1, change the bootloader to point to it and boot W7 from there? F?? what key for the Recovery, sorry but I'm abroad and have no manual with me.

---

### Post by Quackers on 2010-11-29
No, if Windows is booting I would advise you to leave things as they are :-)
A manual should be obtainable from the manufacturer's website.

---

### Post by Dr.Fuzzy on 2010-11-29
OK. Think is F12 but this only brings up the boot menu and a diagnostics option for video/memory etc tests.

---

### Post by Quackers on 2010-11-29
Not F12 then :-)
F12 is commonly used for boot options in later machines.

---

### Post by Dr.Fuzzy on 2010-11-29
google'd it but couldn't find anything relevant...

---

### Post by Quackers on 2010-11-29
My first hit on Google. Have you tried this?

[http://www.ehow.com/how_2134715_dell-windows-vista-factory-settings.html](http://www.ehow.com/how_2134715_dell-windows-vista-factory-settings.html)

---

### Post by Davste on 2010-11-29
Can you get into windows? I had a similar problem and I installed easy BCD, messed around with the settings, did a "Fix MBR", and it worked like a charm.

If you can't get into windows try getting windows on a usb stick or something similar - it's slow but serves the purpose ;)

---

### Post by Dr.Fuzzy on 2010-11-29
@Quackers

man I feel ashamed...seriously didn't see it. Thanks a lot! 

@Davster

I can now boot on W7, but had to to do it the hard way. Anyways, the BCD tool was not of any use to me since I wasn't being able to boot on W7. All good now!

---

### Post by Quackers on 2010-11-29
No problem at all :-)
If you are happy that your questions have been answered please mark the thread as solved using the Thread Tools near the top of the page, as it may help others when searching.
Thanks.

---

### Post by oldfred on 2010-11-29
Did you ever run the fix from post #20 as you still showed grub installed in the windows boot sector of sda2. Windows has to have its code in the boot sector and testdisk can recover it (usually). Otherwise you could run fixboot on sda2 from a windows repairCD.

---

### Post by Dr.Fuzzy on 2010-11-29
> **oldfred said:**
> Did you ever run the fix from post #20 as you still showed grub installed in the windows boot sector of sda2. Windows has to have its code in the boot sector and testdisk can recover it (usually). Otherwise you could run fixboot on sda2 from a windows repairCD.

Ahhh the testdisk...yes I gave that a go and ended up in the grub rescue prompt (before I had the Grub menu, and my main problem was not being able to boot W7)! Then I had to go through the Grub manual to figure out the commands to boot Ubuntu again! NO, I wouldn't recommend it, at least It didn't work for me, only made things worse.

---

### Post by Dr.Fuzzy on 2010-12-20
> **Quackers said:**
> My first hit on Google. Have you tried this?

[http://www.ehow.com/how_2134715_dell-windows-vista-factory-settings.html](http://www.ehow.com/how_2134715_dell-windows-vista-factory-settings.html)

Well I decided to resurrect the topic since I've just realized another problem. Pressing F8 at boot time supposedly starts up the Dell restore utility. Sadly this doesn't happen not that I planned to restore my laptop any soon, but just in case I need it I want to have the option working.

The report from the boot_info_script follows:

 ```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 226360144 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 385740112 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,321        80,259   6 FAT16
/dev/sda2              81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3    *     30,801,920   196,728,066   165,926,147   7 HPFS/NTFS
/dev/sda4         196,728,830   488,396,783   291,667,954   f W95 Ext d (LBA)
/dev/sda5         196,728,832   476,469,247   279,740,416  83 Linux
/dev/sda6         476,471,296   488,396,783    11,925,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        761CEEBB1CEE7591                       ntfs       RECOVERY                      
/dev/sda3        F480F0C380F08CFC                       ntfs       Windows 7                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        80dbb1f1-69f5-4d7c-a556-7929b10a3c48   ext4                                     
/dev/sda6        f932f059-06e3-45f3-8202-5fb0fe5c27b6   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/DellUtility       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec)
/dev/sda2        /media/RECOVERY          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=80dbb1f1-69f5-4d7c-a556-7929b10a3c48 ro   quiet splash noapic
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=80dbb1f1-69f5-4d7c-a556-7929b10a3c48 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 80dbb1f1-69f5-4d7c-a556-7929b10a3c48
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 761ceebb1cee7591
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f480f0c380f08cfc
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=80dbb1f1-69f5-4d7c-a556-7929b10a3c48 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f932f059-06e3-45f3-8202-5fb0fe5c27b6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 111.6GB: boot/grub/core.img
 107.4GB: boot/grub/grub.cfg
 101.4GB: boot/initrd.img-2.6.35-24-generic
 111.7GB: boot/vmlinuz-2.6.35-24-generic
 101.4GB: initrd.img
 111.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

and my fdisk -l

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83fc49c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40129+   6  FAT16
Partition 1 does not end on cylinder boundary.
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       12246    82963073+   7  HPFS/NTFS
/dev/sda4           12246       30402   145833977    f  W95 Ext'd (LBA)
/dev/sda5           12246       29659   139870208   83  Linux
/dev/sda6           29659       30402     5962744   82  Linux swap / Solaris

```

Grub2 menu displays Ubuntu (sda4), Windows 7 loader (sda3) - boots into W7,  and Windows 7 loader (sda2) which is the RECOVERY partition identified when did grub-update and doesn't boot.

sda1 is the DellUtility partition.

I am near perfect, if only I manage to fix the restore option!

---

### Post by Quackers on 2010-12-20
Grub2 is installed in the boot sector of sda1 and sda2 (as well as the mbr of sda). This is probably what is borking the recovery partition from running. You got a bit too busy with grub2 I think. I don't know what to suggest to get grub out of sda1 and sda2.
What I would definitely recommend is to make the recovery dvd's as quickly as possible, and verify them too. 
I would also make the recovery disc (which is actually the repair disc) available in Backup and Restore centre in Control Panel - on the left side.

---

### Post by Dr.Fuzzy on 2010-12-20
Tried it, but the st***d windows require a DVD drive (don't have one, nor an external) to create the restore disk nor allow you to create it as an iso and save it elsewhere! So it seems the only option is to try and fix the current system!

---

### Post by oldfred on 2010-12-20
I know testdisk works to recover a backup bootsector as many were installing grub to the windows partitions.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Not sure if it works for FAT partitions also. I would try sda2 first, then see if it works for sda1.

If you cannot create the repairCD I would download this.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I was only able to get the above on a USB by creating the CD and then booting the CD to copy itself to a USB flash drive. I tried all the standard unetbootin and just copying from the ISO. Neither of those worked. I understand they may work for a full Windows ISO.

---

### Post by Dr.Fuzzy on 2010-12-20
testdisk no doubt can do the job but in my case (if you see my earlier posts) made things worse, actually ended up trying to boot from a grub rescue prompt...not very pleasant. 

Removing grub from sda1 and sda2 as Quackers suggested might be the cure to F8 restore denial, but myself haven't got a clue how to.

---

### Post by oldfred on 2010-12-20
If you do not want to use the testdisk way to recover the boot sector you have to use a windows disk to recreate one.

Do not run fixMBR if you want to keep grub in the MBR as fixMBR put the windows boot loader in the MBR.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by Dr.Fuzzy on 2010-12-20
First of all thank you!

Windows 7 boots fine, so instead of using an installation/repair disk cannot just boot them, go into command mode or recovery console and run the mbr commands? Now, supposedly I run the fixmbr command, grub will be wiped out, but I can always boot from an Ubuntu live cd and install it again, update grub entries, etc...serves the purpose or not? Ok, apart from the fixmbr command the rest:

BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

apart from the 1st will also replace grub or not?

---

### Post by Quackers on 2010-12-20
Could you check something please?
Your recovery partition will most likely have an option that it can be accessed (run) by tapping a certain key at boot. On mine I think it's F10, on others it can be F11 or ctrl + F11. Find out which key yours is and try tapping it at boot. If the recovery starts up you will see a black screen with white writing near the bottom which says "Loading Windows Files" and a grey progress bar which turns white as files are loaded. If this proceeds to the recovery environment you will get choices re: recovering your system.
I would guess that if you get this far your recovery will work.
If you don't get any of this I would surmise that grub may have slightly over-written something the recovery partition needed. In that case it is now probably useless without testdisk or something similar.

If you get to the bluey-green background of the recovery environment you can cancel it without changing anything.

---

### Post by Dr.Fuzzy on 2010-12-21
Yes its F7 and pressing it right after the dell boot logo (checked it in the manual) unfortunately doesn't work, instead the grub menu loads up. Anyways, I'm willing to take the risk and try to fix it with testdisk as you proposed, but I haven't got the slightest clue of what to do. Help is needed!

---

### Post by Quackers on 2010-12-21
Try here
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Dr.Fuzzy on 2010-12-22
Thanx for that. Had a quick look, and to tell you the truth I don't clearly see how to use the tool to remove grub from sda1,2...Something I miss here for sure.

---

### Post by Quackers on 2010-12-22
The link is to recover the partition, not remove grub, as such.

---

### Post by Dr.Fuzzy on 2010-12-23
Followed the guide but according to testdisk the boot sector and backup boot sector in both sda1,2 are OK (boot sectors are identical. Of course I repaired them anyway, but no difference) so I don't see what else to look for...

At this state I'm so stubborn and want to fix it that I would try any possible thing that you may think!

---

### Post by oldfred on 2010-12-23
If recovery of backup does not work, testdisk also has a rebuild function.

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_a_lost_and_damaged_NTFS)

If Backup BS isn't available, choose RebuildBS. 

You may also be able to use windows tools to create a new boot sector. Do you have a win7 repairCD?

---

### Post by Dr.Fuzzy on 2010-12-24
No W7 repair CD unfortunately, neither a CD Drive! Based on link (Recovery of a Dell Computer section), I tried to declare my DellUtility partition as "de", wrote the changes on disk, rebooted but for some strange reason the changes were not saved! Repeated that a few times, but no success! Maybe a testdisk bug? I don't know. 

Rebuild and backup bs? Where are those?

---

### Post by oldfred on 2010-12-24
Testdisk has it in its instructions, but I have not used it so I do not know all the details.

You can download a windows repair CD from this:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

The only problem I had was that I could not copy to a USB easily. I tried a variety of ways from Ubuntu, but the only way that worked for me was to create the CD and use the CD to create the bootable USB. If you do not have a CD, then you would have to use another computer to create a USB version. If you have a working windows somewhere it may be easier with that but I do not know.

---

