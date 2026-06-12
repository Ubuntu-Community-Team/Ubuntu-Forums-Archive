---
title: "Dual boot help: XP on laptop and Ubuntu on ext HD"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by digital_nite on 2011-01-20
Hi everyone,
   I've been having a difficult time with a dual boot. I hope someone out there can help me. Here's what's going on. I'm on a laptop and have an external hard drive. I have XP on the laptop and Ubuntu on the external hard dirve. For some reason every time I turn my computer on I get this weird message, something like "no device [...] found", and then I'm stuck with a command line that states "grub restore>". I've been able to gain access to the system by starting my computer with the Ubuntu 10.10 live disk then choosing restart from a menu inside of it. However, this isn't how things should be. I should be able to start my system and choose what operating system I want to run without a disk.

    Special note: I used to run Ubuntu through the Wubi installer and things worked perfect, but one day I started having booting problems. I let my system do an update in Ubuntu and ever since then I've been where I am now. All help is welcome.

Thanks everyone,
digital_nite

---

### Post by bcbc on 2011-01-21
So I am unclear... do you currently have Wubi installed on the external?

Do you get a grub prompt whether you have the external drive plugged in or not?

If you are running a Wubi install, then you've accidentally told Grub to install its bootloader on your laptop drive. You need to boot from a windows repair CD and reinstall the windows bootloader. For XP run "fixmbr", for Vista/7 run "bootrec.exe /fixmbr"
See [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) Problem #1.

---

### Post by Rubi1200 on 2011-01-21
I suggest you run the boot info script and post the results here for us to get a better overview of the current state of your system.

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by digital_nite on 2011-01-25
Hello again,
   I've been really busy so please excuse the delayed response. I followed the advice of Rubi1200 and have the "RESULTS." from the boot info script. It should help everyone see what's going on on my system. 


Thanks to everyone for your help.
digital_nite

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     14,346,045   234,420,479   220,074,435   7 HPFS/NTFS
/dev/sda2                  63    14,346,044    14,345,982   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,638,079,102 1,638,077,055   7 HPFS/NTFS
/dev/sdb2       1,638,080,510 1,953,517,567   315,437,058   5 Extended
/dev/sdb5       1,638,080,512 1,948,303,359   310,222,848  83 Linux
/dev/sdb6       1,948,305,408 1,953,517,567     5,212,160  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C040DD3E40DD3C3A                       ntfs                                     
/dev/sda2        6A5F-1690                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BA78CD6178CD1D4F                       ntfs       Elements                      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86   ext4                                     
/dev/sdb6        4f9b84e0-cc77-491e-9315-ab6f0e3501e7   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
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
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c040dd3e40dd3c3a
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6a5f-1690
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=4ad32ca4-4d6a-4dd2-a1c5-1216bd14bf86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4f9b84e0-cc77-491e-9315-ab6f0e3501e7 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 881.8GB: boot/grub/core.img
 860.3GB: boot/grub/grub.cfg
 839.6GB: boot/initrd.img-2.6.35-22-generic
 881.8GB: boot/vmlinuz-2.6.35-22-generic
 839.6GB: initrd.img
 881.8GB: vmlinuz
```

---

### Post by bcbc on 2011-01-25
Likely you want your laptop to boot windows when the external is not plugged in.
When the external is plugged in, you want to select to boot from it and then boot Ubuntu.

If you get a grub rescue prompt when you boot up with the external plugged in then likely your bios is set to boot from it first (when present). (Which is good)

So what I would do is, boot a live CD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```

Reboot, with external plugged in: you should see your grub menu
Shutdown, remove external, and boot again: you should go right into Windows.

Note: when you run apt-get install lilo you'll get a big splash screen warning about running linux from lilo - ignore this - as you're booting windows. If you prefer you can also install the windows bootloader to your laptop drive (boot without external from a windows disc to a repair prompt and run: fixmbr).

PS If my assumptions aren't correct, you aren't sure, or you want more information - let me know

---

### Post by digital_nite on 2011-01-26
Hey BCBC,
       About my external drive, I've been using it as storage for both my operating systems.
I would like to continue using it for this, but simply add on the ability to boot linux. If I take your suggestion, can I access the drive in XP by perhaps plugging it in after boot up?

Thanks,
digital_nite

---

### Post by bcbc on 2011-01-26
> **digital_nite said:**
> Hey BCBC,
       About my external drive, I've been using it as storage for both my operating systems.
I would like to continue using it for this, but simply add on the ability to boot linux. If I take your suggestion, can I still access the drive in XP by perhaps plugging it in after boot up?

Thanks,
digital_nite
Yes - it would work the same. The changes you are making are only for the bootloaders (only affects computer at boot time). You will still be able to boot Windows from Grub2 (when the external is plugged in at boot time), and you can still access existing ntfs or fat partitions from Windows from the external.

---

### Post by digital_nite on 2011-01-26
Hey BCBC,
    I have a problem. I followed all your steps and now I don't get a boot menu to log into ubuntu. In addition, I can't get into Ubuntu at all. What should I do? I'd hate to reformat the external drive and reinstall linux completely.

digital_nite

---

### Post by bcbc on 2011-01-26
You don't need to reinstall Ubuntu. You just need to choose the external as the first boot device.

Either go into your BIOS and select to boot first from USB devices, or press the BIOS boot menu override key and select to boot from the USB each time you want Ubuntu.

---

### Post by digital_nite on 2011-01-28
Hello again,
    Looks like everything's coming together BCBC. I'm getting closer to dual booting successfully. I just have one problem. When I change my boot order I get to a grub command line. What do I do to boot into Ubuntu from here? Thanks again for the help.

digital_nite

---

### Post by bcbc on 2011-01-28
Did you reinstall grub to the external MBR?
> sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

Is it a grub rescue prompt or a normal grub command line?

If you can't get it working by reinstalling grub, then run the bootinfoscript and post it again.

---

### Post by digital_nite on 2011-01-30
Hi bcbc,
     When I start my computer I can boot to grub but don't know what to do  to boot linux. What should I do? Thanks for all your help

digital_nite

---

### Post by bcbc on 2011-01-31
So... did you install grub2 bootloader to /dev/sdb? When you boot, you select to boot from the external, and then it drops you at a grub prompt? (or a rescue grub prompt?).

What does the bootinfoscript say?

---

