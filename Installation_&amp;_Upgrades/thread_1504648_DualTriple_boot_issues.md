---
title: "Dual/Triple boot issues"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by AliPM on 2010-06-08
Hi, I've been getting into Ubuntu for the last 6 months or so but I've run into some complications. My computer originally had 2 SATA HDDs, one with Windows 7 installed on it and one without a bootable OS (which I just used for storage), then I got hold of a 20GB IDE disc and installed that to use Ubuntu on. This worked fine (with 9.04 and then 9.10) for months, having a GRUB at startup and both Ubuntu and Win7 behaving normally, until I upgraded to 10.04 and it kept coming up with error messages (most annoyingly regarding fglrx compatibility). About a week ago I reinstalled 9.10 and it all worked fine again.

But then about 5 days ago I got all crazy and decided to install XP on the disc that previously had no OS on it, and after doing this I lost the GRUB screen and it would boot straight into XP. I tried looking on the live CD for a restore GRUB option (as quite a few people had recommended) but couldn't find it so I just reinstalled 9.10, and after this a strange thing happened - GRUB was back, with Windows 7 listed as the only other OS, but choosing this option made it boot into XP! Also the sound drivers seemed to be all messed up in XP.

Yesterday I ran the "bootsect.exe" utility from the Win7 system restore console and I'm back to using Win7 with no GRUB or option to use any other OS. Could anyone tell me how to get the GRUB back without reinstalling Ubuntu? I don't mind losing XP, in fact I might just reformat that disc anyway.

Any help is appreciated! Thanks

---

### Post by darkod on 2010-06-08
To get a better idea what we are dealing with, can you run the boot info script and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

And another thought. Since you were willing to make a clean install of 9.10, did you try a clean install of 10.04 too? Sometimes the upgrade process goes wrong but a clean install wouldn't show the same issues.

---

### Post by AliPM on 2010-06-09
Here are the results of running that boot script. Thanks very much btw.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
27 heads, 10 sectors/track, 1808878 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2c246f8

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    11,266,047    11,264,000  27 Hidden HPFS/NTFS
/dev/sda2    *     11,279,520   488,375,999   477,096,480   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,560,639   312,560,577   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfd478bc7

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    37,383,254    37,383,192  83 Linux
/dev/sdc2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sdc5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AE16BDF816BDC19F                       ntfs                                     
/dev/sda2        8454341354340B06                       ntfs                                     
/dev/sdb1        B660339E60336471                       ntfs                                     
/dev/sdc1        57b025f3-a749-4c10-b11f-a92045a9f9c5   ext4                                     
/dev/sdc5        ec365f80-71aa-4679-9107-e3880923b3ba   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda2        /media/8454341354340B06  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin /usepmtimer 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set 57b025f3-a749-4c10-b11f-a92045a9f9c5
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
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 57b025f3-a749-4c10-b11f-a92045a9f9c5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=57b025f3-a749-4c10-b11f-a92045a9f9c5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 57b025f3-a749-4c10-b11f-a92045a9f9c5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=57b025f3-a749-4c10-b11f-a92045a9f9c5 ro single 
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 8454341354340b06
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=57b025f3-a749-4c10-b11f-a92045a9f9c5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=ec365f80-71aa-4679-9107-e3880923b3ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   2.6GB: boot/grub/core.img
   2.6GB: boot/grub/grub.cfg
   2.7GB: boot/initrd.img-2.6.31-14-generic
   2.1GB: boot/vmlinuz-2.6.31-14-generic
   2.7GB: initrd.img
   2.1GB: vmlinuz
```




ps. The main reason I gave up on 10.04 so quickly is because all the window minimize/maximise/close buttons are in the top left and not top right and I couldn't get used to it. Bloody Mac users always getting their way! ;) And no I haven't tried giving it a clean install.

---

### Post by darkod on 2010-06-09
You can get grub2 back to the MBR of /dev/sdc if you boot the ubuntu cd in live mode and execute:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

But in order to see grub2 you need to set BIOS to boot from /dev/sdc, the 20GB disk first.

Your 7 and XP boot files are both on /dev/sda2 but don´t seem combined together. I guess this has to do with which windows OS is installed first. You could try tweaking around, or just restore the XP boot files but before that you need to set specific options, because it depends on them where windows will put the boot files. It´s not very intelligent.

---

### Post by AliPM on 2010-06-10
Should I set the BIOS to boot from the 20gb disc before or after making changes in ubuntu from the live cd or does it not matter?

Thanks for your help btw

---

### Post by darkod on 2010-06-10
> **AliPM said:**
> Should I set the BIOS to boot from the 20gb disc before or after making changes in ubuntu from the live cd or does it not matter?

Thanks for your help btw

For linux it doesn't matter. But windows depends on which disk is set as first to boot from, and which partition on that disk has the boot flag set. It will install the windows bootloader to that disk and windows boot files to that partition. Even if windows is not actually installed in it.

That's why before repairing any type of windows boot files you have to take into account which disk is set as first and which partition on it with the boot flag because that's how you control where the boot files will go.

---

### Post by AliPM on 2010-06-10
So just to clarify before I do anything, to restore the XP boot files do I need to go through the Repair a Broken System options off the install CD? The Ubuntu liveCD isn't smart enough to fix my Windows boot problems as well is it?

I haven't tried anything yet because I don't want to lose the ability to do certain things i can only do in windows until I'm sure I can get it back fairly easily and quickly.

---

### Post by darkod on 2010-06-10
To make things as safe as possible, actually it's best to:

1. Open Gparted from ubuntu live mode and right-click /dev/sdb1, and set a boot flag on it (it currently doesn't have it).

2. Then power down and disconnect other disks, leave just the XP disk connected.

3. Boot with the XP cd, go into Recovery Console, and try:

fixboot (or maybe fixboot c:)
fixmbr

4. Restart and see whether XP boots fine. Until it does, you need to repair the boot process.

Once XP is working fine again, power down, connect the other disks, and you will need to restore grub2 to the MBR of /dev/sdc and make sdc the first disk to boot from.

---

### Post by AliPM on 2010-06-10
Right, I'll try that. Do you know if it is enough to disable the drives in BIOS, rather than physically disconnecting them?

---

### Post by darkod on 2010-06-10
> **AliPM said:**
> Right, I'll try that. Do you know if it is enough to disable the drives in BIOS, rather than physically disconnecting them?

Should be enough. If BIOS does't see them, nothing should be able to see them.

---

### Post by AliPM on 2010-08-18
@darkod
Sorry I never replied to let you know how it went - I was unable to disable the drive in BIOS, and simply because I've been really busy and haven't been in the mood to do fiddle around with my computer a lot I just let it slide. I'm taking a different tack though, getting rid of my copy of 7 (which I discovered was actually a pirate copy, cos it started giving me hassle about it not being genuine) and reinstalling XP and 9.10 on my 2 SATA drives.

Your help was truly appreciated, and I hope you weren't too pissed off that I didn't let you know how it went. I just decided that scrubbing all the mess away and starting again clean seemed by far the easiest way to a noob like myself!

---

### Post by AliPM on 2010-08-20
@darkod again
Thanks so much for helping me figure out what was going on with the MBR/grub. Since posting my last post I've managed to get the computer booting up exactly how I want it with XP on one disc and ubuntu 9.10 on the other, and I definitely wouldn't have been able to do it without referring to various posts of yours and using your boot info script.

 I look forward to putting bloody Windoze behind me - I'm just hanging onto it for the games, I promise.

---

### Post by ssulaco on 2010-08-20
> **AliPM said:**
> 
ps. The main reason I gave up on 10.04 so quickly is because all the window minimize/maximise/close buttons are in the top left and not top right and I couldn't get used to it. Bloody Mac users always getting their way! ;) And no I haven't tried giving it a clean install.
This script makes it easy to swop the buttons
[http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html)

---

### Post by AliPM on 2010-08-21
That's some weird psychic internet juju that is - I was thinking about reinstalling Lucid (and deciding against it because of the window buttons thing) 5 mins before I read that post. I literally haven't given a second's thought to using Lucid instead of Karmic since writing that post in June. Cue Twilight Zone music...

And thanks for the heads up, I might reconsider at some point.

---

