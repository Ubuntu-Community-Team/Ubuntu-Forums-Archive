---
title: "Dual boot issues with XP"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by EddyOS on 2011-02-23
It's not so much an issue but a question...

I have Windows XP SP3 running on my Desktop PC and wish to dual boot it with Ubuntu 10.10. This isn't the issue as I can do this and it gives me the GRUB menu but selecting Windows XP won't do anything - or so it seems

How long should it take to boot into Windows from the GRUB menu?

---

### Post by sikander3786 on 2011-02-23
Welcome to the forums :-)

It shouldn't take more than half a second to boot Windows XP.

Please boot Ubuntu and post the output of bootinfoscript as per instructions here to let us see what is going wrong in there.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by EddyOS on 2011-02-23
Nice one, will have a blast when I get home - had to reinstall XP from scratch to get it working so not set Ubuntu back up yet but will do ASAP

Hopefully it's something simple but all I can tell you at the mo is it just goes to a black screen with a flashing cursor

---

### Post by sikander3786 on 2011-02-23
> **EddyOS said:**
> Nice one, will have a blast when I get home - had to reinstall XP from scratch to get it working so not set Ubuntu back up yet but will do ASAP

Hopefully it's something simple but all I can tell you at the mo is it just goes to a black screen with a flashing cursor
Do you mean you installed Windows after the installation of Ubuntu? And it is Ubuntu going to the blinking cursor or Windows XP?

If you are not able to boot Ubuntu from the HDD, you need to run the boot script from a Live Ubuntu CD/USB.

---

### Post by EddyOS on 2011-02-23
No, Windows was running before Ubuntu. I then got the Ubuntu CD and installed it on an EXT4 partition which GPartEd sorted out from the existing single HDD. I then allowed Ubuntu to get all the updates it needed and made sure it was all working then rebooted the PC and on the GRUB list I chose Windows XP and it just sat there on a black screen

If I reboot again and choose Ubuntu it loads fine so it seems to affect the dual boot side getting into Windows

---

### Post by sikander3786 on 2011-02-23
Ok. The boot script output will tell us.

---

### Post by FoxEWolf on 2011-02-23
Before I can really help you, I need to clarify the order in which you had the OS's on your HDD. Did you Install Windows before or after Meerkat? I want to be able to decide whether it was an issue with the WUBI install process or whether you just have an issue with the install of XP inside the partition. 

Can you still get into Ubuntu?

---

### Post by EddyOS on 2011-02-23
Windows was in situ **before** Ubuntu - I had tried it via a VirtualBox VM but wanted to see how it ran on my Desktop natively. It was after adding Ubuntu to the party that I experienced issues. I'd booted from the CD to install Ubuntu not through Windows if that helps to clarify things

And yes, Ubuntu could be accessed from the GRUB menu, it was only XP that failed to boot. As it stands this second I had to reformat and have just got XP on it's own

---

### Post by TheGrave on 2011-02-24
Exactly the same issue here, here is my output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sda2         409,602,048   471,042,047    61,440,000  83 Linux
/dev/sda3         471,042,048   488,396,799    17,354,752  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1              16,065 1,953,520,064 1,953,504,000   f W95 Ext d (LBA)
/dev/sdb5              16,128   838,882,169   838,866,042   7 HPFS/NTFS
/dev/sdb6         838,882,233 1,090,540,394   251,658,162   7 HPFS/NTFS
/dev/sdb7       1,090,540,458 1,300,252,904   209,712,447   7 HPFS/NTFS
/dev/sdb8       1,300,252,968 1,953,520,064   653,267,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        262A0FCE2A0F99C7                       ntfs       Storage                       
/dev/sda2        ce3a9015-138e-4b09-a70a-c9572bc85c76   ext4                                     
/dev/sda3        fc3e5257-9024-41f1-b814-caa901387826   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1: PTTYPE="dos" 
/dev/sdb5        6C70CB5870CB2822                       ntfs       Music                         
/dev/sdb6        9CACA0ACACA081FE                       ntfs       Software & Pictures           
/dev/sdb7        56CC1D71CC1D4D1D                       ntfs       Others                        
/dev/sdb8        649494429494191E                       ntfs       Backup                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /execute /fastdetect /nopae 
[spybotsd] 
timeout.old=30 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ce3a9015-138e-4b09-a70a-c9572bc85c76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=ce3a9015-138e-4b09-a70a-c9572bc85c76 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ce3a9015-138e-4b09-a70a-c9572bc85c76 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ce3a9015-138e-4b09-a70a-c9572bc85c76 ro single 
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set ce3a9015-138e-4b09-a70a-c9572bc85c76
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 262a0fce2a0f99c7
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=ce3a9015-138e-4b09-a70a-c9572bc85c76 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=fc3e5257-9024-41f1-b814-caa901387826 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 233.7GB: boot/grub/core.img
 218.8GB: boot/grub/grub.cfg
 210.6GB: boot/initrd.img-2.6.35-22-generic
 210.7GB: boot/initrd.img-2.6.35-25-generic
 233.7GB: boot/vmlinuz-2.6.35-22-generic
 233.8GB: boot/vmlinuz-2.6.35-25-generic
 210.7GB: initrd.img
 210.6GB: initrd.img.old
 233.8GB: vmlinuz
 233.7GB: vmlinuz.old
```

---

### Post by TheGrave on 2011-02-28
Just managed to fix the issue. There is a package called testdisk. Select the correct drive and go through the options until you find "BS Recovery". This small utility will scan your bootsector and fix it to match the new partition structure. Then simply boot windows via grub. If this doesn't help (which I highly doubt) you can boot WIndows from Hiren (there is an entry "Boot in WinXP (NTLDR)", run scandisk for the partions on the resized drive and their size will be corrected in the MFT.

---

