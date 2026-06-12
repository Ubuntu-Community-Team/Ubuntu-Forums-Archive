---
title: "install failure on HP h8-1120"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by pgarossino on 2011-11-25
I am facing a kernel panic at the end of the install process that prevents the install from proceeding.

The machine is a an HP Pavilion HPE h8-1120 
It has a Hitachi 1Tbyte hard drive and an nVidia GT530 graphics card.

It has windows 7 installed upon delivery.

I have tried both 11.10 and 11.04 installs from ISO.  Both do the same thing.

They boot up initally and let me go through the entire install process up to and including downloading the files and installing the system.

At that point I get the installation complete GUI and when I hit "restart now" the GUI disappears, the CD drive opens, the screen then goes black and I get a text report in white text on a black background that looks like a shutdown sequence.  In the foreground is the ubuntu dots, 5 of them in purple and white with a red dot cycling along them over and over.  Also in purple is a message asking me to remove the install media and hit "return".

When I hit return the purple stuff vanishes and is replaced with more white text on a black background which initially looks like the continuation of the shutdown and restart sequence.  When it hits the restart things seem to come off the rails.  I get:

[ 3411.994179] BUG: unable to handle kernel paging request at 

and then some memory address.

There is a bit more of this kind of thing with various RIP type messages.  The last line is a CR2 reference.

I have used this CD to build several 11.04 boxes recently with no issues, but they were Lenovo boxes, different BIOS and different disk partitioning.

The box is definitely dead at this point.  The only way out is a power cycle at which point the box runs the original windows boot sector stuff and comes up in windows 7.

Has anyone run into this situation with this HP equipment.  This is the very first time I have purchased and HP box and so far it has been a less than satisfying experience in the Linux world.

Paul

---

### Post by Quackers on 2011-11-25
Welcome to UF.
How many partitions is Windows using and what are they called? Have a look in Windows Disk Management screen and report.

---

### Post by pgarossino on 2011-11-25
Windows is using 3 partitions.  One for the C: drive, one for the HP recovery area and one named System.

They are on /dev/sda1,2,3

I resized the C partition to give me room to install ubuntu.

---

### Post by Quackers on 2011-11-25
Hmm, interesting. Was there one called HP_TOOLS at any time?

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by pgarossino on 2011-11-25
Nope, no HP_Tools at any time.

I will proceed with your request and be back in a bit..........................

thanks for the help.

BTW I have been through HP support but they gave up completely on the dual boot issue as might be expected as they don't ship with linux installed and didn't want to get into the minutea of what may be happening.........

---

### Post by Quackers on 2011-11-25
HP are unlikely to be of any help in this respect :-)

---

### Post by pgarossino on 2011-11-25
here is the output from the bootinfo script:

```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

```

---

### Post by Quackers on 2011-11-25
You appear to have chopped off most of the contents of Results.txt
Can you re-post the full file please? :-)

---

### Post by pgarossino on 2011-11-25
One thing I noticed when running from the CD, I got a brief flash on the screen at the very start with the message:

Error: "prefix" is not set

I don't know if this is important.  I don't remember seeing this message when I used this disk for an install just recently on a Lenovo box.

---

### Post by pgarossino on 2011-11-25
Oops sorry, here is the full file:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   289,662,975   289,456,128   7 NTFS / exFAT / HPFS
/dev/sda3       1,928,062,976 1,953,521,663    25,458,688   7 NTFS / exFAT / HPFS
/dev/sda4         289,665,022 1,928,060,927 1,638,395,906   5 Extended
/dev/sda5         289,665,024   320,913,407    31,248,384  82 Linux swap / Solaris
/dev/sda6         320,915,456 1,928,060,927 1,607,145,472  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        422CAFEC2CAFD8E5                       ntfs       SYSTEM
/dev/sda2        6C74B65C74B6292A                       ntfs       OS
/dev/sda3        88F2D148F2D13B60                       ntfs       HP_RECOVERY
/dev/sda5        4d8f05b1-e94f-4941-9766-f05bf8b17590   swap
/dev/sda6        e4d2ae59-862d-4f50-8437-bf254521732d   ext4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos6)'
        search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=e4d2ae59-862d-4f50-8437-bf254521732d ro   quiet splash vt.handoff=7
        initrd  /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        set gfxpayload=$linux_gfx_mode
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos6)'
        search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
        echo    'Loading Linux 2.6.38-8-generic ...'
        linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=e4d2ae59-862d-4f50-8437-bf254521732d ro single
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos6)'
        search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(/dev/sda,msdos6)'
        search --no-floppy --fs-uuid --set=root e4d2ae59-862d-4f50-8437-bf254521732d
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos1)'
        search --no-floppy --fs-uuid --set=root 422CAFEC2CAFD8E5
        chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos2)'
        search --no-floppy --fs-uuid --set=root 6C74B65C74B6292A
        chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(/dev/sda,msdos3)'
        search --no-floppy --fs-uuid --set=root 88F2D148F2D13B60
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=e4d2ae59-862d-4f50-8437-bf254521732d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4d8f05b1-e94f-4941-9766-f05bf8b17590 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 605.341091156 = 649.980047360  boot/grub/grub.cfg                             1
 154.704101562 = 166.112264192  boot/initrd.img-2.6.38-8-generic               2
 157.157230377 = 168.746291200  boot/vmlinuz-2.6.38-8-generic                  1
 154.704101562 = 166.112264192  initrd.img                                     2
 157.157230377 = 168.746291200  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde


```

---

### Post by Quackers on 2011-11-25
Grub has not been installed to the MBR of the drive. I'm not sure why that hasn't happened if there were no errors shown toward the end of the installation.
We can try to install it now with a couple of commands but I would first ask if you have a Windows 7 repair disc? That's a repair CD, not a recovery dvd or recovery partition. You may need this disc if something goes wrong. It's easy enough to make one from within your Windows system, if you don't already have one.

Go to Control Panel and then Backup & Restore Centre and in the left pane click on "make a recovery CD" then pop a CD in the drive and a few seconds later you will have one.

When you have that repair disc boot from the Ubuntu live cd/usb again and select "try Ubuntu". When the desktop loads open up a terminal and copy/paste these commands in, one at a time, pressing enter after each line.
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
This should report No Errors. If that is the case please reboot and see what happens.

---

### Post by pgarossino on 2011-11-25
BINGO!!

That did it.  It appears that the system is on board and intact and GRUB now gives me the option to boot into Ubuntu at startup.

Thank-you very much for your most timely and professional assistance.  I am sure I would never have gotten here by myself.

Ciao,
Paolo

---

### Post by Quackers on 2011-11-25
Excellent :-) You're welcome!
So the grub menu gives you a choice between Windows and Ubuntu?
If not run ```
sudo update-grub
``` in a terminal.

I don't know why grub did not install during the Ubuntu installation, though it is not the first time I have seen it. Very curious.

Happy Ubuntu-ing :-)

Please mark the thread as solved using Thread Tools near the top right of this page.

---

### Post by darkod on 2011-11-25
One more strange thing is that the script reports the file wubildr on /dev/sda3 but there is no full wubi install.

Not sure if this will interfere if you ever try to boot /dev/sda3 which is the recovery partition.

---

### Post by Quackers on 2011-11-25
> **darkod said:**
> One more strange thing is that the script reports the file wubildr on /dev/sda3 but there is no full wubi install.

Not sure if this will interfere if you ever try to boot /dev/sda3 which is the recovery partition.
Yes, that's true. I forgot about that :-)
Have you ever installed Ubuntu via wubi?
It may indeed stop the recovery partition from booting and should be removed I would say.

---

### Post by pgarossino on 2011-11-25
I did a WUBI install of 11.10 which I gave up on as I didn't have control over the partitioning and I just could not stand 11.10 with respect to mouse focus, window roll-up etc.  All things that I  use alot on various linuxes and seemed to be unnaturally complicated on 11.10.  I also can't stand the Unity desktop and tried to get back to the ubuntu classic gnome desktop which I succeeded in doing with the exception that double click roll-up on the window title bar would never work.  I just don't want to live without that.

I then did a full restore of windows, including a rebuild of the partitioning prior to trying again with the 11.04 install ISO.  I don't know why the wubi stuff would still be there.  I'll take a look at that.  Thanks for the head's up.

---

