---
title: "[Newbie] 11.04 will not start after install"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by ThirdPerson on 2011-07-18
Hi, I'm new to Ubuntu (as in, literally this day) and I have a problem.  I installed Ubuntu to my external hard drive from USB stick, and the install went fine- however, when I try to boot from the boot menu and selecting "External USB storage device" I get another boot menu, showing the installed OSs (in pink, so I assume that this is Ubuntu's) and when I pick Ubuntu-generic...etc, I just get a plain pink screen.  Any help appreiciated.

...Unless this is a really obvious problem that's asked *all the time* and is already answered, or I'm in the wrong forum, in which case I apologise.

---

### Post by Quackers on 2011-07-18
Welcome to UF.
Which graphics card are you using? You may need to use a boot option (like nomodeset) temporarily.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ThirdPerson on 2011-07-18
Let's see...apparently my model has an Intel GMA 950 chip, does that answer your question?  However, the graphics were fine during the installation.

---

### Post by ThirdPerson on 2011-07-19
Incidentally, I just tried running it from USB stick, and it's fine.  Could this be to do with the manual partitioning I did?  I set it to use ext2, using "/" as a mount point.

---

### Post by Quackers on 2011-07-19
The default file system for recent versions of Ubuntu is ext4. I don't know whether using ext2 will have any effect or not.
From the live desktop please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by ThirdPerson on 2011-07-19
(Note that the terminal said "[I]"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results."[/I])

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30574 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
33 heads, 63 sectors/track, 3774 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,847,935     7,847,904   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f604638d-4406-2b48-bd5a-39633faaaf2b   ext2       casper-rw
/dev/sda1        9408881B0887FA8E                       ntfs       
/dev/sdb1        1402-3D47                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-07-19
All that's showing is a 80GB hard drive and a 4GB drive (presumably your flash drive).
Is the external hard drive connected? If it isn't please connect it and run the script again.

---

### Post by ThirdPerson on 2011-07-19
.

---

### Post by ThirdPerson on 2011-07-19
Sorry about that; I disconnect the external one on start up to make sure that by "USB storage device" I'm specifying the flash drive rather than the installed copy on the external.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30574 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   117,210,239   117,210,177   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4018 MB, 4018143232 bytes
33 heads, 63 sectors/track, 3774 cylinders, total 7847936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,847,935     7,847,904   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 3,613,720,563 3,613,720,501   7 NTFS / exFAT / HPFS
/dev/sdc2       3,613,720,574 3,907,028,991   293,308,418   5 Extended
/dev/sdc5       3,613,720,576 3,900,889,087   287,168,512  83 Linux
/dev/sdc6       3,900,891,136 3,907,028,991     6,137,856  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       f604638d-4406-2b48-bd5a-39633faaaf2b   ext2       casper-rw
/dev/sda1        9408881B0887FA8E                       ntfs       
/dev/sdb1        1402-3D47                              vfat       PENDRIVE
/dev/sdc1        FC0C24480C23FBF0                       ntfs       Expansion Drive
/dev/sdc5        f38ef760-7888-4fb7-b553-b122e2c57910   ext2       
/dev/sdc6        16f146e4-a5a5-4fcd-afe5-884e97e391f9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Expansion Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/f38ef760-7888-4fb7-b553-b122e2c57910 ext2       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos5)'
search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdc5 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=/dev/sdc5 ro single 
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
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos5)'
    search --no-floppy --fs-uuid --set=root f38ef760-7888-4fb7-b553-b122e2c57910
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9408881B0887FA8E
    drivemap -s (hd0) ${root}
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

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=f38ef760-7888-4fb7-b553-b122e2c57910 /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=16f146e4-a5a5-4fcd-afe5-884e97e391f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1737.890747070 = 1866.045980672 boot/grub/core.img                             1
1737.890754700 = 1866.045988864 boot/grub/grub.cfg                             1
1737.786914825 = 1865.934491648 boot/initrd.img-2.6.38-8-generic               6
1737.772960663 = 1865.919508480 boot/vmlinuz-2.6.38-8-generic                  3
1737.786914825 = 1865.934491648 initrd.img                                     6
1737.772960663 = 1865.919508480 vmlinuz                                        3

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Quackers on 2011-07-19
That looks fine to me.
I suggest that you go into your bios at boot time (not using the one-time only key) and have a look at your boot priority options. Instead of selectign the "external usb storage device" try selecting one for USB HDD and making that first boot device (or at least put it before your internal hard drive in the order) then save the setting and reboot, taking out your flash drive.
See what happens.

---

### Post by ThirdPerson on 2011-07-19
As I said, I'm a *very *new newbie (though I do have a smattering of knowledge), but wouldn't that be the same as selecting it manually using the boot menu?

---

### Post by Quackers on 2011-07-19
Yes you could use that, but if it works you will need to go into your bios to set it as a permananet change anyway.

---

### Post by ThirdPerson on 2011-07-19
Here we go... (also I'll probably be offline for the night in a few hours, so don't get mad if I stop responding.)

---

### Post by Quackers on 2011-07-19
No problem, the timeline is yours to choose :-)

---

### Post by ThirdPerson on 2011-07-19
OK, there's no separate option for "USB HDD", but it seems the flash drive gets priority over it anyway.  When I boot the HDD, I get the pink boot menu mentioned earlier, and selecting the Ubuntu option leads to a command prompt-style "Busybox". XP boots fine from experience.  And when I said "a few hours" earlier, I misspoke- I'll probably be off within the hour.

---

### Post by Quackers on 2011-07-19
Is there an option for an external HDD or something like that?
I'm not clear on what the pink menu is that you are seeing. What options are you seeing on that menu? You say XP boots ok from that menu? Is it white writing on a pink background?
You go when you want to :-)

---

### Post by ThirdPerson on 2011-07-19
The pink menu is white on pink, and lists Ubuntu, Ubuntu (recovery mode), XP, and some other options I think.  GIve a minute to check...

---

### Post by Quackers on 2011-07-19
Have you tried booting the recovery mode option?

---

### Post by ThirdPerson on 2011-07-19
Right, think I've figured out what the menu is- embarrassingly, I have not until now noticed "GRUB VERSION...etc" at the top, so presumably this is the Grub menu I've seen mentioned around the site.  The other two options are memory tests.

---

### Post by Quackers on 2011-07-19
That's what it sounded like.
At that menu and with the Ubuntu generic entry highlighted, press the "e" key and a new screen will appear.
On the new screen go to the end of the kernel line which currently ends with "quiet splash" and with the backspace key delete those words.
Then press ctrl + x to boot.
This time you will see lots of white text scroll by.
When booting stops the last line or two of that text should give us a clue as to what's wrong.
Please copy those last couple of lines, or any error message and post them here.

Obviously whenever it's convenient for you.

---

### Post by ThirdPerson on 2011-07-19
Starting "Recovery Mode" leads to a wall of text similar to normal (assuming flash drive boot is "normal") boot up, but stops at listing external HDD details.  It then changes to "Busybox", saying that "Gave up waiting for root device, defaulting to shell (or similar)", and adds that "WARNING- dev\sdc5\ does not exist"  (with no pointer, copy and paste is pretty much useless and I have to restart to boot up flash drive anyway, so I'm relying on memory here)

---

### Post by Quackers on 2011-07-19
Have you mentioned that sdc5 error before? I haven't noticed that.
There are a couple of things you could look at or try.
Firstly go into your bios and see if there is a parameter of any kind to look for "large drives" or LBA. If so, please enable it.
Secondly, boot the normal Ubuntu (not recovery) when deleting the quiet splash words.
If that's no good go back to the quiet splash line, delete the quiet splash words then type in 
```
rootdelay=30
``` then press ctrl + x to boot.

---

### Post by ThirdPerson on 2011-07-21
.

---

### Post by ThirdPerson on 2011-07-21
After deleting "quiet slash" leads to a few lines saying (in order)

```
*  Loading essential drivers...done.
*  Running /scripts/init-premount...done.
*  Mounting root file system...Begin: Running /scripts/local-top...done.
```

This stays up for a few minutes before changing to the BusyBox.  This also happens if I insert "rootdelay=30".

---

### Post by dino99 on 2011-07-21
is this installation looks like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ThirdPerson on 2011-07-21
No, just "\", and the swap partition.

---

### Post by ThirdPerson on 2011-07-26
Oh, well, I suppose I can turn my HDD partition into a live USB like I did with my flash drive.

---

