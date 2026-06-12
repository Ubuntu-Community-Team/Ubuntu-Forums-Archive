---
title: "Dual Boot XP and Xubuntu"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by Shadowforce on 2010-07-05
After quite a bit of troubleshooting, I have only made my problems dual booting XP and Xubuntu go from bad to worse.

I installed xubuntu on my Windows XP laptop as a dual boot system. 
(Single 40gb Hard Disk, used xubuntu wizard to repartition XP)

After installation, Windows XP would not boot from the boot menu; it would just go to a blank screen with a blinking cursor in the upper left corner (xubuntu was fine).

So far, I have repair installed (not clean) Windows XP and used the Windows XP recovery console commands "fixboot" and "fixmbr" (fixmbr caused xubuntu to become unbootable with no boot menu) to no avail.

It would be greatly appreciated if someone could help me out.

---

### Post by darkod on 2010-07-05
From the XP recovery console also try running:

chkdsk c: /r /f

The main thing is to get XP in order. Reinstalling grub2 back to the MBR is easy after that.

---

### Post by Shadowforce on 2010-07-05
Checkdisk is oddly only allowing two parameters: /P and /R

/P: Check even if the drive is not flagged dirty
/R: Locates bad sectors and recovers readable information

Should I just skip /F parameter?

---

### Post by darkod on 2010-07-05
Yeah, give it a go.

---

### Post by Shadowforce on 2010-07-05
CHKDSK has finished.

---

### Post by wilee-nilee on 2010-07-05
> **Shadowforce said:**
> CHKDSK has finished.

If XP is still not booting post the boot script in my signature in code tags as described. I am assuming Xubuntu is booting, still let us know.

Edit: I missed the fixmbr command

---

### Post by Shadowforce on 2010-07-05
Unfortunately, I believe that Grub was overwritten when I used the "fixmbr" command in XP recovery (thus, giving me no access to xubuntu). Is it okay if I run the command off a live cd?

---

### Post by wilee-nilee on 2010-07-05
> **Shadowforce said:**
> Unfortunately, I believe that Grub was overwritten when I used the "fixmbr" command in XP recovery (thus, giving me no access to xubuntu). Is it okay if I run the command off a live cd?

I would rather see the bootscript first, but if you just need grub back in the mbr to have a choice of OS to boot follow this link. The link will default to the #11 link in the top right menu links. This is instructions on reloading grub2 with a live cd. **We are assuming here that this is not a wubi install.**
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Shadowforce on 2010-07-06
> **wilee-nilee said:**
> I would rather see the bootscript first, but if you just need grub back in the mbr to have a choice of OS to boot follow this link. The link will default to the #11 link in the top right menu links. This is instructions on reloading grub2 with a live cd. **We are assuming here that this is not a wubi install.**
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I can run the bootscript off a live cd if you want. I was originally unable to boot XP, and now (after using "fixmbr") I have no boot menu. (No, this is not a wubi install)

---

### Post by CarpKing on 2010-07-06
I think I have had this same symptom with some past upgrades.  It was caused by an erroneous menu.list, IIRC.  Something like "(0,1)" placed after the windows entry causing it to point to the wrong place.

---

### Post by wilee-nilee on 2010-07-06
> **Shadowforce said:**
> I can run the bootscript off a live cd if you want. I was originally unable to boot XP, and now (after using "fixmbr") I have no boot menu. (No, this is not a wubi install)

Run the script, and give a clear description of what is going on, can you boot any OS.

---

### Post by Shadowforce on 2010-07-07
Okay, I will run the script off a live cd. Currently, I cannot boot any operating system. I was able to boot xubuntu before using the "fixmbr" command in the xp recovery console.

---

### Post by Shadowforce on 2010-07-08
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    50,811,299    50,811,237   7 HPFS/NTFS
/dev/sda2          50,812,926    78,139,391    27,326,466   5 Extended
/dev/sda5          50,812,928    76,894,207    26,081,280  83 Linux
/dev/sda6          76,896,256    78,139,391     1,243,136  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        9AF87274F8724E8F                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62e368bf-7990-4eeb-8d33-48b3de2ed97e   ext4                                     
/dev/sda6        45681d0f-3abe-4721-8681-977040e0146f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /forceresetreg /fastdetect /noexecute=optin 

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
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
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=62e368bf-7990-4eeb-8d33-48b3de2ed97e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=62e368bf-7990-4eeb-8d33-48b3de2ed97e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 62e368bf-7990-4eeb-8d33-48b3de2ed97e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9af87274f8724e8f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=62e368bf-7990-4eeb-8d33-48b3de2ed97e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=45681d0f-3abe-4721-8681-977040e0146f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  31.3GB: boot/grub/core.img
  32.8GB: boot/grub/grub.cfg
  31.3GB: boot/initrd.img-2.6.32-21-generic
  31.2GB: boot/vmlinuz-2.6.32-21-generic
  31.3GB: initrd.img
  31.2GB: vmlinuz

```

---

### Post by Shadowforce on 2010-07-12
Can someone interpret the bootscript for me? Help would be greatly appreciated.

---

### Post by wilee-nilee on 2010-07-12
> **Shadowforce said:**
> Can someone interpret the bootscript for me? Help would be greatly appreciated.

The bootscript reads that you should be able to boot XP can you? The MS bootloader is in the MBR=sda.

---

### Post by Shadowforce on 2010-07-12
> **wilee-nilee said:**
> The bootscript reads that you should be able to boot XP can you? The MS bootloader is in the MBR=sda.

Unfortunately, I currently cannot boot Windows XP.

---

### Post by wilee-nilee on 2010-07-12
> **Shadowforce said:**
> Unfortunately, I currently cannot boot Windows XP.

I'm not sure why XP is not working, I guess you have to choose what you want, you could extract what you need from the XP install with a Ubuntu disc...media..etc, to a external, then just reinstall.

You could install grub and have Ubuntu working right now most likely, this will not fix XP though. You can reinstall XP though with Ubuntu still on the HD and just reload grub to load both in the end.

Did you run the chkdsk from a XP install cd in the command line?

---

### Post by Shadowforce on 2010-07-12
Yes, I did run chkdsk from an XP install cd.
Should I install grub using the directions in the link?

---

### Post by wilee-nilee on 2010-07-12
> **Shadowforce said:**
> Yes, I did run chkdsk from an XP install cd.
Should I install grub using the directions in the link?

Yes the link is correct.

---

