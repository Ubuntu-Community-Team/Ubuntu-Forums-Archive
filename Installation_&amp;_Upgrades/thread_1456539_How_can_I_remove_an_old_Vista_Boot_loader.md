---
title: "How can I remove an old Vista Boot loader"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by James2k on 2010-04-17
Hey Ubuntu community,

I've just came across something rather strange. I've been having a problem with GRUB 2 and Windows as highlighted in this thread:

[http://ubuntuforums.org/showthread.php?t=1322942](http://ubuntuforums.org/showthread.php?t=1322942)

Often when I attempt to access my Windows partition from GRUB I will get the Windows failed to start error, but today I may have found something rather interesting that may help me solve my problem. Sorry if it looks like im double posting, but im asking something different.

Basically when Windows fails to boot it restarts and when I attempt to boot it again I usually get the Windows failed to start screen with the option to run Startup and Repair when I ran it earlier, I suddenly saw the Windows Vista Loading bar, which is rather impossible as im running Windows 7. But my laptop came pre-loaded with Windows Vista as well as a recovery partition with Windows Vista on it. I thought I'd removed them both completely but now seeing the Windows Vista Loading screen says otherwise. It looks like some part of the Vista loader remains and well could be the cause of my boot issues.

So im wondering how can I go about fully removing the Windows Vista Boot loader?

---

### Post by bumanie on 2010-04-17
As far as I remember, the vista bootloader and the win 7 bootloader are the same and should be able to boot each other, however it may be that only one or two vista boot files are left which will not give a completed boot. If it were me, i would repair the win 7 bootloader and then reinstall grub. It is not unusual for part of a bootloader to get left behind. If that doesn't work, you could zero the drive and start from scratch - zeroing a drive will wipe everything on there. To do this use darik's boot and nuke live cd or use dd commands from a live ubuntu cd > dd if=/dev/zero of=/dev/sdx replacing the x in /dev/sdx with the drive letter you are wishing to zero eg /dev/sda

---

### Post by oldfred on 2010-04-17
Have you run the boot info script as it probes the MBR and PBR to see what it there:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Your Vista bits may be because you had two windows installs and windows combines boot moving boot files to the windows active (boot flag) partition.
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by James2k on 2010-04-17
Thanks for your replies. I'd rather not Nuke my HDD until im all out of options. The various FixMBR and FixBoot commands don't solve my problem. So I'll just that Boot info script and see if anything is there.

---

### Post by James2k on 2010-04-17
> **James2k said:**
> Thanks for your replies. I'd rather not Nuke my HDD until im all out of options. The various FixMBR and FixBoot commands don't solve my problem. So I'll just that Boot info script and see if anything is there.

Here what I got from the boot script

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   218,204,886   218,204,824   7 HPFS/NTFS
/dev/sda2         291,606,528   312,578,047    20,971,520   7 HPFS/NTFS
/dev/sda3         218,210,895   291,595,814    73,384,920   5 Extended
/dev/sda5         218,210,958   288,495,269    70,284,312  83 Linux
/dev/sda6         288,495,333   291,595,814     3,100,482  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        829C99399C992925                       ntfs                                     
/dev/sda2        EAF8F5BEF8F588D9                       ntfs       College Work Backup           
/dev/sda3: PTTYPE="dos" 
/dev/sda5        df97da0b-a902-4779-b4ef-bdfad7c6ca92   ext4                                     
/dev/sda6        b299e17d-f687-48f6-bfda-4429d1eb4086   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /mnt/collegework         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1        /mnt/windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


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
set default="4"
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
search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
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
search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=20
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
    search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
    linux    /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 ro   quiet splash ipv6.disable=1 acpi=force
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set df97da0b-a902-4779-b4ef-bdfad7c6ca92
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 829c99399c992925
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda5 :
UUID=df97da0b-a902-4779-b4ef-bdfad7c6ca92    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=EAF8F5BEF8F588D9    /mnt/collegework    ntfs    defaults,“umask=022&#8243;    0    0
#Entry for /dev/sda1 :
UUID=829C99399C992925    /mnt/windows    ntfs    defaults,“umask=022&#8243;    0    0
#Entry for /dev/sda6 :
UUID=b299e17d-f687-48f6-bfda-4429d1eb4086    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0



=================== sda5: Location of files loaded by Grub: ===================


 111.9GB: boot/grub/core.img
 115.1GB: boot/grub/grub.cfg
 124.5GB: boot/initrd.img-2.6.32-21-generic
 113.5GB: boot/vmlinuz-2.6.32-21-generic
 124.5GB: initrd.img
 113.5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by oldfred on 2010-04-17
While the script tries to tell Vista from 7 is may not always be correct. It looks like everything is win7 and looks normal to me. I think your issues is purely windows and perhaps they have a solution.

---

