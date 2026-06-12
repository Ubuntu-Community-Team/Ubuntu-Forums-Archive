---
title: "No boot loader change after install on XP"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by pcreqeust on 2010-08-29
I have been installing 10.4 on machines with much success from USB.  This is really the first Linux distro I have been excited about. I'm having problems on one machine though.  It is a Dell Precision T5400 with a RAID 0 on Dell 6/iR Adapter controller.  I booted to USB no problem, just like I did on my netbook, and laptop and did a pretty standard install.  I'm dual booting to XP on this workstation.  After the installer completed, I didn't see a grub menu.  It's like nothing happened.  Of course in Windows I see less drive space now since I had allocated that for Ubuntu in the Ubuntu setup.  To clarify, I am not using Wubi.

---

### Post by wilee-nilee on 2010-08-29
Post the bootscript in my signature in code tags as described.

Some Dells have a program in windows that you should know about to look for if needed, in control panel add/remove programs.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

If you do have the data safe program, and remove it you may need to reload grub2 to the mbr
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by pcreqeust on 2010-08-29
I'm confident I don't have the DataSafe program.  I installed XP from my  own media w/o Dell helper discs, and I try to run lean.  I don't see it  in the Control Panel.

I booted to a LiveUSB using the latest and greatest image today had to offer, in order to run the script.  Here are the results:

```
               Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:   /[COMMAND.COM]("http://command.com/")

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /[NTDETECT.COM]("http://ntdetect.com/")

sdb3: _________________________________________________________________________

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

    File system:
    Boot sector type:  -
    Boot sector info:
    Mounting failed:
mount: unknown filesystem type ''

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________
_____________________________________________________

Disk /dev/sda: 1014 MB, 1014497280 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1981440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,981,439     1,981,377   b W95 FAT32


Drive: sdb ___________________
_____________________________________________________

Disk /dev/sdb: 292.0 GB, 291999055872 bytes
255 heads, 63 sectors/track, 35500 cylinders, total 570310656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63       112,454       112,392  de Dell Utility
/dev/sdb2    *        112,455   102,510,764   102,398,310   7 HPFS/NTFS
/dev/sdb3         102,510,826   570,291,434   467,780,609   f W95 Ext d (LBA)
/dev/sdb5         102,510,828   391,099,468   288,588,641   7 HPFS/NTFS
/dev/sdb6         450,896,418   570,291,434   119,395,017   e W95 FAT16 (LBA)
/dev/sdb7         391,100,416   448,339,967    57,239,552  83 Linux
/dev/sdb8         448,342,016   450,895,871     2,553,856  82 Linux
swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE
LABEL

/dev/loop0                                              squashfs
/dev/sda1        C0F0-7B70                              vfat
PENDRIVE
/dev/sda: PTTYPE="dos"
/dev/sdb1        07D8-021B                              vfat
DellUtility
/dev/sdb2        34ECA5F8ECA5B510                       ntfs       XP
/dev/sdb3: PTTYPE="dos"
/dev/sdb5        08F42B68F42B576A                       ntfs
DATA
/dev/sdb7        8d72b24b-2805-439a-8f7d-87c8775e7338   ext4
/dev/sdb8        9d25ae37-88b4-4eb2-b155-b2500f4e68bf   swap
/dev/sdb: PTTYPE="dos"

============================ "mount | grep ^/dev  output:
===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat
(rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb2/boot.ini: ================================

[boot loader]

timeout=3

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP
Professional" /noexecute=optin /fastdetect

C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons


=========================== sdb7/boot/grub/grub.cfg: ===========================

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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then
save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu
--class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,7)'
        search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
        linux   /boot/vmlinuz-2.6.32-24-generic-pae
root=UUID=8d72b24b-2805-439a-8f7d-87c8775e7338 ro   quiet splash
        initrd  /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)'
--class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod ext2
        set root='(hd1,7)'
        search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
        echo    'Loading Linux 2.6.32-24-generic-pae ...'
        linux   /boot/vmlinuz-2.6.32-24-generic-pae
root=UUID=8d72b24b-2805-439a-8f7d-87c8775e7338 ro single
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod ext2
        set root='(hd1,7)'
        search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod ext2
        set root='(hd1,7)'
        search --no-floppy --fs-uuid --set 8d72b24b-2805-439a-8f7d-87c8775e7338
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb2)" {
        insmod ntfs
        set root='(hd1,2)'
        search --no-floppy --fs-uuid --set 34eca5f8eca5b510
        drivemap -s (hd0) ${root}
        chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=8d72b24b-2805-439a-8f7d-87c8775e7338 /               ext4
errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=9d25ae37-88b4-4eb2-b155-b2500f4e68bf none            swap    sw
           0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 204.6GB: boot/grub/core.img
 218.0GB: boot/grub/grub.cfg
 204.6GB: boot/initrd.img-2.6.32-24-generic-pae
 204.6GB: boot/vmlinuz-2.6.32-24-generic-pae
 204.6GB: initrd.img
 204.6GB: vmlinuz

```

---

### Post by wilee-nilee on 2010-08-29
So with a raid format set-up there are others on the forum who are more familiar with what's going on. The script is helpful for them to see what is where, just post any more changes you might make, if you do.

I think it is a fairly straight forward fix I just don't know what it is.;)

---

### Post by oldfred on 2010-08-29
I do not see any mention of raid? The script usually shows it or is it so hardware related that it does not show?

I would just install grub to sda or sdb from your install in sdb7.

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sdb7 and want grub2 in drive sda's MBR:
Find linux partition, change sdb7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you install to sdb you have to make sure in BIOS your are booting sdb.

---

### Post by wilee-nilee on 2010-08-29
> **oldfred said:**
> I do not see any mention of raid? The script usually shows it or is it so hardware related that it does not show?

I would just install grub to sda or sdb from your install in sdb7.

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sdb7 and want grub2 in drive sda's MBR:
Find linux partition, change sdb7 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sdb7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

If you install to sdb you have to make sure in BIOS your are booting sdb.

I didn't see any raid in the script, but out of concern seeing the use of the words in post #1 I thought it better to error on the side of caution.

---

### Post by wilee-nilee on 2010-08-30
So it does look like sda1 is the thumb so use this link to confirm that sdb is the hard drive.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If it still is run from the thumb booted live in the teminal.
```
sudo mount /dev/sdb7 /mnt
```
then run
```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot then choose Ubuntu and run in it in the terminal.
```
sudo update-grub
```

When you boot from a loaded thumb at times at least on my set up it will show it as sda rather then a second HD.

---

### Post by pcreqeust on 2010-08-30
sda was definitely the thumb drive.  Note that I have never seen the grub menu at bootup, not even once, even though the Ubuntu installer completed unremarkably.  FWIW, here is a screenshot of the Disk Manager in Windows.  I think I'll try a reinstall from the LiveUSB one more time, before venturing into the prescribed commands.

---

### Post by oldfred on 2010-08-30
It looks like windows sees the flash drive as drive 1 but grub/Ubuntu see it as drive 0 or sda.

When you install Ubuntu grub normally installs to sda as it assumes in most cases that is the default boot drive. It has an advanced button to use to make sure where to install grub. Click the advanced button and make sure you install grub to the same drive as the install and in BIOS are booting that same drive.

Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)

---

### Post by pcreqeust on 2010-08-30
I am mid install and have my fingers crossed.  In the Ubuntu installer from the USB (which showed up as sda again)I deleted sdb6, sdb7, sdb8.  I did an Advanced partioning.  I made a new sdb6 and sdb7, with one being swap, and the other being ext4 mounted at / (i hope that was a good choice).  At the last summary screen, i cliked Advanced, and there is a check mark to install boot loader on /dev/sda by default.  Being that is the USB drive, that didn't seem very useful.  my other choices were /dev/sdb Dell virtual disk (292.0GB) or sdb2 MS Windows XP Pro.  i piicked /dev/sdb.  I hope that was a good choice :)

---

### Post by pcreqeust on 2010-08-30
well, it seemed to complete.  it reached 100%, then i think it presented me with a reboot button.  I cliked it.  it took a minute to go away.  it
s been 15 minutes at the pink background screen and no reboot. numlock and capslock don't toggle, so the keyboard seems unresponsive. I'm going to walk away from it for 30 minutes or so and hopefully i can boot to _some_ OS.

---

### Post by oldfred on 2010-08-31
There seems to be a minor bug on ending. I had to hit enter and then it rebooted.

---

### Post by pcreqeust on 2010-08-31
Yes.  I'm replying from Ubuntu in my problem machine.  I came back to it, pressed numlock to see if the computer was responsive, then it finally rebooted.  I see a grub menu after the hardware RAID adapter initializes. Ubuntu and XP!  I just get one weird startup problem for Ubuntu.  After I choose it in Grub, I get "Gave up waiting for root device...Check Boot Args...rootdelay...dropping to a shell"  If I type quit, a few moments later I can log in.

---

### Post by oldfred on 2010-08-31
See quixote's recommendation:

[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

---

