---
title: "Dual boot. Windows 7 wont boot"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by PigFoot55 on 2011-02-09
Hi everyone,
i have a little problem here. I bought my notebook few months ago with pre-installed Windows 7. Ive decided to try Ubuntu (v10.10) so I installed it "alongside with windows" .But I chose the "choose partitions automatically"   That was the mistake I quess.

Now when I restart and get to the GRUB screen I can see Ubuntu,memory,window7 and vista. But when I choose Windows 7 It just clears the screen for a second and jumps back to the GRUB screen.

Ive tried repairing StartUp with the windows recovery CD (first time it found some problems with disk,fixed it but didnt help. Tried it two more times but no problems found now)

Here is log from boot_info_script :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 862886560 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 has 
                       30722047 sectors, but according to the info from 
                       fdisk, it has 30943279 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500,1 GB, 500 107 862 016 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 60 801, celkem 976 773 168 sektor&#367;
Jednotky = sektory po 1 * 512 = 512 bajtech
Velikost sektoru (logického/fyzického): 512 bajt&#367; / 512 bajt&#367;

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       411,647       409,600   7 HPFS/NTFS
/dev/sda2             411,648   535,437,219   535,025,572   7 HPFS/NTFS
/dev/sda3         535,437,310   945,829,887   410,392,578   f W95 Ext d (LBA)
/dev/sda5         885,022,720   945,829,887    60,807,168   7 HPFS/NTFS
/dev/sda6         535,437,312   870,756,351   335,319,040  83 Linux
/dev/sda7         870,758,400   885,020,671    14,262,272  82 Linux swap / Solaris
/dev/sda4         945,829,888   976,773,167    30,943,280  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda: PTTYPE="dos" 
/dev/sda1        CA8A74088A73EF77                       ntfs                                     
/dev/sda2        64BE7652BE761CAC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        44527EE9527EDEDC                       ntfs       LENOVO_PART                   
/dev/sda5        9642B14E42B133B9                       ntfs       LENOVO                        
/dev/sda6        ae78be8d-0395-4c0a-a419-b023a5dada6b   ext4                                     
/dev/sda7        04983b51-2442-4666-a4f3-5adae7e17901   swap                                     
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/RecoveryDisc001   udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


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
search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
set locale_dir=($root)/boot/grub/locale
set lang=cs
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set ae78be8d-0395-4c0a-a419-b023a5dada6b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ca8a74088a73ef77
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 44527ee9527ededc
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
UUID=ae78be8d-0395-4c0a-a419-b023a5dada6b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=04983b51-2442-4666-a4f3-5adae7e17901 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 441.7GB: boot/grub/core.img
 308.7GB: boot/grub/grub.cfg
 275.1GB: boot/initrd.img-2.6.35-25-generic-pae
 441.7GB: boot/vmlinuz-2.6.35-25-generic-pae
 275.1GB: initrd.img
 441.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```Thanks for any help/advice

---

### Post by Quackers on 2011-02-09
Which Windows entry are you trying to boot?

---

### Post by kansasnoob on 2011-02-09
You've installed grub to the boot sector of the Windows boot partition:

> sda1: _________________________________________________________________________

    File system:       ntfs
    [B][COLOR="Red"]Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 862886560 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR][/B]
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

That's discussed here along with the fix:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Once you've fixed that you'll need to restore grub2 to the MBR using your 10.10 Live CD and running:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Then after booting into your installed Ubuntu run:

```
sudo update-grub
```

---

### Post by PigFoot55 on 2011-02-09
Windows 7 (loader) (on /dev/sda1

If that is what are you asking for

---

### Post by Quackers on 2011-02-09
Yes it was, thanks.
Kansasnoob is correct. You have installed grub to the sda1 partition, whereas it should be installed to the mbr of the drive (sda).
If you follow kansasnoobs fixes you should be good.
One oddity in your boot script output is that in os-prober part of the grub.cfg file, the Windows loader seems to be pointing to the wrong partition (hd0,msdos3), even though it states sda1.
This should be fixed using kansasnoobs guide.

---

### Post by PigFoot55 on 2011-02-09
Oh guys thank you for such a quick help. I will let you know how it goes

but I dont understand how is all that possible. I let Ubuntu decide,where it should install it self and hoped that it is smart enough not to screw my sestem up...followed the Recommanded options and still it install where it shouldn.

---

### Post by Quackers on 2011-02-09
Usually, by default, grub will install to sda. It is usually only via user input that it goes in sda1. That is strange.

---

### Post by PigFoot55 on 2011-02-09
Im a bit ashamed to ask this. I got the the point where the testdisk aks me "
Select the Windows system partition"

And Im not sure,which one to select.Im sending a picture
Yeah I know its lame and stupid question but I think its better to ask than to cry later :D

---

### Post by Quackers on 2011-02-09
As I don't know if kansasnoob is about, I will say that, as I've not used testdisk to repair the Windows bootloader I am unsure. I would suspect, however, that it is the first partition, as that has the first two Windows boot files in it.

Edit: And it's not a stupid question! It's much better to get it right first time. If that means asking, then ask!

---

### Post by PigFoot55 on 2011-02-09
Still not sure about those partitions...there are 2 NTFS. The smaller should be for windows system files and the bigger for the rest of windows normal files.But not sure about that

---

### Post by kansasnoob on 2011-02-09
> **Quackers said:**
> As I don't know if kansasnoob is about, I will say that, as I've not used testdisk to repair the Windows bootloader I am unsure. I would suspect, however, that it is the first partition, as that has the first two Windows boot files in it.

Edit: And it's not a stupid question! It's much better to get it right first time. If that means asking, then ask!

When in doubt look at the partition size, according to fdisk:

```
/dev/sda1    *          2,048       411,647       **409,600**   7 HPFS/NTFS
/dev/sda2             411,648   535,437,219   **535,025,572**   7 HPFS/NTFS
```

And then look at the screenshot of TestDisk in post #8. According to that it's definitely partition #1.

I'm digging out from no less than 14" of snow, in places it's nearly 2 feet deep, so I'll be busy for a while :p

At least I don't have to play tax preparer today :lolflag:

---

### Post by kansasnoob on 2011-02-09
> **PigFoot55 said:**
> Still not sure about those partitions...there are 2 NTFS. The smaller should be for windows system files and the bigger for the rest of windows normal files.But not sure about that

It's the one you had highlighted in post #8.

---

### Post by Quackers on 2011-02-09
I understand what you are saying, kansasnoob, but from the guide you linked to the words " Fifth   screen:  Select the Windows system partition  and choose "boot""
may cause confusion, as some might consider the "system partition" to be the main Windows partition - not unreasonably I would say :-)

Happy digging to you :-)

---

### Post by kansasnoob on 2011-02-09
There are actually three ways to tell. First, TestDisk is run from Linux so generally the device designations are the same as Ubuntu other than the first two letters possibly being "hd" instead of "sd". The second is the boot flag represented by a "*". And the third is partition size.

My fingers are warm so back to the shoveling, sure wish I hadn't given my tractor to my son right now.

---

### Post by PigFoot55 on 2011-02-09
You guys are just Awesome ! Everything ready and working as its supposed to !

Thank you both for your time and help. I would help you at least with the snow in return, but I guess we are thousend of kilometer from each other :)

Can I give you some Plus points or anything like that (like on other forums)?


Solved !

---

### Post by Quackers on 2011-02-09
Excellent :-)
Nice one kansasnoob :-)
No plus points, but a small fish would be nice :-)

---

### Post by kansasnoob on 2011-02-09
> **Quackers said:**
> Excellent :-)
Nice one kansasnoob :-)
No plus points, but **a small fish would be nice** :-)

Halibut for supper tonight! And I promise not choke on the bones :D

---

### Post by kansasnoob on 2011-02-09
> **Quackers said:**
> I understand what you are saying, kansasnoob, but from the guide you linked to the words " Fifth   screen:  Select the Windows system partition  and choose "boot""
may cause confusion, as some might consider the "system partition" to be the main Windows partition - not unreasonably I would say :-)

Happy digging to you :-)

Just getting ready to head out on the labor end of the shovel again and I thought this needed additional comment. I think you may be right.

I've hammered hard for some changes to the BIS itself:

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692/topic/4058900)

I have a lot to follow up on there and I'm seriously stressed for time so I'm reluctant to add another task, but I think a simple "rewrite" of those instructions would be good, better yet would be HowTo here on the forums with some screenshots.

But I'm following up on quite a few bugs and I'm already many days behind on other tasks, I need to prepare for iso/upgrade testing for 10.04.2 so I can perform "full disc", "auto-resize", and "manual partitioning" tests along with upgrade testing, both from 8.04.4 and 9.10, in just the next few days.

My plate is simply full.

---

