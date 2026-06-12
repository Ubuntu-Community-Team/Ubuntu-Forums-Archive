---
title: "Black Screen after install Ubuntu 10.04.2 x64"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by paracelus on 2011-03-17
I recently decided to give Ubuntu another try after a break for a while, and have hit a bit of a road block The live CD booted fine, ran, installed, all flawlessly, so it's now a dual boot with Windows 7. Only issue now is when trying to load the HDD installed Ubuntu, it just hangs on a black screen, no HDD activity light or anything. First up my specs:

DFI Lanparty JR P45-T2RS
4GB DDR2
Q6600
nVidia 8800GT
1x 320GB Samsung Spinpoint Sata II (System drive)
1x 1TB     Samsung Spinpoint Sata II

Next, what happens in detail:

Machine posts, loads boot loader with OS options. Whether choose Ubuntu or recovery Ubuntu, it always hangs on black screen straight after that.

Next, what I have tried to fix it so far:

Tried pressing 'e' and replacing the quiet splash with nomodeset, same result with both normal flavour and recovery.

Tried copying the xorg.conf from the live CD filesystem to X11 folder on main system drive. Also tried editing it to try and use generic vesa driver.

Tried switching DVI outputs.

This is driving me nuts now, I dont get how the Live CD can work perfectly, then it borks on HDD install! Please help! Thanks

---

### Post by Dutch70 on 2011-03-17
Welcome to UF paracelus, 

This is probably over my head, but so someone else can see it, can you post a pic of your hdd in Gparted? 

Also and more importantly, download Boot Info Script & copy/paste the results between code tags (# in the toolbar) on your next post.
You can download it from here...
[[COLOR="Blue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")

---

### Post by paracelus on 2011-03-17
Ok, will try these when get home from work and post back results! Thanks!

---

### Post by sikander3786 on 2011-03-17
Welcome back to Ubuntu :-)

I hope this link will help you. See the section named 'First Boot after installation is over'.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Feel free to ask if you've got any further queries or anything on that page doesn't seem to help.

---

### Post by paracelus on 2011-03-19
Ok, results from boot script as follows:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   506,227,656   506,020,809   7 HPFS/NTFS
/dev/sda3         506,228,734   625,141,759   118,913,026   5 Extended
/dev/sda5         506,228,736   620,195,839   113,967,104  83 Linux
/dev/sda6         620,197,888   625,141,759     4,943,872  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        506C02C06C02A0B8                       ntfs       System Reserved               
/dev/sda2        06BA0654BA064123                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        c5f6a57a-5f90-4c44-86eb-2aefb66db45a   ext4                                     
/dev/sda6        fd003cbb-7fea-4fdc-92a8-d8e20c7b408f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D6F257F5F257D7F7                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
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
search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=c5f6a57a-5f90-4c44-86eb-2aefb66db45a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=c5f6a57a-5f90-4c44-86eb-2aefb66db45a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c5f6a57a-5f90-4c44-86eb-2aefb66db45a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 506c02c06c02a0b8
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
UUID=c5f6a57a-5f90-4c44-86eb-2aefb66db45a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=fd003cbb-7fea-4fdc-92a8-d8e20c7b408f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 261.4GB: boot/grub/core.img
 302.3GB: boot/grub/grub.cfg
 289.7GB: boot/initrd.img-2.6.32-28-generic
 261.4GB: boot/vmlinuz-2.6.32-28-generic
 289.7GB: initrd.img
 261.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  92 f5 43 91 f8 40 8e f5  38 8c f4 34 88 f0 2b 83  |..C..@..8..4..+.|
00000010  ef 26 7e ea 1d 7c e9 1e  7d ea 1c 82 ee 1f 85 f1  |.&~..|..}.......|
00000020  1d 8b f5 20 8e f8 22 8e  f5 1f 8b f2 1d 89 eb 19  |... ..".........|
00000030  85 e7 26 83 d9 24 81 d7  33 81 cd 33 81 cd 41 7b  |..&..$..3..3..A{|
00000040  b3 30 6a a2 33 5a 7f 22  49 6e 26 41 55 27 42 56  |.0j.3Z."In&AU'BV|
00000050  39 4b 4c 38 4a 4b 3b 48  41 3b 48 41 3c 4a 34 37  |9KL8JK;HA;HA<J47|
00000060  45 2f 39 44 28 39 44 28  3d 47 24 3f 49 26 41 45  |E/9D(9D(=G$?I&AE|
00000070  25 47 4b 2b 44 46 26 45  47 27 3e 40 20 3f 41 21  |%GK+DF&EG'>@ ?A!|
00000080  39 3d 1d 3a 3e 1e 33 39  14 33 39 14 31 39 0d 32  |9=.:>.39.39.19.2|
00000090  3a 0e 2b 3a 06 2a 39 05  2a 41 03 2c 43 05 22 43  |:.+:.*9.*A.,C."C|
000000a0  08 1b 3c 01 06 33 00 00  1d 00 00 0b 00 00 02 00  |..<..3..........|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000110  00 0e 00 00 16 01 00 1f  08 00 26 0f 00 29 11 00  |..........&..)..|
00000120  2d 15 01 2f 12 02 30 13  01 31 0d 01 31 0d 10 34  |-../..0..1..1..4|
00000130  09 10 34 09 1f 39 06 1c  36 03 32 38 07 30 36 05  |..4..9..6.28.06.|
00000140  41 33 06 41 33 06 4b 2d  0c 48 2a 09 53 28 0f 52  |A3.A3.K-.H*.S(.R|
00000150  27 0e 4d 1f 15 4e 20 16  4a 1c 1f 4e 20 23 3a 1d  |'.M..N .J..N #:.|
00000160  2a 3c 1f 2c 26 1d 32 22  19 2e 04 16 29 03 15 28  |*<.,&.2"....)..(|
00000170  00 1a 28 00 1b 29 00 24  27 00 26 29 00 2f 27 00  |..(..).$'.&)./'.|
00000180  2f 27 00 2e 25 00 2f 26  00 30 27 00 32 29 05 2f  |/'..%./&.0'.2)./|
00000190  2c 02 2c 29 09 23 25 06  20 22 09 22 12 09 22 12  |,.,).#%. "."..".|
000001a0  0c 29 01 01 1e 00 00 1d  00 00 13 00 00 21 00 00  |.)...........!..|
000001b0  21 00 00 2b 00 00 2b 00  00 36 00 00 36 00 00 ef  |!..+..+..6..6...|
000001c0  ff ff 83 ef ff ff 02 00  00 00 00 00 cb 06 00 ef  |................|
000001d0  ff ff 05 ef ff ff 02 00  cb 06 00 78 4b 00 00 00  |...........xK...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============


```

Please, tell me there is a solution!

---

### Post by Quackers on 2011-03-19
There is always a solution :-)
It seems that you have both a wubi installation and a partition installation of Ubuntu. I have no experience at all with wubi, but I suspect that the two installations may be conflicting (as far as booting goes). I would recommend that you backup anything that you may need in your wubi install (the one within Windows) and then delete all traces of that installation from within Windows. Then reboot into Windows, to make sure it's still happy :-)
Then reboot again and try Ubuntu. It may boot. If it doesn't we can try re-installing grub.

---

### Post by kansasnoob on 2011-03-20
I have a rather dumb question :redface:

Does your "boot" screen look like this:

[ATTACH]186626[/ATTACH]

Or like this:

[ATTACH]186627[/ATTACH]

---

### Post by paracelus on 2011-03-20
First one, it's def GRUB. Hmm, ok, have removed the WUBI install, lets try a reboot :)

---

### Post by paracelus on 2011-03-20
Ok. Windows still boots fine, but no change on the Ubuntu options, still blank screen.

I'm half tempted to wipe the drive completley and try having a pure Ubuntu install, no Windows, as a test.

---

### Post by paracelus on 2011-03-20
Right. Completely wiped primary drive, installed Ubuntu, now get this: 

```


[       1.980993] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
_


```

---

### Post by Dutch70 on 2011-03-20
Can you boot to the live cd or usb with no problems? If so, try re-installing Grub if you're sure you totally got rid of Wubi.

[[COLOR="Blue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you can't boot to the live cd/usb, you may have to choose nomodeset at start up by hitting the f6 key when it gets to the purple screen. 
I can't remember exactly how it's done, as I've never had to do it, but more than a few people have had to, if you wanna search around.

---

### Post by Quackers on 2011-03-20
That's a kernel panic, often caused by a hardware problem.
Have you had Ubuntu booting before on your system?
Have you tried selecting "try ubuntu" from the live cd, to see if it runs on your hardware?

---

### Post by paracelus on 2011-03-20
Yeah the LiveCD boots and runs fine, infact using it at the moment! :) It runs great, really don't get why it has an issue on HDD install

---

### Post by Quackers on 2011-03-20
From the live cd desktop please go to System > Admin > gparted and open it. Does it show any details for your hard drive (probably /dev/sda)?

---

### Post by paracelus on 2011-03-20
Attached a screenshot :)

---

### Post by Quackers on 2011-03-20
Ok thanks. It's definitely installed now :-)
I'm not an expert on dealing with kernel panics. I've only had one or two and they resolved themselves with reboots.
Try booting a couple more times and see if it can boot eventually.
If that doesn't work, when booting up hold down the shift key. This will interrupt the boot process to display the grub menu. When the grub menu appears the top (highlighted) entry will be Ubuntu. Press the "e" key and you will see a different screen. Using your arrow keys, navigate to the end of the line which says "quiet splash". Leaving a space after that, type in acpi=off, then press 
ctrl + X to boot. See if that boots then come back here please.

---

### Post by paracelus on 2011-03-20
I get the same error, but with Disabled IRQ 18 before it. :(

---

### Post by Quackers on 2011-03-20
I don't know how to find out what IRQ18 is, except for google. You could also google for other Linux boot options - there are many.

---

### Post by paracelus on 2011-03-20
Bleh. At this point I'm tempted to give up for another few versions. Sucks, always preferred using Linux for primary OS, but this is kind of beyond reasonable setup.

---

### Post by Quackers on 2011-03-20
That's unfortunate.
What you could try is version 10.10, as there are different hardware capabilities in that. You may find that that version will boot.
Sorry, but that's all I can think of.
I have asked another member to have a look at your problem, but he appears to be offline at the moment.

---

### Post by Dutch70 on 2011-03-20
Did you try re-installing Grub from the live cd, with the link I gave you. Its not difficult at all. 

As a matter of fact, just boot to the live cd and run these 2 commands.
```
sudo mount /dev/sda1 /mnt
```

and then...
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot & see if you can log-in to Ubuntu.

---

### Post by coffeecat on 2011-03-20
Hi

You're getting the kernel panic with the hard drive install, but not the live CD? Odd.

I've found what might be a relevant bug, even though it involves the 32-bit server version:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720865?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/720865?comments=all)

Doesn't seem to much activity there, so I'd point the finger at a buggy BIOS in your machine. In which case there's a few more kernel parameters to try here:

[http://linux.koolsolutions.com/2008/03/04/vfs-kernel-panic-error-acpi-and-apic-issues-part-1/](http://linux.koolsolutions.com/2008/03/04/vfs-kernel-panic-error-acpi-and-apic-issues-part-1/)

"acpi=off" has been a popular cure-all. The link is a bit dated, mentioning legacy grub and lilo, but you can add the parameters at the grub 2 menu the way you have been doing with 'e'.   

**EDIT**:

> **Quackers said:**
> I have asked another member to have a look at  your problem, but he appears to be offline at the moment.

I'm back! :)

---

