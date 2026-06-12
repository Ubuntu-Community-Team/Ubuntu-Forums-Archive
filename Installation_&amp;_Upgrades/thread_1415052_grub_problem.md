---
title: "grub problem"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by themis on 2010-02-24
Hello, 

I had xp, added win7, and now added kubuntu.

But can't choose the OS to load on grub.

Can't find a fix through the posted threads, can you guide me to solving the problem?

Thanks in advance, 
themis

---

### Post by drs305 on 2010-02-24
Are you using Grub 2?  (Check with "grub-install -v" in a terminal).

Do you see any menu when you boot?

If you don't see a menu, try holding down the SHIFT key during boot to reveal the menu.

Which OS is currently booting?

---

### Post by themis on 2010-02-24
grub-install (GNU GRUB 1.97~beta4)

yes i do see the boot menu!

---

### Post by drs305 on 2010-02-24
Can you give us more information on your problem?  

If you see the menu, do you mean that if you select one of the Windows entries they don't work? If so, here is a link that helps restore Windows after installing Ubuntu (and variants).
[How to restore the Ubuntu/XP/Vista/7 bootloader ]("http://ubuntuforums.org/showthread.php?t=1014708")

If that is not the problem or the link doesn't work, please post the results of this script by meierfra. Place the contents within "code" tags by clicking the # symbol.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by themis on 2010-02-24
I see the menu but the keyboard doesnt work(the arrows and 'Enter').

I ll have a look to the tutorial,
thanks for showing it to me.

If I still have a problem, I'll post again.

Thank you

---

### Post by kansasnoob on 2010-02-24
> I see the menu but the keyboard doesnt work(the arrows and 'Enter').

Is it a USB keyboard?

If so it's possible you may need to enable USB Legacy Support in the BIOS:

[http://support.creative.com/kb/ShowArticle.aspx?sid=5754](http://support.creative.com/kb/ShowArticle.aspx?sid=5754)

---

### Post by ajgreeny on 2010-02-24
If your system will boot into kubuntu, just open a terminal (Konsole in kde if I remember correctly) and type the command sudo update-grub.  That may fix the problem, but it sounds as if there is some problem with the BIOS not recognising your keyboard. Is it a usb keyboard?

Have a quick look in the BIOS screens at boot time by pressing the key that will be shown on screen "Press Del to enter setup" or similar, and see if there is somewhere to "enable legacy usb devices" or a similar option.  It may help the keyboard to work, though is seldom needed these days.

---

### Post by themis on 2010-02-24
It is a usb keyboard.

The weird is that the arrows sometimes(a few though) do work!
How can they be selective on when they will work????

AT BIOS:USB controllers, USB Legacy Function and USB Storage Function were
and still are enabled.
Ubuntu is currently booting.

[How to restore the Ubuntu/XP/Vista/7 bootloader ]("http://ubuntuforums.org/showthread.php?t=1014708") asks for a [B]sudo fdisk -l
[/B] and I get

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x27f427f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      121601   874361722+   f  W95 Ext'd (LBA)
/dev/sda5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda6           25497       50992   204796588+  83  Linux
/dev/sda7           50993       76488   204796588+  83  Linux
/dev/sda8          120606      121601     8000338+  82  Linux swap / Solaris
/dev/sda9          107858      120605   102398278+  83  Linux
/dev/sda10          76489      107857   251971461   83  Linux

Partition table entries are not in disk order

```

How can I tell which is my Ubuntu drive to continue with the tutorial?

---

### Post by ajgreeny on 2010-02-24
Why so many linux partitions in what appears to be a bit of a mess with sda2 containing everything else except the sda1 boot partition for windows?   Have you installed more than one time without overwriting partitions the second time?
You can find which are your ubuntu by in Ubuntu running ```
mount
``` in terminal and at the top you will see a line like
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
```meaning sda1 is mounted as / (root) and is ext4. Depending on your setup you may also get a line like
```
/dev/sda2 on /home type ext4 (rw)
```which is my /home partition.  There are a lot of other lines you can largely ignore as most are just virtual system mounted devices.  Those two lines will be the important ones for your Ubuntu install.

---

### Post by oldfred on 2010-02-24
I had the same problem when I put a new motherboard in about a year ago. Keyboard worked in BIOS and windows but not in grub. I had to switch it to the standard mouse & keyboard ports and then switch back. Once I updated the BIOS everything worked.

If you run the boot-info_script that drs305 suggested, we can tell a lot about your system. Otherwise we are guessing.

---

### Post by themis on 2010-02-25
Ok, this is my RESULTS.txt

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27f427f3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 1,953,520,064 1,748,723,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683   409,593,239   204,796,557   7 HPFS/NTFS
/dev/sda6         409,593,303   819,186,479   409,593,177  83 Linux
/dev/sda7         819,186,543 1,228,779,719   409,593,177  83 Linux
/dev/sda8       1,937,519,388 1,953,520,064    16,000,677  82 Linux swap / Solaris
/dev/sda9       1,732,722,768 1,937,519,324   204,796,557  83 Linux
/dev/sda10      1,228,779,783 1,732,722,704   503,942,922  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        86BC9BEEBC9BD6D1                       ntfs       xp pro system                 
/dev/sda5        0432AFFC32AFF0BA                       ntfs       win 7 pro                     
/dev/sda8        4a849167-89a1-4e52-8eb6-aa7ba4ea4285   swap                                     
/dev/sda9        a0486bd8-28e2-48ea-8b49-5adb35c51ec1   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 86bc9beebc9bd6d1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4a849167-89a1-4e52-8eb6-aa7ba4ea4285 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 905.5GB: boot/grub/core.img
 905.6GB: boot/grub/grub.cfg
 905.7GB: boot/initrd.img-2.6.31-19-generic-pae
 905.5GB: boot/vmlinuz-2.6.31-19-generic-pae
 905.7GB: initrd.img
 905.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by themis on 2010-02-25
Since nobody replied I followed [this]("http://ubuntuforums.org/showthread.php?t=1014708") tutorial but BUMP new problem,
As I boot I am at 'grub rescue>' mode.

Found [this]("http://osdir.com/ml/ubuntu-users/2009-10/msg01413.html") help.
**[COLOR="Red"]ls[/COLOR]** is working
but **[COLOR="red"]root(hd0,X)[/COLOR]** doesnt  ->>> unknown command.
even [COLOR="red"]**help **[/COLOR]is unknown command

any ideas!!???

---

### Post by themis on 2010-02-25
```
ls
set 
ls (hd0,9)/
set root=(hd0,9)
set prefix=(hd0,9)/boot/grub
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda9 ro 
initrd /initrd.img
boot
```

found these helpful commands by [meierfra.]("http://ubuntuforums.org/member.php?u=552151") on [this]("http://ubuntuforums.org/showthread.php?t=1415425&highlight=grub+rescue&page=2") thread

rebooted to see if grub works but AGAIN **grub rescue>**.
so!.. back in kubuntu waiting for directions to set my grub back again!!

---

### Post by oldfred on 2010-02-25
Meierfra's instructions are a one time boot from the error message, you still have to repair once you get into Ubuntu or have to type the instructions again on a reboot.

When you followed the instructions on reinstalling grub which instructions did you follow? There is a difference between grub and grub2 that is very important. If you reinstalled grub2 it should still have booted ok. If you installed grub legacy we now have to remove it completely and reinstall grub.

Rerun the script so we know where you are at.

---

### Post by themis on 2010-02-25
Sorry for the delay

Oldfred, I followed **[these instructions]("http://ubuntuforums.org/showthread.php?t=1014708")** - grub bootloader (9.10 and beyond)

my RESULTS.txt now is

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /mnt/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x27f427f3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 1,953,520,064 1,748,723,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683   409,593,239   204,796,557   7 HPFS/NTFS
/dev/sda6         409,593,303   819,186,479   409,593,177  83 Linux
/dev/sda7         819,186,543 1,228,779,719   409,593,177  83 Linux
/dev/sda8       1,937,519,388 1,953,520,064    16,000,677  82 Linux swap / Solaris
/dev/sda9       1,732,722,768 1,937,519,324   204,796,557  83 Linux
/dev/sda10      1,228,779,783 1,732,722,704   503,942,922  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        86BC9BEEBC9BD6D1                       ntfs       xp pro system                 
/dev/sda5        0432AFFC32AFF0BA                       ntfs       win 7 pro                     
/dev/sda8        4a849167-89a1-4e52-8eb6-aa7ba4ea4285   swap                                     
/dev/sda9        a0486bd8-28e2-48ea-8b49-5adb35c51ec1   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext3       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set a0486bd8-28e2-48ea-8b49-5adb35c51ec1
	linux	/boot/vmlinuz-2.6.31-19-generic-pae root=UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 86bc9beebc9bd6d1
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=a0486bd8-28e2-48ea-8b49-5adb35c51ec1 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=4a849167-89a1-4e52-8eb6-aa7ba4ea4285 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


 905.6GB: boot/grub/core.img
 905.6GB: boot/grub/grub.cfg
 905.7GB: boot/initrd.img-2.6.31-19-generic-pae
 905.5GB: boot/vmlinuz-2.6.31-19-generic-pae
 905.7GB: initrd.img
 905.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by dE_logics on 2010-02-25
Looks like a serious issue.


I don't know f**kin WHY did the Ubuntu developers used an unstable version of Grub!! The version is neither in Gentoo nor in rescueCD.

And what's grub-pc??...this is insane!

---

### Post by oldfred on 2010-02-25
I do not see anything in the result.txt that looks wrong. Maybe someone else will. Can you boot manually by typing in the commands you posted above?

---

### Post by drs305 on 2010-02-25
themis,

Can you rerun these commands from post #13:

```
set root=(hd0,9)
set prefix=(hd0,9)/boot/grub
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda9 ro 
initrd /initrd.img
boot
```

Tell us where you get errors, if any, and what happens after you enter "boot".

---

### Post by themis on 2010-02-25
> **drs305 said:**
> themis,

Can you rerun these commands from post #13:

```
set root=(hd0,9)
set prefix=(hd0,9)/boot/grub
insmod ext2
insmod linux
linux /vmlinuz root=/dev/sda9 ro 
initrd /initrd.img
boot
```

Tell us where you get errors, if any, and what happens after you enter "boot".

just rerun these commands,
all run great,
no problems, no errors!
after "boot" kubuntu loads normally

---

### Post by oldfred on 2010-02-25
If you have a working system but have to manually boot you should reinstall grub from your boot.

sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

---

### Post by themis on 2010-02-25
> **oldfred said:**
> If you have a working system but have to manually boot you should reinstall grub from your boot.

sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

it did work!
I have my grub back!

Time to solve the initial problem!...hold on!
I am working now with two keyboards.
I realized that the USB keyboard doesnt work on grub menu, 
whereas the 'analog' one does.

USB legacy function on BIOS is enabled.
Thank you oldfred!

---

### Post by drs305 on 2010-02-25
> **themis said:**
> it did work!
I have my grub back!

Time to solve the initial problem!...hold on!
I am working now with two keyboards.
I realized that the USB keyboard doesnt work on grub menu, 
whereas the 'analog' one does.

USB legacy function on BIOS is enabled.
Thank you oldfred!

With a working Grub 2, try adding this line to /etc/default/grub:
```

GRUB_PRELOAD_MODULES="usb_keyboard"

```
Save the file, then "sudo update-grub" to get this into the grub.cfg file.

I haven't used this since I've not had problems. The intent is to preload the usb keyboard module as Grub 2 loads. Perhaps it will work for you.

---

### Post by themis on 2010-02-25
> **drs305 said:**
> With a working Grub 2, try adding this line to /etc/default/grub:
```

GRUB_PRELOAD_MODULES="usb_keyboard"

```
Save the file, then "sudo update-grub" to get this into the grub.cfg file.

I haven't used this since I've not had problems. The intent is to preload the usb keyboard module as Grub 2 loads. Perhaps it will work for you.


what do you mean 'with a working grub 2'??
should I exec grub first?

---

### Post by drs305 on 2010-02-25
> **themis said:**
> what do you mean 'with a working grub 2'??
should I exec grub first?

I just meant that now that you have everything working, you can just add this to /etc/default/grub by editing the file in the normal manner (gksu and your text editor of choice). No having to change anything during boot, run extra commands, etc.  Sorry if it was confusing.

---

### Post by themis on 2010-02-25
> **drs305 said:**
> I just meant that now that you have everything working, you can just add this to /etc/default/grub by editing the file in the normal manner (gksu and your text editor of choice). No having to change anything during boot, run extra commands, etc.  Sorry if it was confusing.

I did it,
and now i boot and it stops at  **GRUB loading..**
and reboots, and if I let it, it will continue rebooting forever!

---

### Post by drs305 on 2010-02-25
Ok. Can you get back to the desktop and remove the line and update grub again? 

If not, if you can get to the command line at the menu, press "c" and then remove the usb_keyboard module by typing "rmmod usb_keyboard". Press ESC, then highlight the kernel you want, press "E" and cursor to the "insmod usb_keyboard" line (if it exists) and use the DEL key to remove the line. Then ctrl-x to boot.

---

### Post by themis on 2010-02-25
> **drs305 said:**
> Ok. Can you get back to the desktop and remove the line and update grub again? 

If not, if you can get to the command line at the menu, press "c" and then remove the usb_keyboard module by typing "rmmod usb_keyboard". Press ESC, then highlight the kernel you want, press "E" and cursor to the "insmod usb_keyboard" line (if it exists) and use the DEL key to remove the line. Then ctrl-x to boot.

how can I get to the command line at the menu>>>???
Which menu do you mean?
It doesnt reaches the point where it shows the available OSs.
It reboots before that.
BIOS does work, but I believe this has nothing to do with what you are telling me to do.
fffff... that was close!

---

### Post by drs305 on 2010-02-25
> **themis said:**
> how can I get to the command line at the menu>>>???
Which menu do you mean?
It doesnt reaches the point where it shows the available OSs.
It reboots before that.
BIOS does work, but I believe this has nothing to do with what you are telling me to do.
fffff... that was close!

No it doesn't have anything to do with the BIOS. 
> fffff... that was close!
Is it fixed? I didn't think so.

If you can hold down SHIFT you might get a chance to see the menu - but I doubt it's getting that far. But if you can, then the instructions in the previous post would apply.

If you can't, boot the LiveCD to the Desktop, mount the Ubuntu partition, and then open the grub and grub.cfg files for editing. Substitute your text editor for "gedit".
```
sudo mount /dev/sda9 /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu *gedit* /mnt/etc/default/grub /mnt/boot/grub/grub.cfg
```
Remove the **GRUB_PRELOAD_MODULES="usb_keyboard"** line from grub.
Remove the "**insmod usb_keyboard**" line from grub.cfg
Save both files.

Reboot and your system will be back to the way it was - working but still having your keyboard issue.

---

### Post by themis on 2010-02-25
> **drs305 said:**
> No it doesn't have anything to do with the BIOS. 

Is it fixed? I didn't think so.

If you can hold down SHIFT you might get a chance to see the menu - but I doubt it's getting that far. But if you can, then the instructions in the previous post would apply.

If you can't, boot the LiveCD to the Desktop, mount the Ubuntu partition, and then open the grub and grub.cfg files for editing. Substitute your text editor for "gedit".
```
sudo mount /dev/sda9 /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu *gedit* /mnt/etc/default/grub /mnt/boot/grub/grub.cfg
```
Remove the **GRUB_PRELOAD_MODULES="usb_keyboard"** line from grub.
Remove the "**insmod usb_keyboard**" line from grub.cfg
Save both files.

Reboot and your system will be back to the way it was - working but still having your keyboard issue.

Ok, I have my system back.
One last thing before we give up the try.
I had xp. then installed win 7.
I had these problems at the win loader too, before installing
ubuntu. Does this help?

Thank you anyhow for your patience.
I'll get an analog keyboard first thing in the morning!

---

### Post by drs305 on 2010-02-25
> **themis said:**
> Ok, I have my system back.
One last thing before we give up the try.
I had xp. then installed win 7.
[COLOR="DarkRed"]I had these problems at the win loader too, before installing
ubuntu. Does this help?[/COLOR]

Do you have another usb keyboard to find out if this is a hardware issue specific to this keyboard? You should not have problems with usb keyboards, and the fact that you had the same problem with windows makes the hardware issue even more likely.

---

### Post by themis on 2010-02-25
> **drs305 said:**
> Do you have another usb keyboard to find out if this is a hardware issue specific to this keyboard? You should not have problems with usb keyboards, and the fact that you had the same problem with windows makes the hardware issue even more likely.

no, not for now at least.
but I ll let people know when I try one.
thanks drs305!

---

