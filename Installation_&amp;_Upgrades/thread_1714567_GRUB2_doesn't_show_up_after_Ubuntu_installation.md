---
title: "GRUB2 doesn't show up after Ubuntu installation"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by d2kx on 2011-03-25
Hi,

I just got the new Lenovo Ideapad S205 which is AMD Fusion-powered and got some problems with Ubuntu. When I install Ubuntu 10.10 or 11.04-daily from USB drive (I don't have an optical drive), GRUB2 doesn't show up after installation and reboot. It just loops, rebooting again and again as if there was nothing installed on the hard drive. By using Google a bit I found someone with a similar problem on an older Lenovo Ideapad where he found that there was a bug that happened that made Ubiquity install GRUB2 on the USB drive instead of the MBR of the hard drive.

1.) Fedora works fine, it's not a hardware problem.

2.) I already tried installing Ubuntu and install GRUB2 from a chroot-environment from the LiveCD-on-USB drive after installation. Didn't change anything (doesn't surprise me, probably same bug).

What do you say to the following possible (?) solutions:

1.) Prepare the USB drive with some allocated space so that Ubuntu can actually write on it. Then hope that it actually installs GRUB2 on there and boots Ubuntu when I have the USB drive with GRUB2 inserted and if it boots, reinstall GRUB2 from there?

2.) Alternate-CD?

3.) Install GRUB2 from another distribution? I tried installing GRUB2 with the root-directory-method form within Fedora 14 and it kinda worked, I had Fedora's GRUB1 (legacy) installed but would need to manually create a /boot/grub/menu.lst etc. because update-grub does not work with that method. Also it would be GRUB1 (legacy) and it's not that clean. Is there another method to install GRUB2 easily?

Other opinions? Don't want to just try out the above without hearing your opinion because it took a lot of  time to set up Fedora the way I want, although at the end I want to use Ubuntu and not Fedora...

Thank you!

- d2kx

---

### Post by Quackers on 2011-03-25
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dutch70 on 2011-03-25
Hi, this may not be much help, but have you tried the following method for installing Grub2 from the Live cd/usb? 

[[COLOR="Blue"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Also, I've reinstalled, actually I should say reinstall Grub 2 almost daily from Kubuntu 10.10. Every time I update Ubuntu 11.04 & Kubuntu 11.04. They take over Grub2. I've never tried it from Fedora though.

---

### Post by d2kx on 2011-03-25
Okay, here is the RESUTS.txt. It looks like GRUB2 is actually installed from this file, but I dont know whats wrong with it. I tried holding down Shift when I turn on the system to maybe see a GRUB2 menu. With that, I see it saying 'Loading GRUB' or something like that and then it just reboots.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   195,522,559   195,520,512  83 Linux
/dev/sda2         195,524,606   976,771,071   781,246,466   5 Extended
/dev/sda5         195,524,608   203,335,679     7,811,072  82 Linux swap / Solaris
/dev/sda6         203,337,728   976,771,071   773,433,344  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4025 MB, 4025810432 bytes
124 heads, 62 sectors/track, 1022 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     7,857,135     7,857,074   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b7d059a2-0e3e-0541-98fb-d8036439377e   ext2       casper-rw                     
/dev/sda1        4ca269b3-9d60-4b74-a305-f21396efcfba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a5af5296-0c67-4af9-ba33-3048c5edc580   swap                                     
/dev/sda6        22b5efe4-f4af-43fe-b242-ec97aaf7b7d0   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        32F4-E30C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
set locale_dir=($root)/boot/grub/locale
set lang=de
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4ca269b3-9d60-4b74-a305-f21396efcfba ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4ca269b3-9d60-4b74-a305-f21396efcfba ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4ca269b3-9d60-4b74-a305-f21396efcfba
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4ca269b3-9d60-4b74-a305-f21396efcfba /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=22b5efe4-f4af-43fe-b242-ec97aaf7b7d0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a5af5296-0c67-4af9-ba33-3048c5edc580 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
  75.5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.35-22-generic
   4.5GB: boot/vmlinuz-2.6.35-22-generic
    .5GB: initrd.img
   4.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 2e 04  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3e 00 00 00  |........?...>...|
00000020  b2 e3 77 00 e9 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0c e3 f4 32 4e  4f 20 4e 41 4d 45 20 20  |..)...2NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-03-25
I see nothing wrong with the boot script output.
The boot script shows that grub2 is installed in the mbr of sda and that grub is looking for its boot files in sda1, which is the correct location of those files.
I see no reason why it will not boot.
You speak in your first post of Ubuntu 10.10 and 11.04. I see only sda1 with Ubuntu and its root partition and sda6, which appears to be Ubuntu's /home partition. There is no sign of Ubuntu 11.04 being installed. This would explain why no grub menu appears, as the system thinks that only one OS is installed, so does not show the grub menu by default.
Are you under the impression that 11.04 is installed as well?

---

### Post by d2kx on 2011-03-25
I tried Ubuntu 11.04, didn't work, formatted, then 10.10, so only 10.10 installed at the moment. I really don't know what's going on. It says "GRUB loading." and then just reboots.

---

### Post by Quackers on 2011-03-25
Sometimes re-installing grub will fix booting problems. There is the short way and the long way :-) The long way replaces all boot files and is more thorough.
We can try the short way first.
Please boot from the Ubuntu live cd/usb and select "try ubuntu" then open up a terminal and copy/paste the following commands in, one line at a time, pressing enter after each line.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
If no errors are reported, please reboot and see if Ubuntu boots up.

---

### Post by d2kx on 2011-03-25
No errors reported, seems to install GRUB2 fine but still doesn't boot "GRUB loading." and then instant reboot :( Trying openSUSE with GRUB1 now, if it also works like Fedora, it may be a GRUB2 problem.

---

### Post by Dutch70 on 2011-03-25
> **d2kx said:**
> No errors reported, seems to install GRUB2 fine but still doesn't boot "GRUB loading." and then instant reboot :( Trying openSUSE with GRUB1 now, if it also works like Fedora, it may be a GRUB2 problem.

You have mentioned Fedora a couple times, do you have it installed to a different hdd, or just had it installed at a different time?

---

### Post by d2kx on 2011-03-26
To make things short: I solved the problem by downgrading to GRUB legacy from a LiveUSB system. It worked fine once GRUB2 was replaced.

---

### Post by Quackers on 2011-03-26
That's a little odd, but glad you sorted it out. It seems that grub legacy and grub2 have been fighting.

---

### Post by Dutch70 on 2011-03-26
> **d2kx said:**
> To make things short: I solved the problem by downgrading to GRUB legacy from a LiveUSB system. It worked fine once GRUB2 was replaced.

Not sure how that happened. Ubuntu 10.10 doesn't use Grub Legacy.
I wonder if the entire thing has something to do with you trying 11.04, which uses Grub2, but it's version 1.99, not 1.98. Must have been a mix up with your (hd,0,0) or w/e numbers. Grub1 counts from (hd,0,1) If I remember correctly.

Anyway, glad you've got it working. It would be nice if you'd give a little more info before marking this thread "Solved" so others with your problem can find it.

Best regards

---

### Post by ottosykora on 2011-03-26
OH I was also thinking of this, but can you tell me how did you do this?
I would also like to replace the grub2 with the legacy grub, which seems to me still more reliable.

I can boot with life CD , connect to net, but then? I need to install the grub legacy to the root partition of the ubuntu only, not to mbr, so need to place it in sda10 in my case.

---

### Post by d2kx on 2011-03-26
I will post how I installed GRUB1 and fixed this very soon, but another question for now:

So it seems my notebook uses UEFI as the BIOS. I did a very short test and replaced grub-pc with grub-efi when I still had the problem but it didn't change anything. Does anyone have additional ideas when keeping in mind that I might need something for EFI?

---

### Post by bejurne on 2011-04-06
I have the same problem with the s205. Out of some reason Grub2 cant deal with EFI...

The simplest solution is to downgrade to grub. I did this with Natty but it should work the same with older Versions.

First boot into the live environment and remove the package grub-pc and install grub. Then mount the harddrive with your ubuntu installation. I mounted it to /mnt

Next install the old grub with

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Now you just need create a new menu.lst and you are good to go. This can be a bit tricky since there is no way to do this automatically. Check for some sample files online and copy the boot parameters from your grub2 config.

Dont forget to downgrade in the actual ubuntu installation as well. Otherwise it will just reinstall grub2 after the next update.

---

### Post by mb36 on 2011-04-21
Please give some more step-by-step information on how to downgrade to grub 1, or actually the whole process of gettind the ideapad S205 running Ubuntu. I seem to have managed to do the downgrading according to the instructions in this and other threads but when I reboot I just get the grub menu, and I don't know how to handle it from there. I tried to enter details like kernel and initrd, and then ran the boot command. A lot of messages flashed by and disappeared before me. It seemed to complain about fstab and other things. I know I should create a menu.lst file but that is beyond me at this point.

---

### Post by oldfred on 2011-04-21
@mb36
HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)


@d2kx
UEFI is just starting to work with grub2. v1.99 as part of Natty.

grub EFI
[http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html](http://www.mail-archive.com/maverick-changes@lists.ubuntu.com/msg01724.html)
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[http://grub.enbug.org/TestingOnUEFI](http://grub.enbug.org/TestingOnUEFI)
UEFI issues srs5694 post #58
[http://ubuntuforums.org/showthread.php?t=1719851&page=6](http://ubuntuforums.org/showthread.php?t=1719851&page=6)
EFI System Partition Subdirectory Registry
[http://www.uefi.org/specs/esp_registry](http://www.uefi.org/specs/esp_registry)
All linux distro installers (Ubuntu included) assume EFISYS partition to be mounted at /boot/efi.


Lots of links and more discussion:
[http://ubuntuforums.org/showthread.php?t=1734677](http://ubuntuforums.org/showthread.php?t=1734677)

---

### Post by mb36 on 2011-04-22
@oldfred: Thanks a lot. I actually found the way, by more or less the same instructions from the "upstream source", that is the community grub2 documentation.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2") 

The problem for people at my level of limited knowledge was how to do it from the live-usb stick. This can be done using the chroot command, which is also covered at another point on the same page.

So this is how got it working:

Go down the page to 12. Reinstalling Grub2/ 3. Method 3 - CHROOT: 

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT]("https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT")

Follow the instructions up to and including step 8 - update-grub

Then go down the page to the following section 13. Uninstalling GRUB/ 1. Reverting to GRUB Legacy:

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

Then you're done. At least this worked for me. 

Next step with the IdeaPad S205 will be to get the wifi working. The applet says something like "wireless is deactivated by hardware". There is a switch on the right side edge of the computer, but it's definitely in the "on" position. Anyone with info or advice on this?

**EDIT**
Wlan now working. First I should say that the S205 ships with either Railink or Atheros wireless card. Mine is Atheros. Got the information from a German forum - [http://www.planet3dnow.de/vbulletin/showthread.php?t=393400]("http://www.planet3dnow.de/vbulletin/showthread.php?t=393400"). This model is not sold in US so less activities and info in English than in German. My German is shaky but it seems one kernel module too many get loaded, so it needs to be removed by modprobe or blacklisted in /etc/modprobe.d. The module is acer_wmi. You might also need some working with the rfkill command.

This is the command I used to get it started on my Live-USB

```
lsmod
sudo modprobe -r acer_wmi
```

Then the wireless fires up. I also used this to see the status.

```
rfkill list all
```

---

### Post by SnappyU on 2011-04-25
Guess we will just have to wait for efi in grub to be properly/fully supported.  At this point, it is still not ready for prime time.

But heck, I just installed it ... :p ... gonna give it a go! hahahaha

---

### Post by freechelmi on 2011-04-29
Hi all , juste got my Lenovo S205 two days ago. Still couldn't install Ubuntu 11.04 ! It's quite the first time i struggle so much.

I've tried several thing : 

- GPT table with the fat EFI partition mounted as /boot/efi and installed Grub-efi on the liveUSB before installing (which led to ia32 version it seems) : grub does not show up , keeps rebooting.

- MBR table (left the fat partition) and replaced grub-pc with grub before installing : same result ! (grub would have failed anyway because of /boot on ext4 I guess) 

I'm a bit about of ideas here, so : 

- Do you think this 205 support Bios emulation ? it seems because a lot of people used Grub1

- What is your feeling about required stuff for UEFI install ? (GPT ? Special label for UEFI partition ? )


ANy help appreciated

---

### Post by ameseisch on 2011-05-20
I had a similar problem with GRUB on the s205. installed 11.04 and after restart it just went right back into windows. like nothing had changed but the hard drive was smaller for the windows partition. Ended up wiping the hard drive and reinstalling. now on boot I have to hit 's' to skip it trying to mount a missing drive/partition. could that be related to something getting mistakenly installed on the usb drive as mentioned earlier? any way to get rid of that?

Thanks for the tip on the wifi. That had me a little stuck. 

I still had some difficulty getting it going but the modprobe -r acer_wmi and rfkill put me on the right track. rfkill wasn't removing the hard block so trued reboot, but then the acer_wmi was back, unblocked all again and modprobe -r acer_wmi again and that did it. not sure how this is going to work down the line though. it would be nice to not have to do that on each boot.

UPDATE: The acer_wmi kept coming back, so added it to /etc/modprobe.d/blacklist-modem.conf and that solved that. However, my hardware switch is now consistently detected as off, and rfkill unblock does nothing for that problem. I know the wifi works fine if I can get past this. 

I found some leads at [http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working](http://askubuntu.com/questions/9816/wireless-shows-up-as-disabled-how-can-i-get-it-working) but so far nothing is working. Any ideas?

---

### Post by rwh on 2011-06-13
I wrote a blog post on how I got Ubuntu 11.04 running on my s205... it shows one way (probably not the best way) to downgrade to GRUB legacy, and two possible solutions for the wifi.

[Installing Ubuntu on the lenovo ideapad S205](http://helms-deep.cable.nu/~rwh/blog/?p=177)

---

### Post by balaoko on 2011-06-30
Thanks rwh. I tried you method but could not pass step 6. My S205 has ubuntu only, with 50GB ubuntu (sda1) and rest disk unpartitioned. since I don't have a partition /boot, I used 'mount --bind /boot ./boot' instead of 'mount /dev/sda6 ./boot' in step 5. At step 6, 'update-grub' was successful but 'grub-install /dev/sda1' failed: 'could not find device for /boot'. Is it possible that I don't need the /boot partition? Thanks a lot.



> **rwh said:**
> I wrote a blog post on how I got Ubuntu 11.04 running on my s205... it shows one way (probably not the best way) to downgrade to GRUB legacy, and two possible solutions for the wifi.

[Installing Ubuntu on the lenovo ideapad S205](http://helms-deep.cable.nu/~rwh/blog/?p=177)

---

### Post by rwh on 2011-07-01
Hi balaoko,

Here's step six, for reference:
> 6. Follow these instructions to download to grub legacy: [https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)
- apt-get update ; apt-get install grub
- update-grub
- yes to generate list
- grub-install /dev/sda6
We’ve now installed grub legacy in /dev/sda6, which is our ubuntu /boot partition.  We now need to get the Windows 7 bootloader to chain-boot this.  We do this using a little utility called EasyBCD, though it’s possible to modify the Windows config files manually if you prefer.

There are a couple of problems I can see with your setup.  First, if you don't have a boot partition, then all of the files that would normally have appeared in the /boot partition will now just live in /boot on the root partition.  So you don't need to use the mount --bind step that you mention.

The other problem is that, as far as I can tell by googling, grub-legacy has no support for ext4 partitions.  That's one reason for having a separate /boot partition formatted ext2.

---

### Post by balaoko on 2011-07-01
Thanks rwh for your generous and prompt help. It sounds clear I have to have a separate /boot partition for a moment.

---

### Post by balaoko on 2011-07-01
> **balaoko said:**
> Thanks rwh for your generous and prompt help. It sounds clear I have to have a separate /boot partition for a moment.

Still failed after using /boot partition. The screen display:
"Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation

This product is covered by one or more of the following patents: blah blah

Realtek PCIe FE Family Controller series v1.23 (07/28/10)
PXE-E61: Media test failure, check cable

PXE-M0F: Exiting PXE ROM"

It sounds like the disk cable is loose after google it. However I can create folder in my HD after booting using my USB stick. So I don't think the connection to the HD is a problem.

What should I do now? Thanks.

---

### Post by balaoko on 2011-07-01
One more thing. When I tried to purge grub-pc, it is not installed. Instead, grub-efi is installed which was removed. Thanks.

---

### Post by balaoko on 2011-07-24
Finally md36's method worked. I didn't use a separate /boot partition. In the last step, update-grub, "yes" to create menu.lst failed. So I manually created an empty menu.lst, which was later updated by running update-grub again. After reboot. Bingo!

z.tutto's method makes wireless work, but is apparently much slow. I used the same method when booting with live CD, and it was very fast, though.

Anyway, finally I can use it as I wanted. Thanks all for your useful information that made it happen :popcorn: :popcorn: :popcorn:

---

