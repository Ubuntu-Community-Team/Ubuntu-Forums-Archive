---
title: "Clean install of Ubuntu boots to 'BusyBox'?"
date: 2017-11-11
forum: Installation &amp; Upgrades
---

### Post by chainbade84 on 2017-11-11
[ATTACH=CONFIG]277488[/ATTACH]

120GB SSD.
Windows 7 the first partition non-efi of 60GB on /dev/sda1, /dev/sda2, and /dev/sda3
Installed Ubuntu 17.10 64-bit non-efi on /dev/sda4 of 40GB through live USB stick
Have tried reinstalling various time, having Ubuntu automatically choose how to install or manually choosing the partition to install to.  

upon a little searching, i booted back up with the live USB disk and ran sudo blkid, which should the UUID for /dev/sda4, which matches what the above screenshot says that it does not exisi for some reason...any ideas?

---

### Post by Bashing-om on 2017-11-11
chainbade84; Hello - Welcome to the forum .

Before we delve deeper, let's verify what we are working with.
Boot up the liveUSB and
Post back - Between code tags - the outputs of terminal commands:
```

sudo blkid
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Once we know the target we verify that UUID :)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by oldfred on 2017-11-11
Have you tried typing exit? Sometimes that works.

What brand/model system?
Is drive set for AHCI, not IDE nor RAID?

---

### Post by chainbade84 on 2017-11-11
> **Bashing-om said:**
> chainbade84; Hello - Welcome to the forum .

Before we delve deeper, let's verify what we are working with.
Boot up the liveUSB and
Post back - Between code tags - the outputs of terminal commands:
```

sudo blkid
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Once we know the target we verify that UUID :)[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


```

/dev/sda1: LABEL="System Reserved" UUID="CE3E58513E583525" TYPE="ntfs" PARTUUID="e5e81164-01"
/dev/sda2: UUID="0C4C63244C6307B2" TYPE="ntfs" PARTUUID="e5e81164-02"
/dev/sda5: UUID="1bed0af4-d096-45bd-b6a1-b39531a03665" TYPE="ext4" PARTUUID="e5e81164-05"
/dev/sdb1: LABEL="Data" UUID="2CD450A3D45070D6" TYPE="ntfs" PARTUUID="6cfe656c-01"
/dev/sdc1: LABEL="UUI" UUID="24AC-56AD" TYPE="vfat" PARTUUID="2dbd2b5d-01"
/dev/loop0: TYPE="squashfs"



```


```

Disk /dev/loop0: 1.3 GiB, 1425731584 bytes, 2784632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe5e81164

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 163842047 163635200   78G  7 HPFS/NTFS/exFAT
/dev/sda3       163844094 250068991  86224898 41.1G  5 Extended
/dev/sda5       163844096 250068991  86224896 41.1G 83 Linux

Partition 3 does not start on physical sector boundary.


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x6cfe656c

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 1.9 GiB, 2003828736 bytes, 3913728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2dbd2b5d

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 3913727 3911680  1.9G  c W95 FAT32 (LBA)



```

> **oldfred said:**
> Have you tried typing exit? Sometimes that works.

What brand/model system?
Is drive set for AHCI, not IDE nor RAID?

it's an Asus N56JR laptop (i7 with 12GB RAM), 128GB SSD, 1TB HDD.  Drive is set to AHCI in the BIOS.  No RAID at all.

---

### Post by Bashing-om on 2017-11-11
chainbade84; Himmm ..

Surprise, surprise .. the UUID is identified and the target here is sda5.
Curios and curiouser ......
What results when you attempt to boot sda5 explicitly from grub ?

Reboot the machine, and as soon as the bios screen clears depress and hold a shift key -> grub boot menu;
Here press the 'c' key for (c)ommand mode -> grub > .
here - one command at the time - :
```

set prefix=(hd0,msdos5)/boot/grub
set root=(hd0,msdos5)
linux (hd0,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,msdos5)/initrd.img
boot

```

fault isolation
[INDENT][INDENT]give it a poke and see
[/INDENT][/INDENT]

---

### Post by chainbade84 on 2017-11-11
> **Bashing-om said:**
> chainbade84; Himmm ..

Surprise, surprise .. the UUID is identified and the target here is sda5.
Curios and curiouser ......
What results when you attempt to boot sda5 explicitly from grub ?

Reboot the machine, and as soon as the bios screen clears depress and hold a shift key -> grub boot menu;
Here press the 'c' key for (c)ommand mode -> grub > .
here - one command at the time - :
```

set prefix=(hd0,msdos5)/boot/grub
set root=(hd0,msdos5)
linux (hd0,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,msdos5)/initrd.img
boot

```

fault isolation[INDENT][INDENT]give it a poke and see
[/INDENT]
[/INDENT]


thanks for the reply, unfortunately it did not work.  Here is what it says now:

[ATTACH=CONFIG]277491[/ATTACH]

I'm confused why this is happening.  sda5 is UID 1bed0af4-d096-45bd-b6a1-b39531a03665.  But it keeps claiming it doesen't exist, when it is.  the fact that I've tried a clean install of Ubuntu 3 times and the issue persists is just strange.

---

### Post by Bashing-om on 2017-11-11
chainbade84; Yeah -

Agreed - a bit of a head scratcher.

Let's boot a liveUSB and see what then we can find out .
from the live environment:
```

sudo blkid -c /dev/null

```
this will give all UUIDs in use by partitions / drives etc. The "-c /dev/null" forces blkid to poll the hardware for the UUID so as not take it from an OS cached file.

And now we look and compare. mount the target sda5 ( maybe ??)
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda5 /mnt/looksee
cat /mnt/looksee /etc/fstab
cat /mnt/looksee/etc/default/grub
cat /mnt/looksee/boot/grub/grub.cfg 

```

All ducks in a row ?? All UUIDs look sane ?

when done looking about .. we must UN-mount what we mounted :
```

sudo umount /mnt/looksee

```

just try'n to make sense of non-sense; as of yet I too do not get it .

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by chainbade84 on 2017-11-11
> **Bashing-om said:**
> chainbade84; Yeah -

Agreed - a bit of a head scratcher.

Let's boot a liveUSB and see what then we can find out .
from the live environment:
```

sudo blkid -c /dev/null

```
this will give all UUIDs in use by partitions / drives etc. The "-c /dev/null" forces blkid to poll the hardware for the UUID so as not take it from an OS cached file.

And now we look and compare. mount the target sda5 ( maybe ??)
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda5 /mnt/looksee
cat /mnt/looksee /etc/fstab
cat /mnt/looksee/etc/default/grub
cat /mnt/looksee/boot/grub/grub.cfg 

```

All ducks in a row ?? All UUIDs look sane ?

when done looking about .. we must UN-mount what we mounted :
```

sudo umount /mnt/looksee

```

just try'n to make sense of non-sense; as of yet I too do not get it .[INDENT][INDENT]together we can
[/INDENT]
[/INDENT]


Ya all UUID's look the same and match what the sudo blkid -c /dev/null command said, which was:

```
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="CE3E58513E583525" TYPE="ntfs" PARTUUID="e5e81164-01"
/dev/sda2: UUID="0C4C63244C6307B2" TYPE="ntfs" PARTUUID="e5e81164-02"
/dev/sda5: UUID="1bed0af4-d096-45bd-b6a1-b39531a03665" TYPE="ext4" PARTUUID="e5e81164-05"
/dev/sdb1: LABEL="Data" UUID="2CD450A3D45070D6" TYPE="ntfs" PARTUUID="6cfe656c-01"
/dev/sdc1: LABEL="UUI" UUID="24AC-56AD" TYPE="vfat" PARTUUID="2dbd2b5d-01"


```

if you want to take a look at the grub.cfg, here it is:

```
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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
else
  search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-1bed0af4-d096-45bd-b6a1-b39531a03665' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
    else
      search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
    fi
        linux    /boot/vmlinuz-4.13.0-16-generic root=UUID=1bed0af4-d096-45bd-b6a1-b39531a03665 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.13.0-16-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-1bed0af4-d096-45bd-b6a1-b39531a03665' {
    menuentry 'Ubuntu, with Linux 4.13.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-16-generic-advanced-1bed0af4-d096-45bd-b6a1-b39531a03665' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
        else
          search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
        fi
        echo    'Loading Linux 4.13.0-16-generic ...'
            linux    /boot/vmlinuz-4.13.0-16-generic root=UUID=1bed0af4-d096-45bd-b6a1-b39531a03665 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.13.0-16-generic
    }
    menuentry 'Ubuntu, with Linux 4.13.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.13.0-16-generic-recovery-1bed0af4-d096-45bd-b6a1-b39531a03665' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
        else
          search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
        fi
        echo    'Loading Linux 4.13.0-16-generic ...'
            linux    /boot/vmlinuz-4.13.0-16-generic root=UUID=1bed0af4-d096-45bd-b6a1-b39531a03665 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.13.0-16-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
    else
      search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  1bed0af4-d096-45bd-b6a1-b39531a03665
    else
      search --no-floppy --fs-uuid --set=root 1bed0af4-d096-45bd-b6a1-b39531a03665
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-CE3E58513E583525' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  CE3E58513E583525
    else
      search --no-floppy --fs-uuid --set=root CE3E58513E583525
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by Bashing-om on 2017-11-11
chainbade84; Hu,,, ...

I do not see a thing I can point a finger at . All looks like should workie .

I will have to consider for a spell - see if I can come up with a means to proceed.

sometimes I do wonder
[INDENT][INDENT]other times - I just do not know
[/INDENT][/INDENT]

---

### Post by chainbade84 on 2017-11-11
> **Bashing-om said:**
> chainbade84; Hu,,, ...

I do not see a thing I can point a finger at . All looks like should workie .

I will have to consider for a spell - see if I can come up with a means to proceed.

sometimes I do wonder[INDENT][INDENT]other times - I just do not know
[/INDENT]
[/INDENT]


ya it's the damnedest thing.  I figured a clean install would fix it but it didn't.  I'm going to try to install Kubuntu just to see if it happens to work...

---

### Post by Bashing-om on 2017-11-12
chainbade84; Well

As you have already re-installed several times .. I can not see how an install of Kubuntu will have a different result .

I keep thinking about this - and as I know no better - is to see what results when we re-install grub . But I can not justify this action except we may get a hint of what is not taking place .

[INDENT]right wrong or otherwise
[INDENT][INDENT][INDENT]do something[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2017-11-12
You never said if typing exit at busybox error worked or not.

A full reinstall of grub & a new kernel sometimes works also. You can use Boot-Repair or full chroot.
Sometimes initramfs is not fully configured and new kernel recreates it.

If drive was slow coming up, this sometimes works. But that has been more for slow external drives that may take longer to load.
 May need to add boot parameter for drive to come up to speed.
 GRUB_CMDLINE_LINUX="rootdelay=90"

---

