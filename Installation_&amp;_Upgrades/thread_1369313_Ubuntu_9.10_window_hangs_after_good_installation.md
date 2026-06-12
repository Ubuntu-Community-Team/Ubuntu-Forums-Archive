---
title: "Ubuntu 9.10 window hangs after good installation"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by zzzmuzz on 2009-12-31
Set up dual  Windows / Ubuntu boot of 9.10 having not used Ubuntu before. The installation went ok, although I had to choose the "trial" first, and once into Ubuntu I could do the installation proper.  

At boot, I got the grub menu. Choosing any of the options (except for XP)  gave a hang... cursor sat in top right hand corner doing nothing. 

After hours I found I could edit the kernel line so I added:  all-generic-ide nopapic nolapic

This got me into the Ubuntu main screen.  From here whenever I opened a window - eg to check display, the whole thing hung.   Similarly when I went to try to access download center. 

After many hours, I don't know what to do next. 

My notebook is an Asus M2N  with 768k Ram.  

Help please....I have followed the progress of Ubuntu for years, and would really like to get this to work!!!


Thanks, 

muzz

---

### Post by presence1960 on 2009-12-31
> **zzzmuzz said:**
> Set up dual  Windows / Ubuntu boot of 9.10 having not used Ubuntu before. The installation went ok, although I had to choose the "trial" first, and once into Ubuntu I could do the installation proper.  

At boot, I got the grub menu. Choosing any of the options (except for XP)  gave a hang... cursor sat in top right hand corner doing nothing. 

After hours I found I could edit the kernel line so I added:  all-generic-ide nopapic nolapic

This got me into the Ubuntu main screen.  From here whenever I opened a window - eg to check display, the whole thing hung.   Similarly when I went to try to access download center. 

After many hours, I don't know what to do next. 

My notebook is an Asus M2N  with 768k Ram.  

Help please....I have followed the progress of Ubuntu for years, and would really like to get this to work!!!


Thanks, 

muzz

Let's go back to the very beginning, because sometimes a faulty install or Ubuntu not working properly is the result of a corrupted iso or bad burn to CD or bad bootable USB creation.

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it as an image to CD or making a bootable USB?

Did you burn the image to CD at a slow speed? 4x-8x usually works well.

When you booted the CD or the USB did you select "check disk for defects" prior to doing anything else.

If you did all that and everything checks out then it is reasonable to assume your install media is OK. If that is the case you may have had an error or something messed up when installing. But in any case do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

> After hours I found I could edit the kernel line so I added: all-generic-ide nopapic nolapic

Did you realize that you can choose those options during the install process? See here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by zzzmuzz on 2009-12-31
Thanks for this. The Boot options link I had found earlier but perhaps not understood all the implications. It did trigger off when I was trying to use an Acronis Rescue Disk (Linux) some months ago. I recalled that when it didnt work on the Acronis Linux interface they suggested using quiet acpi-off noapic

I have just done that by editing the command and it seems to go ok..so far!  I will keep testing and if all is ok , I will follow instructions on your link to make the boot permanent. 

If not, I will go back and send the txt file you suggested. BTW ,  I did do the mem check and all was ok. 

Thanks again, 

Muzz

---

### Post by zzzmuzz on 2009-12-31
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8d32665

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    48,419,909    48,419,847   7 HPFS/NTFS
/dev/sda2          48,419,910    78,140,159    29,720,250   f W95 Ext d (LBA)
/dev/sda5          48,419,973    66,814,334    18,394,362   7 HPFS/NTFS
/dev/sda6          66,814,398    77,545,754    10,731,357  83 Linux
/dev/sda7          77,545,818    78,140,159       594,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="8A44B01744B00849" TYPE="ntfs" 
sda5: UUID="CE64B5F364B5DE81" TYPE="ntfs" 
sda6: UUID="c304d08f-459d-444a-83c3-c2f89ab44280" TYPE="ext4" 
sda7: UUID="5d14ba1a-d5c0-4981-b2fc-054c4ef5c35e" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 
C:\wubildr.mbr = "Ubuntu" 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set c304d08f-459d-444a-83c3-c2f89ab44280
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c304d08f-459d-444a-83c3-c2f89ab44280
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c304d08f-459d-444a-83c3-c2f89ab44280 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set c304d08f-459d-444a-83c3-c2f89ab44280
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c304d08f-459d-444a-83c3-c2f89ab44280 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 8a44b01744b00849
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=c304d08f-459d-444a-83c3-c2f89ab44280 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5d14ba1a-d5c0-4981-b2fc-054c4ef5c35e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  34.2GB: boot/grub/core.img
  34.2GB: boot/grub/grub.cfg
  34.2GB: boot/initrd.img-2.6.31-14-generic
  34.2GB: boot/vmlinuz-2.6.31-14-generic
  34.2GB: initrd.img
  34.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200



```


BTW,  I did have to include  acpi-off  to even get the "try first" option going.

---

### Post by presence1960 on 2010-01-01
I think the key is now to edit those kernel lines again and see what happens

I see you have wubi installed. This worries me as I have never seen this:

```
[COLOR="Red"]sda5/Wubi:[/COLOR] _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
```

I have never seen the text in red- seriously never! Plus that partition is not mountable.

---

### Post by zzzmuzz on 2010-01-01
Thanks.  re wubi.  This will be related to the fact that I had earlier tried to do the WIndows installation and assumed it had failed. 

I have now cleaned off both the Ubuntu partitions -- using Easeus.  I have reinstalled Ubuntu  and now have Windows on about 25 and Ubuntu on 12 gb.  To get Ubuntu to load from grub I still need to add acpi=off in the kernel line.   After lots of experimentation this seems to be the only edit I need. 

I have looked at the details of how to include "edits"  in every boot - is there not a simpler process?  Every time I have tried the "Change boot options permanently on an existing installation"  instructions the process has failed.   The menu.lst always comes up blank.

Almost there!
Muzz
[B][SIZE=2]
[/SIZE][/B]

---

### Post by presence1960 on 2010-01-01
> **zzzmuzz said:**
> Thanks.  re wubi.  This will be related to the fact that I had earlier tried to do the WIndows installation and assumed it had failed. 

I have now cleaned off both the Ubuntu partitions -- using Easeus.  I have reinstalled Ubuntu  and now have Windows on about 25 and Ubuntu on 12 gb.  To get Ubuntu to load from grub I still need to add acpi=off in the kernel line.   After lots of experimentation this seems to be the only edit I need. 

I have looked at the details of how to include "edits"  in every boot - is there not a simpler process?  Every time I have tried the "Change boot options permanently on an existing installation"  instructions the process has failed.   The menu.lst always comes up blank.

Almost there!
Muzz
[B][SIZE=2]
[/SIZE][/B]

That's because 9.10 does not use menu.lst- that is used in GRUB 0.97. Karmic uses GRUB2 (version 1.97 beta) and the file is grub.cfg

GRUB 2 is a little different. [Here]("https://help.ubuntu.com/community/Grub2") is a link to GRUB2. I am pretty busy right now but I will try to get back to you tonight if you can't figure out how to make that edit to grub.cfg

---

### Post by drs305 on 2010-01-01
> **zzzmuzz said:**
> To get Ubuntu to load from grub I still need to add acpi=off in the kernel line.   After lots of experimentation this seems to be the only edit I need. 

I have looked at the details of how to include "edits"  in every boot - is there not a simpler process?  Every time I have tried the "Change boot options permanently on an existing installation"  instructions the process has failed.   The menu.lst always comes up blank.

Almost there!
Muzz


For Grub 2, once you have booted into it normally:
Open this file for editing:
```

gksu gedit /etc/default/grub

```
Edit this line and add (if you have other entries on the line, leave them):
> 
GRUB_CMDLINE_LINUX="[COLOR="Red"]acpi=off[/COLOR]"

Save the file, then run "sudo update-grub"

If you look at /boot/grub/grub.cfg after updating Grub, you should see your Ubuntu entries with lines such as:
Example:
> 
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5a880a39-36a1-46f5-b106-e979608f295a ro [COLOR="Red"]acpi=off[/COLOR]  quiet splash


---

### Post by zzzmuzz on 2010-01-01
Thank you Presence and DRS.  I did this:
> 
GRUB_CMDLINE_LINUX="[COLOR=Red]acpi=off[/COLOR]" 			 		

rebooted and all worked ok.

FYU though DRS, when I ran > sudo update-grub  I get:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```


No mention of acpi=off anywhere!  Still, like I said, it all seems to boot correctly now.

happy new year ....as I am in New Zealand, I'm now in Jan 2!

Cheers, 
Muzz

---

### Post by drs305 on 2010-01-01
> **zzzmuzz said:**
> Thank you Presence and DRS.  I did this:

rebooted and all worked ok.
No mention of acpi=off anywhere!  Still, like I said, it all seems to boot correctly now.


Muzz,

You wouldn't see it in the terminal window but it should be inserted into grub.cfg  Only the kernels and OSs update finds are displayed in the terminal window during the update, and actually only those whose script includes the code to echo it in the terminal (not all do).

But the "acpi=off" should be included in the "linux" boot command for each linux kernel in the grub.cfg file.

Happy GNU year to you as well.

Added: You can mark this SOLVED via the Thread Tools at the top right of the first post if you don't have any other questions. (It's reversible).

---

