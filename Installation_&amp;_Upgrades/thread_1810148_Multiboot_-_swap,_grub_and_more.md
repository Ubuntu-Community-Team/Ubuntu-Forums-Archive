---
title: "Multiboot - swap, grub and more"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by tuxor1337 on 2011-07-22
Hi all,

on my Thinkpad X31, I installed several linux distributions:

```
sda1: Ubuntu Studio (~ Ubuntu 11.04) [manages grub2 in MBR]
sda2: Scientific Linux 5.6 (~ Red Hat 5.6)
sda3: Elementary OS (~ Ubuntu 10.10)
sda4: extended
   sda5: Fuduntu (~ Fedora 14)
   sda6: swap [shared between the systems]
```Ubuntu Studio was the last one to be installed, it recognized all of the others and successfully set up the boot loader (grub2). But now some problems arose (feel free to read only one part, if you don't like long and complicated problems):

**First Part: Grub**
Since all of these distributions have there own kernels, it's necessary to update the grub menu after each kernel-update. But since grub "belongs to" Ubuntu at the moment, I have to change the menu manually, unless the kernel update is from Ubuntu.
--> How can I manage this?

**Second Part: Swap**
I want to share the swap partition between the systems. At first it was only recognized by Ubuntu properly, so I tried to reformat it in one of the other systems. But every time I do that, Ubuntu breaks the swap-partition, so that (after a simple boot of Ubuntu) the swap-partition becomes corrupt. The partition simply breaks - gparted shows a yellow exclamation mark and doesn't recognize the partition's type.

**Third Part: The extended partition and Ubuntu**
As soon as I removed the swap-partition with gparted (for testing reasons) and subsequently booted Ubuntu, the partition with Fuduntu was destroyed. I'm not joking: booting Ubuntu renders sda5 unusable! I reinstalled Fuduntu and again removed the swap partition. (After that, sda5 was still intact and Fuduntu booted properly.) But as soon as I booted Ubuntu, sda5 was corrupt. (I repeated this procedure several times changing some details and am really sure now, that booting Ubuntu is the definite reason for this.)
So Ubuntu seems to handle the extended partition kind of strange 
[*]. It even breaks it - I have no reasonable explanation for this. Does anybody know what to do about that?

(Part 2 and 3 are obviously related to each other.)

This is not a configuration for production. I'm just testing! So don't ask me, whether this whole configuration makes sense at all...

[I]
[*] My guess: The partition table, modified by the Fuduntu Installer is compatible with Elementary OS and Fuduntu, but not with Ubuntu - at least as far as extended partitions are concerned.[/I]

---

### Post by oldfred on 2011-07-22
Each of your fstabs has the UUID of swap unless they are mounting by device like /dev/sda6. So if you delete swap and recreate it you have a new UUID. Do not delete & recreate, it is normally just used by a new install.

Grub2's os-prober reads the grub.cfg, menu.lst or other standard menu from other systems and converts to a grub2 boot stanza. You then have to run update-grub in your other install to update its menu, then boot into Ubuntu and run update-grub to get it to see the new entry.

Several work arounds.

If you have grub legacy as a boot loader install it to the partition boot sector of the install. Then just add a chainboot entry to grub2's 40_custom. Then you are booting the menu of that install, just as two steps.

If the other install is Debian based (do not know about others) you can boot using the links in / (root). The link is to the most current kernel and is automatically updated with the new kernel install.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by tuxor1337 on 2011-07-22
> **oldfred said:**
> Each of your fstabs has the UUID of swap unless they are mounting by device like /dev/sda6. So if you delete swap and recreate it you have a new UUID. Do not delete & recreate, it is normally just used by a new install.
I am aware of this and updated the most recent UUID in the /etc/fstab. But as I told you: Ubuntu completely destroys the swap partition. It's not only an fstab-problem, but the partition-table is corrupt!

> **oldfred said:**
> Grub2's os-prober reads the grub.cfg, menu.lst or other standard menu from other systems and converts to a grub2 boot stanza. You then have to run update-grub in your other install to update its menu, then boot into Ubuntu and run update-grub to get it to see the new entry.
That's cool, I didn't know about that. Maybe that's already a solution.

> **oldfred said:**
> If you have grub legacy as a boot loader install it to the partition boot sector of the install. Then just add a chainboot entry to grub2's 40_custom. Then you are booting the menu of that install, just as two steps.
I'm going to test this. :)

> **oldfred said:**
> If the other install is Debian based (do not know about others) you can boot using the links in / (root). The link is to the most current kernel and is automatically updated with the new kernel install.


Most interesting! Thanks for your advice :-)


Would be cool to hear something about the problem, that Ubuntu "kills" my Fuduntu-partition.

---

### Post by ajgreeny on 2011-07-22
I know nothing about Fuduntu, and have never even heard of it till now, but you seem to suggest that it is a version of Fedora 14, in which case it probably installs using LVM as default, which can be a disaster when trying to dual or multiboot with ubuntu, and the whole ubuntu family.

None of the ubuntu OSs can deal with LVM without adding extra packages, and I gave up trying and used manual partitioning when I tried Fedora a long time ago.  That suddenly made life a lot easier and it then showed up in the grub menu, legacy grub at that time.

Check with the command ```
sudo fdisk -l
``` from your ubuntu terminal.  It will still show the fuduntu partition, I suspect, but show that it is partitioned with LVM.  If fdisk does not show it at all, try gparted which I am pretty sure will show the partition, however I think fdisk will show it and list it as LVM.

---

### Post by tuxor1337 on 2011-07-22
Thanks for your reply :)

I'm quite familiar with Fedora and you are right: the standard installation wants to put Fedora into a logical volume. But I manually chose to install Fuduntu (which really is some kind of Fedora 14 Spin) into a normal partition. I did the partitioning myself during install and I checked this configuration after installation with gparted in both Scientific Linux and Elementary OS - everything was fine here (just a usual ext4 partition).

But as soon as I booted Ubuntu (Studio) 11.04, the partition was corrupt: It wouldn't boot any more and would be displayed broken in gparted.

---

### Post by oldfred on 2011-07-22
If you want all the details of what is where and document that run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install mawk

---

### Post by tuxor1337 on 2011-07-22
Please note, that sdb is my usb-stick with FuduntuLiveDVD on it.

**RESULTS.txt when run directly after succesful installation of Fuduntu:**
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.6 
                       (Boron) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fuduntu release 14 (Laughin) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21 ........>4..r>.........7@...0...~.s...~...f...M.f.f....f..0~....>2}.u......
    Boot sector info:   Syslinux looks at sector 1954000 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,454,714    19,454,652  83 Linux
/dev/sda2          19,454,715    37,881,269    18,426,555  83 Linux
/dev/sda3          37,881,856    55,459,839    17,577,984  83 Linux
/dev/sda4          55,459,840    78,139,391    22,679,552   5 Extended
/dev/sda5          55,461,888    73,893,887    18,432,000  83 Linux
/dev/sda6          73,895,936    78,139,391     4,243,456  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4051 MB, 4051697664 bytes
125 heads, 62 sectors/track, 1021 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,912,749     7,912,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              DM_snapshot_cow 
/dev/loop2                                              squashfs   
/dev/loop3       f468a9a6-717d-4b1d-89c9-effefcb2a054   ext4       _Fuduntu-i386-Li
/dev/loop4                                              DM_snapshot_cow 
/dev/mapper/live-osimg-min f468a9a6-717d-4b1d-89c9-effefcb2a054   ext4       _Fuduntu-i386-Li
/dev/mapper/live-rw f468a9a6-717d-4b1d-89c9-effefcb2a054   ext4       _Fuduntu-i386-Li
/dev/sda1        745b4cd1-9be7-4368-a0b3-b5589a2aab4a   ext4       
/dev/sda2        1fc15114-df0b-4af6-9f25-4ae03291c248   ext3       
/dev/sda3        bde570cc-c96c-4745-8939-dd3a9655e884   ext4       
/dev/sda5        65f49bac-af34-4177-8952-d6c5de3c33fb   ext4       _Fuduntu-i386-Li
/dev/sda6        bbfd9391-9fc2-4a76-a0f2-238a9a0dde41   swap       
/dev/sdb1        AE6B-8E4E                              vfat       fuduntu

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
live-osimg-min
live-rw

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/live-rw /                        ext4       (rw,noatime)
/dev/sdb1        /mnt/live                vfat       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda6 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.497462749 = 6.976597504    boot/grub/core.img                             1
   2.416320324 = 2.594504192    boot/grub/grub.cfg                             1
   3.379455090 = 3.628662272    boot/initrd.img-2.6.38-10-generic              2
   3.253886700 = 3.493834240    boot/initrd.img-2.6.38-8-generic               2
   3.273776531 = 3.515190784    boot/vmlinuz-2.6.38-10-generic                 1
   0.635100842 = 0.681934336    boot/vmlinuz-2.6.38-8-generic                  1
   3.379455090 = 3.628662272    initrd.img                                     2
   3.253886700 = 3.493834240    initrd.img.old                                 2
   3.273776531 = 3.515190784    vmlinuz                                        1
   0.635100842 = 0.681934336    vmlinuz.old                                    1

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by livecd-install
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
        initrd /boot/initrd-2.6.18-238.12.1.el5.img
title Elementary OS
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
        initrd /boot/initrd.img-2.6.35-30-generic
title Ubuntu
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
        initrd /boot/initrd.img-2.6.38-10-generic
title Ubuntu Chainload
    root(hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/hda2    /        ext3        defaults    1 1
devpts          /dev/pts        devpts          gid=5,mode=620  0 0
tmpfs            /dev/shm        tmpfs           defaults        0 0
proc            /proc           proc            defaults        0 0
sysfs        /sys            sysfs           defaults        0 0
/dev/hda6    swap        swap        defaults,pri=1    0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.878304958 = 18.122941952   boot/grub/grub.conf                            1
  16.878304958 = 18.122941952   boot/grub/menu.lst                             1
  16.854959011 = 18.097874432   boot/grub/stage2                               2
  16.802663326 = 18.041722368   boot/initrd-2.6.18-238.12.1.el5.img            2
  16.780446529 = 18.017867264   boot/vmlinuz-2.6.18-238.12.1.el5               2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
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
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.1-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.1-1.fc14.i686.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.3-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.3-1.fc14.i686.img
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=bde570cc-c96c-4745-8939-dd3a9655e884 /               ext4    errors=remount-ro 0       1

/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.266391754 = 26.055839744   boot/grub/core.img                             1
  20.358802795 = 21.860098048   boot/grub/grub.cfg                             1
  19.356868744 = 20.784279552   boot/initrd.img-2.6.35-28-generic              2
  19.444622040 = 20.878503936   boot/initrd.img-2.6.35-30-generic              3
  24.493812561 = 26.300030976   boot/vmlinuz-2.6.35-28-generic                 1
  24.261329651 = 26.050404352   boot/vmlinuz-2.6.35-30-generic                 1
  19.444622040 = 20.878503936   initrd.img                                     3
  19.356868744 = 20.784279552   initrd.img.old                                 2
  24.261329651 = 26.050404352   vmlinuz                                        1
  24.493812561 = 26.300030976   vmlinuz.old                                    1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Fri Jul 22 23:46:13 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=65f49bac-af34-4177-8952-d6c5de3c33fb /                       ext4    defaults        1 1
UUID=bbfd9391-9fc2-4a76-a0f2-238a9a0dde41 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.200351715 = 31.353638912   boot/initramfs-2.6.39.1-1.fc14.i686.img        2
  27.753578186 = 29.800177664   boot/initrd-plymouth.img                       1
  27.732833862 = 29.777903616   boot/vmlinuz-2.6.39.1-1.fc14.i686              1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry0
menu label Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb

label ubnentry1
menu label Verify and Boot Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb check

label ubnentry2
menu label Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry3
menu label Boot (Basic Video)
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM xdriver=vesa nomodeset

label ubnentry4
menu label Verify and Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM  check

label ubnentry5
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically



```**RESULTS.txt after reboot to Elementary OS:**
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.6 
                       (Boron) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fuduntu release 14 (Laughin) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21 ........>4..r>.........7@...0...~.s...~...f...M.f.f....f..0~....>2}.u......
    Boot sector info:   Syslinux looks at sector 1954000 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 40.0 GByte, 40007761920 Byte
255 Köpfe, 63 Sektoren/Spur, 4864 Zylinder, zusammen 78140160 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,454,714    19,454,652  83 Linux
/dev/sda2          19,454,715    37,881,269    18,426,555  83 Linux
/dev/sda3          37,881,856    55,459,839    17,577,984  83 Linux
/dev/sda4          55,459,840    78,139,391    22,679,552   5 Extended
/dev/sda5          55,461,888    73,893,887    18,432,000  83 Linux
/dev/sda6          73,895,936    78,139,391     4,243,456  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Platte /dev/sdb: 4051 MByte, 4051697664 Byte
125 Köpfe, 62 Sektoren/Spur, 1021 Zylinder, zusammen 7913472 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,912,749     7,912,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        745b4cd1-9be7-4368-a0b3-b5589a2aab4a   ext4       
/dev/sda2        1fc15114-df0b-4af6-9f25-4ae03291c248   ext3       
/dev/sda3        bde570cc-c96c-4745-8939-dd3a9655e884   ext4       
/dev/sda5        65f49bac-af34-4177-8952-d6c5de3c33fb   ext4       _Fuduntu-i386-Li
/dev/sda6        bbfd9391-9fc2-4a76-a0f2-238a9a0dde41   swap       
/dev/sdb1        AE6B-8E4E                              vfat       fuduntu

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/fuduntu           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda6 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.497462749 = 6.976597504    boot/grub/core.img                             1
   2.416320324 = 2.594504192    boot/grub/grub.cfg                             1
   3.379455090 = 3.628662272    boot/initrd.img-2.6.38-10-generic              2
   3.253886700 = 3.493834240    boot/initrd.img-2.6.38-8-generic               2
   3.273776531 = 3.515190784    boot/vmlinuz-2.6.38-10-generic                 1
   0.635100842 = 0.681934336    boot/vmlinuz-2.6.38-8-generic                  1
   3.379455090 = 3.628662272    initrd.img                                     2
   3.253886700 = 3.493834240    initrd.img.old                                 2
   3.273776531 = 3.515190784    vmlinuz                                        1
   0.635100842 = 0.681934336    vmlinuz.old                                    1

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by livecd-install
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
        initrd /boot/initrd-2.6.18-238.12.1.el5.img
title Elementary OS
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
        initrd /boot/initrd.img-2.6.35-30-generic
title Ubuntu
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
        initrd /boot/initrd.img-2.6.38-10-generic
title Ubuntu Chainload
    root(hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/hda2    /        ext3        defaults    1 1
devpts          /dev/pts        devpts          gid=5,mode=620  0 0
tmpfs            /dev/shm        tmpfs           defaults        0 0
proc            /proc           proc            defaults        0 0
sysfs        /sys            sysfs           defaults        0 0
/dev/hda6    swap        swap        defaults,pri=1    0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.878304958 = 18.122941952   boot/grub/grub.conf                            1
  16.878304958 = 18.122941952   boot/grub/menu.lst                             1
  16.854959011 = 18.097874432   boot/grub/stage2                               2
  16.802663326 = 18.041722368   boot/initrd-2.6.18-238.12.1.el5.img            2
  16.780446529 = 18.017867264   boot/vmlinuz-2.6.18-238.12.1.el5               2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
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
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.1-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.1-1.fc14.i686.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.3-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.3-1.fc14.i686.img
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=bde570cc-c96c-4745-8939-dd3a9655e884 /               ext4    errors=remount-ro 0       1

/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.266391754 = 26.055839744   boot/grub/core.img                             1
  20.358802795 = 21.860098048   boot/grub/grub.cfg                             1
  19.356868744 = 20.784279552   boot/initrd.img-2.6.35-28-generic              2
  19.444622040 = 20.878503936   boot/initrd.img-2.6.35-30-generic              3
  24.493812561 = 26.300030976   boot/vmlinuz-2.6.35-28-generic                 1
  24.261329651 = 26.050404352   boot/vmlinuz-2.6.35-30-generic                 1
  19.444622040 = 20.878503936   initrd.img                                     3
  19.356868744 = 20.784279552   initrd.img.old                                 2
  24.261329651 = 26.050404352   vmlinuz                                        1
  24.493812561 = 26.300030976   vmlinuz.old                                    1

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Fri Jul 22 23:46:13 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=65f49bac-af34-4177-8952-d6c5de3c33fb /                       ext4    defaults        1 1
UUID=bbfd9391-9fc2-4a76-a0f2-238a9a0dde41 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  29.200351715 = 31.353638912   boot/initramfs-2.6.39.1-1.fc14.i686.img        2
  27.753578186 = 29.800177664   boot/initrd-plymouth.img                       1
  27.732833862 = 29.777903616   boot/vmlinuz-2.6.39.1-1.fc14.i686              1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry0
menu label Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb

label ubnentry1
menu label Verify and Boot Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb check

label ubnentry2
menu label Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry3
menu label Boot (Basic Video)
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM xdriver=vesa nomodeset

label ubnentry4
menu label Verify and Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM  check

label ubnentry5
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```**And now the most interesting part! RESULTS.txt after first boot of Ubuntu:**
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.6 
                       (Boron) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unbekannter Dateisystemtyp &#8222;&#8220;

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21 ........>4..r>.........7@...0...~.s...~...f...M.f.f....f..0~....>2}.u......
    Boot sector info:   Syslinux looks at sector 1954000 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 40.0 GByte, 40007761920 Byte
255 Köpfe, 63 Sektoren/Spur, 4864 Zylinder, zusammen 78140160 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,454,714    19,454,652  83 Linux
/dev/sda2          19,454,715    37,881,269    18,426,555  83 Linux
/dev/sda3          37,881,856    55,459,839    17,577,984  83 Linux
/dev/sda4          55,459,840    78,139,391    22,679,552   5 Extended
/dev/sda5          55,461,888    73,893,887    18,432,000  83 Linux
/dev/sda6          73,895,936    78,139,391     4,243,456  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Platte /dev/sdb: 4051 MByte, 4051697664 Byte
125 Köpfe, 62 Sektoren/Spur, 1021 Zylinder, zusammen 7913472 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,912,749     7,912,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 e6c88de2-6ad9-4745-bf72-fe8f7907f626   swap       
/dev/sda1        745b4cd1-9be7-4368-a0b3-b5589a2aab4a   ext4       
/dev/sda2        1fc15114-df0b-4af6-9f25-4ae03291c248   ext3       
/dev/sda3        bde570cc-c96c-4745-8939-dd3a9655e884   ext4       
/dev/sda6        bbfd9391-9fc2-4a76-a0f2-238a9a0dde41   swap       
/dev/sdb1        AE6B-8E4E                              vfat       fuduntu

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/fuduntu           vfat       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda6 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.497462749 = 6.976597504    boot/grub/core.img                             1
   2.416320324 = 2.594504192    boot/grub/grub.cfg                             1
   3.379455090 = 3.628662272    boot/initrd.img-2.6.38-10-generic              2
   3.253886700 = 3.493834240    boot/initrd.img-2.6.38-8-generic               2
   3.273776531 = 3.515190784    boot/vmlinuz-2.6.38-10-generic                 1
   0.635100842 = 0.681934336    boot/vmlinuz-2.6.38-8-generic                  1
   3.379455090 = 3.628662272    initrd.img                                     2
   3.253886700 = 3.493834240    initrd.img.old                                 2
   3.273776531 = 3.515190784    vmlinuz                                        1
   0.635100842 = 0.681934336    vmlinuz.old                                    1

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by livecd-install
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
        initrd /boot/initrd-2.6.18-238.12.1.el5.img
title Elementary OS
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
        initrd /boot/initrd.img-2.6.35-30-generic
title Ubuntu
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
        initrd /boot/initrd.img-2.6.38-10-generic
title Ubuntu Chainload
    root(hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/hda2    /        ext3        defaults    1 1
devpts          /dev/pts        devpts          gid=5,mode=620  0 0
tmpfs            /dev/shm        tmpfs           defaults        0 0
proc            /proc           proc            defaults        0 0
sysfs        /sys            sysfs           defaults        0 0
/dev/hda6    swap        swap        defaults,pri=1    0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.878304958 = 18.122941952   boot/grub/grub.conf                            1
  16.878304958 = 18.122941952   boot/grub/menu.lst                             1
  16.854959011 = 18.097874432   boot/grub/stage2                               2
  16.802663326 = 18.041722368   boot/initrd-2.6.18-238.12.1.el5.img            2
  16.780446529 = 18.017867264   boot/vmlinuz-2.6.18-238.12.1.el5               2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
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
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.1-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.1-1.fc14.i686.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.3-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.3-1.fc14.i686.img
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=bde570cc-c96c-4745-8939-dd3a9655e884 /               ext4    errors=remount-ro 0       1

/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.266391754 = 26.055839744   boot/grub/core.img                             1
  20.358802795 = 21.860098048   boot/grub/grub.cfg                             1
  19.356868744 = 20.784279552   boot/initrd.img-2.6.35-28-generic              2
  19.444622040 = 20.878503936   boot/initrd.img-2.6.35-30-generic              3
  24.493812561 = 26.300030976   boot/vmlinuz-2.6.35-28-generic                 1
  24.261329651 = 26.050404352   boot/vmlinuz-2.6.35-30-generic                 1
  19.444622040 = 20.878503936   initrd.img                                     3
  19.356868744 = 20.784279552   initrd.img.old                                 2
  24.261329651 = 26.050404352   vmlinuz                                        1
  24.493812561 = 26.300030976   vmlinuz.old                                    1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry0
menu label Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb

label ubnentry1
menu label Verify and Boot Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb check

label ubnentry2
menu label Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry3
menu label Boot (Basic Video)
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM xdriver=vesa nomodeset

label ubnentry4
menu label Verify and Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM  check

label ubnentry5
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```[B]Believe me: sda5 is completely broken after that. No way of fixing it! And I found nothing in dmesg that might explain this destructive behaviour of Natty. Ubuntu 10.10 (Elementary OS) is not that aggressive ;-)
[/B]

---

### Post by tuxor1337 on 2011-07-22
[B]What I did now is: I removed the corrupt partition using gparted. After that, I booted Natty again. And now the SWAP-partition is also corrupt! Maybe Natty doesn't like the number 5 in sda5....... :

[/B]```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.6 
                       (Boron) Kernel on an
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unbekannter Dateisystemtyp „“

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 2010-07-21 ........>4..r>.........7@...0...~.s...~...f...M.f.f....f..0~....>2}.u......
    Boot sector info:   Syslinux looks at sector 1954000 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 40.0 GByte, 40007761920 Byte
255 Köpfe, 63 Sektoren/Spur, 4864 Zylinder, zusammen 78140160 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    19,454,714    19,454,652  83 Linux
/dev/sda2          19,454,715    37,881,269    18,426,555  83 Linux
/dev/sda3          37,881,856    55,459,839    17,577,984  83 Linux
/dev/sda4          55,459,840    78,139,391    22,679,552   5 Extended
/dev/sda5          73,895,936    78,139,391     4,243,456  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Platte /dev/sdb: 4051 MByte, 4051697664 Byte
125 Köpfe, 62 Sektoren/Spur, 1021 Zylinder, zusammen 7913472 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,912,749     7,912,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 37a822a2-db07-4f88-b021-1d97ddf62b36   swap       
/dev/sda1        745b4cd1-9be7-4368-a0b3-b5589a2aab4a   ext4       
/dev/sda2        1fc15114-df0b-4af6-9f25-4ae03291c248   ext3       
/dev/sda3        bde570cc-c96c-4745-8939-dd3a9655e884   ext4       
/dev/sdb1        AE6B-8E4E                              vfat       fuduntu

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/fuduntu_          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
set locale_dir=($root)/boot/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-10-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 745b4cd1-9be7-4368-a0b3-b5589a2aab4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
    initrd /boot/initrd.img-2.6.35-28-generic
}
menuentry "elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root bde570cc-c96c-4745-8939-dd3a9655e884
    linux /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single
    initrd /boot/initrd.img-2.6.35-28-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda6 none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.497462749 = 6.976597504    boot/grub/core.img                             1
   2.416320324 = 2.594504192    boot/grub/grub.cfg                             1
   3.379455090 = 3.628662272    boot/initrd.img-2.6.38-10-generic              2
   3.253886700 = 3.493834240    boot/initrd.img-2.6.38-8-generic               2
   3.273776531 = 3.515190784    boot/vmlinuz-2.6.38-10-generic                 1
   0.635100842 = 0.681934336    boot/vmlinuz-2.6.38-8-generic                  1
   3.379455090 = 3.628662272    initrd.img                                     2
   3.253886700 = 3.493834240    initrd.img.old                                 2
   3.273776531 = 3.515190784    vmlinuz                                        1
   0.635100842 = 0.681934336    vmlinuz.old                                    1

========================== sda2/boot/grub/grub.conf: ===========================

--------------------------------------------------------------------------------
# grub.conf generated by livecd-install
default=0
timeout=10
splashimage=(hd0,1)/boot/grub/splash.xpm.gz
#hiddenmenu
title Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5)
        root (hd0,1)
        kernel /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
        initrd /boot/initrd-2.6.18-238.12.1.el5.img
title Elementary OS
        root (hd0,2)
        kernel /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro quiet splash
        initrd /boot/initrd.img-2.6.35-30-generic
title Ubuntu
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.38-10-generic root=UUID=745b4cd1-9be7-4368-a0b3-b5589a2aab4a ro   quiet splash vt.handoff=7
        initrd /boot/initrd.img-2.6.38-10-generic
title Ubuntu Chainload
    root(hd0,0)
    chainloader +1
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
/dev/hda2    /        ext3        defaults    1 1
devpts          /dev/pts        devpts          gid=5,mode=620  0 0
tmpfs            /dev/shm        tmpfs           defaults        0 0
proc            /proc           proc            defaults        0 0
sysfs        /sys            sysfs           defaults        0 0
/dev/hda6    swap        swap        defaults,pri=1    0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.878304958 = 18.122941952   boot/grub/grub.conf                            1
  16.878304958 = 18.122941952   boot/grub/menu.lst                             1
  16.854959011 = 18.097874432   boot/grub/stage2                               2
  16.802663326 = 18.041722368   boot/initrd-2.6.18-238.12.1.el5.img            2
  16.780446529 = 18.017867264   boot/vmlinuz-2.6.18-238.12.1.el5               2

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
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
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'elementary-jupiter, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set bde570cc-c96c-4745-8939-dd3a9655e884
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=bde570cc-c96c-4745-8939-dd3a9655e884 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set de68c92b-b2de-4a37-a0d1-aecc53613bd1
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=de68c92b-b2de-4a37-a0d1-aecc53613bd1 ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Scientific Linux SL release 5.6 (Boron) (2.6.18-238.12.1.el5) (on /dev/sda2)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 1fc15114-df0b-4af6-9f25-4ae03291c248
    linux /boot/vmlinuz-2.6.18-238.12.1.el5 ro root=/dev/hda2
    initrd /boot/initrd-2.6.18-238.12.1.el5.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.1-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.1-1.fc14.i686.img
}
menuentry "Fuduntu release 14 (Laughin) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set fef027a2-fc77-4bfc-bd2e-03c53e72c392
    linux /boot/vmlinuz-2.6.39.3-1.fc14.i686 root=/dev/sda6
    initrd /boot/initramfs-2.6.39.3-1.fc14.i686.img
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=bde570cc-c96c-4745-8939-dd3a9655e884 /               ext4    errors=remount-ro 0       1

/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.266391754 = 26.055839744   boot/grub/core.img                             1
  20.358802795 = 21.860098048   boot/grub/grub.cfg                             1
  19.356868744 = 20.784279552   boot/initrd.img-2.6.35-28-generic              2
  19.444622040 = 20.878503936   boot/initrd.img-2.6.35-30-generic              3
  24.493812561 = 26.300030976   boot/vmlinuz-2.6.35-28-generic                 1
  24.261329651 = 26.050404352   boot/vmlinuz-2.6.35-30-generic                 1
  19.444622040 = 20.878503936   initrd.img                                     3
  19.356868744 = 20.784279552   initrd.img.old                                 2
  24.261329651 = 26.050404352   vmlinuz                                        1
  24.493812561 = 26.300030976   vmlinuz.old                                    1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry0
menu label Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb

label ubnentry1
menu label Verify and Boot Fuduntu-i386-LiveDVD
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb check

label ubnentry2
menu label Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM

label ubnentry3
menu label Boot (Basic Video)
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM xdriver=vesa nomodeset

label ubnentry4
menu label Verify and Boot
kernel /EFI/boot/vmlinuz0
append initrd=/EFI/boot/initrd0.img root=UUID=AE6B-8E4E rootfstype=auto ro liveimg quiet rhgb quiet acpi_osi=Linux elevator=deadline rhgb rd_NO_LUKS rd_NO_MD rd_NO_DM  check

label ubnentry5
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit 

--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-07-22
I tried to look for an inconsistent entry that might cause problems, but could not find anything.

Your Fuduntu does not look complete in any of the boot scripts. It has no grub files and grub.conf or menu.lst (not sure what it uses).

Your SL is older and probably does not recognize ext4 partitions. Perhaps that is an issue. 

I do not see how swap can be corrupted. It is just empty space, it is not formated. But I might change to using UUID not device /dev/sda6.

---

### Post by tuxor1337 on 2011-07-22
Thanks for your answer.

> **oldfred said:**
> Your Fuduntu does not look complete in any of the boot scripts. It has no grub files and grub.conf or menu.lst (not sure what it uses).
Yes, that's right. Fuduntu usually uses Grub legacy, but on installation I chose not to install any boot loader to guarantee that there is no bootloader conflict.

> **oldfred said:**
> Your SL is older and probably does not recognize ext4 partitions. Perhaps that is an issue. 
None of the above RESULTS.txt was created on the SL installation. Indeed SL5.6 can't read ext4. But I don't know how this could be an issue...

> **oldfred said:**
> I do not see how swap can be corrupted. It is just empty space, it is not formated. But I might change to using UUID not device /dev/sda6.
Yes, that's the big question... /dev/sda6 was just a temporary workaround, because I recreated that partition so often lately. Will use UUID again asap.

Tomorrow, I will be able to report back concerning another attempt to get those four OS on that hdd ;)

---

### Post by tuxor1337 on 2011-07-23
I finally found solutions to all of my problems :)
[B]
PART ONE: Grub
[/B]As oldfred pointed out, grub2 is pretty good at checking other systems' boot menus at update-grub2. So I will just do a update-grub2 everytime I have a kernel update. Since kernel-updates are not that often, that's a quite satisfactory solution.
Besides I told the other OS to install their grub into their own partitions - this makes it easy to restore access to them (e.g. via chainloader) in case of damage to grub2 or to my Natty installation.

**PART TWO and PART THREE: Swap**
Indeed, there was something wrong with the swap thing: While the other three were using the swap partition as I wanted them to, Natty wanted to use a crypt-swap! For a strange reason, Natty always used the last partition on my hdd. And so of course no other OS knew, why this parititon became corrupt: it was overwritten by an encrypted (i.e. unreadable) swap!
Deactivating crypt swap like in this tutorial helped: [http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

Now the four penguines as described in the first post live peacefully together on my ThinkPad X31 and they all work really fine :)

Thanks for your advices and your help! This is a great forum!

---

