---
title: "can't boot into ubuntu, stuck at boot menu"
date: 2014-03-13
forum: Installation &amp; Upgrades
---

### Post by chris189 on 2014-03-13
Hi all, I am having trouble booting into my ubuntu installation. Details are at:
[http://paste.ubuntu.com/7082816](http://paste.ubuntu.com/7082816)

I have a Samsung laptop that was reformatted before I installed ubuntu via USB stick. When I turn the computer on it appears to restart 1x before loading up the boot menu. It the shows 1) windows boot manager 2) windows boot manager 3) SATA CD. I do not have windows installed. I do not see an option for the SATA HD where i installed ubuntu. If I look at the BIOS, the SATA HD does show up. If i select any of the 3 options it flashes black and then goes back to this menu. If i hit ESC it reboots and I end up at this boot menu again. 

I have disabled Fast BIOS, disabled Secure Boot and OS mode selection is UEFI OS.

Thanks for your help.

---

### Post by chkneater on 2014-03-13
There's a certain way you have to wipe windows off to fully get all the files off becaue MS does not want people to start using the much superior Linux.  

I'm not sure how to do it but a simple search of "wipe windows" or something like that you should find something.

---

### Post by chris189 on 2014-03-13
the weird thing is that it worked after a certain # of reboots 1x and then i used it and saved a bunch of stuff on it. now i rebooted again and can't remember what i did to get into ubuntu and as a result can't access my files...

---

### Post by nibal on 2014-03-13
> **chris189 said:**
> the weird thing is that it worked after a certain # of reboots 1x and then i used it and saved a bunch of stuff on it. now i rebooted again and can't remember what i did to get into ubuntu and as a result can't access my files...

So, what is the status now? Can boot, but not access your files, or cannot boot at all? Use the following procedure to try different boot configurations:

Boot from your live CD. Choose  "Try Ubuntu". You will get to a desktop. Open a terminal and type:

```


sudo mount <root partition> /mnt
sudo mount /boot /mnt/boot     (only if boot loader is in a separate partition)
sudo mount --bind -t proc /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt
grub-install


```

where <root partition> is your "/" filesystem (i.e. /dev/sda7)
grub-install will overwrite mbr and should remove any windows leftovers.
Lastly type:

```


grub-mkconfig -o /boot/grub/grub.cfg (or wherever is your grub.cfg)


```

Check the terminal output for any windows partitions. Clean them up and reboot.

HTH,
Nikos

---

### Post by chris189 on 2014-03-13
i can boot into the BIOS and boot menu (where I see the 2 windows boot manager options) but i cannot get into grub/ubuntu. will try your suggestions. thanks.

---

### Post by oldfred on 2014-03-13
You have installed Ubuntu in BIOS/CSM/Legacy boot mode. 
You have no UEFI. So turn off UEFI or turn on BIOS boot mode in UEFI/BIOS menu.
I do not think you are getting Windows boot menu as you have no Windows, but are getting a UEFI type menu.

Other have post menus like these.

---

### Post by chris189 on 2014-03-13
when i chose CSM only in the BIOS the boot menu came up again but it was only for the SATA CD drive. no other options. did i miss something? thanks

---

### Post by oldfred on 2014-03-13
What boot menu? UEFI/BIOS?
And booting a hard drive is how BIOS boots.  If several drives you then have to choose which drive to boot from.

Since you have only one install, you will not get grub menu unless you hold shift key (some with UEFI need escape key) until menu appears.

And if just getting blank screen in BIOS boot mode you may need to bring up grub menu and add nomodeset or other boot parameters.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by chris189 on 2014-03-15
> **oldfred said:**
> You have installed Ubuntu in BIOS/CSM/Legacy boot mode. 
You have no UEFI. So turn off UEFI or turn on BIOS boot mode in UEFI/BIOS menu.
I do not think you are getting Windows boot menu as you have no Windows, but are getting a UEFI type menu.

Other have post menus like these.

exactly, my menu is like the second image you posted, the UEFI/CSM one. so I am unable to get into the BIOS per se still. I tried UEFI OS only, CSM OS only, and UEFI and CSM OS and still getting stuck at the Boot Menu.

the title of my menu is "Phoenix SecureCore Tiano Setup"

---

### Post by chris189 on 2014-03-16
> **nibal said:**
> So, what is the status now? Can boot, but not access your files, or cannot boot at all? Use the following procedure to try different boot configurations:

Boot from your live CD. Choose  "Try Ubuntu". You will get to a desktop. Open a terminal and type:

```


sudo mount <root partition> /mnt
sudo mount /boot /mnt/boot     (only if boot loader is in a separate partition)
sudo mount --bind -t proc /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
chroot /mnt
grub-install


```

where <root partition> is your "/" filesystem (i.e. /dev/sda7)
grub-install will overwrite mbr and should remove any windows leftovers.
Lastly type:

```


grub-mkconfig -o /boot/grub/grub.cfg (or wherever is your grub.cfg)


```

Check the terminal output for any windows partitions. Clean them up and reboot.

HTH,
Nikos

i think my root partition is /dev/sda1 and i went through the step accodingly. still have the same error. any ideas? does the fact when i restart it gets to the samsung logo and then automatically reboots again before going to boot menu provide any additional debug information? thx.

---

### Post by oldfred on 2014-03-16
Because you have drive in MBR(msdos) partitioning, you can only boot in BIOS mode, not UEFI.
You have to have gpt partitioning to use UEFI and Windows only boots from gpt with UEFI.
But Ubuntu can boot from gpt with BIOS or UEFI if correct support partitions are on drive.

So only try booting with BIOS, hold shift key to get grub menu and try nomodeset or other boot parameters.
Some old BIOS systems would not boot past 137GB on a drive, so then a small  20 or 25GB / at beginning of drive and rest of the drive as /home or data partition(s) would work. I have yet to see a UEFI system need that change. But what mode are hard drives in in UEFI/BIOS. Should be AHCI, not RAID nor IDE.

---

### Post by chris189 on 2014-03-23
thanks. holding down shift doesn't do anything. i still go to the boot menu where i can go change the boot priority, etc but the HDD still doesn't show up.
could it be anything else?

---

### Post by oldfred on 2014-03-23
Sometimes with UEFI systems you have to use escape key, not shift.

What does one time boot key show?

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by chris189 on 2014-03-23
when i hit f2 it is the same as the app setup which i believe is the bios
the screen looks the same as this [http://imageshack.us/a/img805/9348/dsc0266qa.jpg](http://imageshack.us/a/img805/9348/dsc0266qa.jpg)
boot menu shows 1) windows boot manager 2) windows boot manager 3) SATA CD and nothing else

---

### Post by chris189 on 2014-03-23
[ATTACH]251416[/ATTACH]

i have attached the bootinfoscript results if that helps...

---

### Post by chris189 on 2014-03-23
i have attached the bootinfoscript results if that helps...

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   476,426,239   476,424,192  83 Linux
/dev/sda2         476,428,286   488,396,799    11,968,514   5 Extended
/dev/sda5         476,428,288   488,396,799    11,968,512  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3926 MB, 3926949888 bytes
64 heads, 32 sectors/track, 3745 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             64     1,497,087     1,497,024  17 Hidden NTFS / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        bb520670-dcf2-4d7c-9bd3-aaed09d4928e   ext4       
/dev/sda5        4cb277ed-e978-495f-82da-011ddf757b77   swap       
/dev/sdb1                                               iso9660    Ubuntu 12.04.4 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.11.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=bb520670-dcf2-4d7c-9bd3-aaed09d4928e ro   quiet splash nomodeset $vt_handoff
    initrd    /boot/initrd.img-3.11.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.11.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    echo    'Loading Linux 3.11.0-15-generic ...'
    linux    /boot/vmlinuz-3.11.0-15-generic root=UUID=bb520670-dcf2-4d7c-9bd3-aaed09d4928e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.11.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    linux    /boot/vmlinuz-3.2.0-59-generic-pae root=UUID=bb520670-dcf2-4d7c-9bd3-aaed09d4928e ro   quiet splash nomodeset $vt_handoff
    initrd    /boot/initrd.img-3.2.0-59-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    echo    'Loading Linux 3.2.0-59-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-59-generic-pae root=UUID=bb520670-dcf2-4d7c-9bd3-aaed09d4928e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-59-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb520670-dcf2-4d7c-9bd3-aaed09d4928e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bb520670-dcf2-4d7c-9bd3-aaed09d4928e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4cb277ed-e978-495f-82da-011ddf757b77 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.11.0-15-generic              1
               =                boot/initrd.img-3.2.0-59-generic-pae           1
               =                boot/vmlinuz-3.11.0-15-generic                 1
               =                boot/vmlinuz-3.2.0-59-generic-pae              1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  01 43 44 30 30 31 01 00  20 20 20 20 20 20 20 20  |.CD001..        |
00000010  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
00000020  20 20 20 20 20 20 20 20  55 62 75 6e 74 75 20 31  |        Ubuntu 1|
00000030  32 2e 30 34 2e 34 20 4c  54 53 20 69 33 38 36 20  |2.04.4 LTS i386 |
00000040  20 20 20 20 20 20 20 20  00 00 00 00 00 00 00 00  |        ........|
00000050  00 b6 05 00 00 05 b6 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  01 00 00 01 01 00 00 01  |................|
00000080  00 08 08 00 6a 02 00 00  00 00 02 6a 57 00 00 00  |....j......jW...|
00000090  00 00 00 00 00 00 00 58  00 00 00 00 22 00 23 00  |.......X....".#.|
000000a0  00 00 00 00 00 23 00 08  00 00 00 00 08 00 72 02  |.....#........r.|
000000b0  04 0c 0c 25 00 02 00 00  01 00 00 01 01 00 20 20  |...%..........  |
000000c0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000001b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 58 4f  |              XO|
000001c0  52 52 49 53 4f 2d 31 2e  31 2e 38 20 32 30 31 31  |RRISO-1.1.8 2011|
000001d0  2e 31 31 2e 32 30 2e 31  37 33 30 30 31 2c 20 4c  |.11.20.173001, L|
000001e0  49 42 49 53 4f 42 55 52  4e 2d 31 2e 31 2e 38 2c  |IBISOBURN-1.1.8,|
000001f0  20 4c 49 42 49 53 4f 46  53 2d 31 2e 31 2e 36 2c  | LIBISOFS-1.1.6,|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

 
```

---

### Post by oldfred on 2014-03-24
Did you install a 32 bit version?

Only 64bit works with UEFI, but the 32 bit should work in BIOS boot mode, just that then you are not using all the resources of a new system.

---

### Post by chris189 on 2014-03-24
yup. 32 bit.

---

### Post by frank18 on 2014-03-24
> **chris189 said:**
> yup. 32 bit.



have you tried to use the (Try Ubuntu before install) and then when you're running it from the Cd or USB drive, on the desktop there is an option app that says Install Ubuntu.

---

### Post by oldfred on 2014-03-24
I might try the 64 bit also.

One user posted this a while back.
>  (Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.



---

### Post by chris189 on 2014-03-24
> **frank18 said:**
> have you tried to use the (Try Ubuntu before install) and then when you're running it from the Cd or USB drive, on the desktop there is an option app that says Install Ubuntu.

yup, thats how i ran boot-repair. didn't change the boot problems though.

---

### Post by chris189 on 2014-03-24
> **oldfred said:**
> I might try the 64 bit also.

One user posted this a while back.

would i install it on a new partition? i would be able to access my files from the 32 bit install?

---

### Post by oldfred on 2014-03-25
If you have room for another / partition of 10 to 25GB. I have many installs to test something on my sdc drive.
I use shared data partitions for most of my data, but can access my other installs. Sometimes there are permission or ownership type issues, but sudo solves those type issues on a temporary basis.

---

