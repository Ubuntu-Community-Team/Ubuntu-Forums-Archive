---
title: "inotify_add_watch 12.04 (crypsetup)"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by 3246251196 on 2012-08-07
I am booting with the 12.04 64bit Desktop CD. The only thing is, I get the problem:

{{example}}: 
```
udevd-work [95]: inotify_add_watch(6, /dev/sdb5, 10) no such directory
```I can hear Ubuntu in the background. I have heard that installing crytsetup will correct this issue, but how to boot into terminal in the first place. How to do an install in the first place to install this package?

===

EDIT1 : 10.10 seems to ignore inotify_add_watch() and continue on. I will now try installing the cryptsetup package from 10.10, then I will try upgrading to 11.04.
EDIT2 : 
```

...ri:~$ sudo apt-get install cryptsetup
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version.
The following package was automatically installed and is no longer required:
  linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 380 not upgraded.
...@...ri:~$

```So, this package is already installed. I know that if I upgrade then, though Ubuntu will load, it will hang on a terminal-like screen with an inotify_add_watch().

---

### Post by 3246251196 on 2012-08-08
Consequently, until I can find out how to merely have that terminal-like screen disappear then I will remain with 10.10.

Thank you for reading, I would love to hear some thoughts as to how to solve this.

---

### Post by 3246251196 on 2012-08-16
The only version of Ubuntu that runs on my system is 10.10 - I have no problems with it. Well, I do: inotify_add_watch pops up in a terminal-like-window in 10.10 but then Ubuntu goes on to continue. However, with 12.04 inotify_add_watch just hangs on the screen and there is not a thing I can do to continue on - I know the system starts up in the background too, which is rather annoying. What is more annoying is the fact that no one has replied to a work-around for this in another thread: [http://ubuntuforums.org/showthread.php?t=2039013](http://ubuntuforums.org/showthread.php?t=2039013)

Anyway, I have 10.10 working fine. I then decide to upgrade to 11.04. Now, upon booting from the grub screen the system just hangs and does nothing. So, I restart and boot into recovery mode: The hanging seems to be after this line:

```
usb 2-1.3: new full speed USB device using uhci_hcd and address 11
```Has anyone came across this issue, or does anyone know how to solve it? The only USB devices connected are mouse, key, microphone. I have tried discon' microphone but that is besides the point anyway as there is no issue in 10.10.

What can be done?

Thank you, I will - as always - patiently wait for an eventual reply and will remain hopeful that someone will, indeed, reply.

324

---

### Post by wildmanne39 on 2012-08-16
Hi, will I am not the best at this but I will at least start you out by asking for information.

Download the script and follow the directions.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

Boot Info Script courtesy of forum members 
meierfra & Gert Hulselmans.
Thanks

---

### Post by wildmanne39 on 2012-08-16
Threads merged! Please do not post duplicates, it dilutes community effort.

---

### Post by 3246251196 on 2012-08-17
Wild Man, thanks for your input, though I fail to see how these are duplicates. Nevertheless, I need to update something:

```
usb 2-1.3: new full speed USB device using uhci_hcd and address 11
```Should be:

```
usb 2-1.3: new full speed USB device using **ehci**_hcd and address **x**
```===

Additionally, how can I run this script when I cannot boot into my Ubuntu (11.04) OS in the first place? I will try booting up to 10.10 Live CD, mounting and then running the script, I guess.

I appreciate your input.

---

### Post by 3246251196 on 2012-08-17
While I hope someone does come up with either a solution, or worse a work-around, it would be nice if I could just go to a terminal screen in either of these situations: Whether it is the inotify hangup or the ehci problem - because the cntrlshift function keys will not work.

This would probably all be good if I could just get past the inotify_add_watch() error that comes beaming with 12.04: And by getting rid of the error I just mean hiding it; since "they" will not fix it at all, even though it has been a problem for a lot of people running raid for years, just a way to hide that terminal-like-screen with the error and bring GDM to the forefront of the screen [ubuntu runs in the background].

10.10 is literally my only option, and it is not supported anymore. It still has the inotify_add_watch() error, but then that screen goes away: what is it that 12.04 fails to do that 10.10 does do to get rid of this screen. What is it that makes 10.10 be able to deal with the EHCI error I now receive having upgraded from 10.10->11.04.

Someone has got to know some information, and I have searched a lot; I will continue searching and troubleshooting, but some additional help would be appreciated. This is not just me either with this inotify problem - or ehci problem.

Thanks.

---

### Post by wildmanne39 on 2012-08-17
Hi, yes you use the livecd, the directions are at the link.
Thanks

---

### Post by 3246251196 on 2012-08-17
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_bibcajihb_Volume0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 3 for /boot/grub.

isw_bibcajihb_Volume01: ________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

isw_bibcajihb_Volume02: ________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

isw_bibcajihb_Volume03: ________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

isw_bibcajihb_Volume04: ________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: isw_bibcajihb_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_bibcajihb_Volume0: 300.1 GB, 300074401792 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586082816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bibcajihb_Volume01   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bibcajihb_Volume02            206,848   513,110,015   512,903,168   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bibcajihb_Volume03        513,110,016   571,703,807    58,593,792  83 Linux
/dev/mapper/isw_bibcajihb_Volume04        571,703,808   586,082,815    14,379,008  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bibcajihb_Volume01 7CBA431BBA42D0F6                       ntfs       System Reserved
/dev/mapper/isw_bibcajihb_Volume02 688EE46D8EE4356A                       ntfs       
/dev/mapper/isw_bibcajihb_Volume03 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e   ext4       
/dev/mapper/isw_bibcajihb_Volume04 09ccd3d2-9205-4cfc-be46-22a868dbe519   swap       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bibcajihb_Volume0
isw_bibcajihb_Volume01
isw_bibcajihb_Volume02
isw_bibcajihb_Volume03
isw_bibcajihb_Volume04

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_bibcajihb_Volume02 /media/688EE46D8EE4356A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/mapper/isw_bibcajihb_Volume03 /media/95d7877b-5ee9-4a8b-a6d9-43dd02368c1e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================== isw_bibcajihb_Volume03/boot/grub/grub.cfg: ==================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos3)'
search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd2,msdos3)'
search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=95d7877b-5ee9-4a8b-a6d9-43dd02368c1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    echo    'Loading Linux 2.6.38-15-generic ...'
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=95d7877b-5ee9-4a8b-a6d9-43dd02368c1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=95d7877b-5ee9-4a8b-a6d9-43dd02368c1e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    echo    'Loading Linux 2.6.35-32-generic ...'
    linux    /boot/vmlinuz-2.6.35-32-generic root=UUID=95d7877b-5ee9-4a8b-a6d9-43dd02368c1e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-32-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos3)'
    search --no-floppy --fs-uuid --set=root 95d7877b-5ee9-4a8b-a6d9-43dd02368c1e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/mapper/isw_bibcajihb_Volume01)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set=root 7CBA431BBA42D0F6
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
--------------------------------------------------------------------------------

====================== isw_bibcajihb_Volume03/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bibcajihb_Volume03 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bibcajihb_Volume04 none            swap    sw              0       0
--------------------------------------------------------------------------------

========== isw_bibcajihb_Volume03: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

 254.926197052 = 273.724919808  boot/grub/core.img                             1
 254.941535950 = 273.741389824  boot/grub/grub.cfg                             1
 246.005859375 = 264.146780160  boot/initrd.img-2.6.35-32-generic              2
 270.969238281 = 290.951004160  boot/initrd.img-2.6.38-15-generic              1
 255.192039490 = 274.010365952  boot/vmlinuz-2.6.35-32-generic                 1
 246.064781189 = 264.210046976  boot/vmlinuz-2.6.38-15-generic                 1
 270.969238281 = 290.951004160  initrd.img                                     1
 246.005859375 = 264.146780160  initrd.img.old                                 2
 246.064781189 = 264.210046976  vmlinuz                                        1
 255.192039490 = 274.010365952  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

```

---

### Post by 3246251196 on 2012-08-18
I used the 12.04 CD today, and had to use ```
nomodeset
``` in order for it to work. Everything is fine. Whether that was the issue with the hanging screen I am not too sure. Either way, nomodeset seems to correct the issue with this newer age nvidia card.

So I go about installing 12.04 from the CD. The only thing is, I install grub to the /dev/mapper/isw_xxxxx (my raid volume) and when I restart the system and select to enter ubuntu from grub I am taken into "busybox".

This is the new problem now, then. I read some instructions:

[http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration/](http://productive.me/blog/installing-ubuntu-64-bit-on-intel-raid-0-configuration/)

I followed those, though I did NOT install kpartx.

So, the guide suggests to install grub onto the raid. Though, on my other system, when I used the alternate installation - it is suggested that grub is installed onto SDA and NOT the raid. So there is a conflict there.

Basically, the new issue is where to correctly install grub to, give that I have a RAID0 configuration:

300GB Raid0 Volume_0
-> NTFS Windows OS ~~270GB Volume01
-> NTFS Windows ~~0.14GB Volume02
-> FREE SPACE ~~30GB

---

### Post by 3246251196 on 2012-08-19
Okay, I tried something else.

Wiped all partitions that were non-windows. Booted with the 10.10 64bit Live CD. This installation gives me the option to install onto /boot on SDA - which, surely, is correct (I am sure 12.04 only gave me the option to install onto SDB/Raid Device).

So, as always 10.10 installs fine without problems.
Booted into 10.10, upgraded to 11.04 for the nth time. Tried to boot into 11.04 from grub, same issues - the screen just hanging. So, this time used **nomodeset** in the boot config and 11.04 is currently up and running.

Currently I am installing the upgrade to 11.10; I am sure I will need to use **nomodeset** for the remainder of the releases until there is a fix for these new video cards.

Anyway, it seems that the issue has not been to do with ehci_hcd, but all along it has been to do with my video card and the need to use **nomodeset**. That is probably why I have had hanging on the screen with: 

```
udevd-work [a]: inotify_add_watch(b, /dev/sdbc, d) no such directory
```
And the screen with:

```
usb 2-1.3: new full speed USB device using ehci_hcd and address x
```

##

I hope I write this post not too soon, and maybe I should have waited until I can confirm, but it is at least a little exciting.

The upgrade to 11.10 is in progress and I will let you know what happens.

One last question: I wonder why the Live CD 12.04 would not allow to install bootloader onto SDA?

---

### Post by 3246251196 on 2012-08-19
I am now writing this post on 12.04 64bit. This is now solved and it was all to do with my newer nVidia card.

It was never the problems that displayed on the screen that hung, rather the fact that the OS could not proceed due to nVidia drivers.

There is still a problem with:

```

inotify_add_watch

```which I would like to see a solution for, as this has been a problem for years. However, this problem is merely put in the background.

There is also a question that I still have:

Why would 12.04 64bit not allow me to install the boot loader to SDA?

###

In summary, if you ever get a hanging screen try to append **nomodeset**  to the [b]linux /boot[b] line of the grub configuration.

---

