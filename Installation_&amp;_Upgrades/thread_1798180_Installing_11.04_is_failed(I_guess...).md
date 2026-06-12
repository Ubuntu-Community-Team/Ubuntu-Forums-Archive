---
title: "Installing 11.04 is failed(I guess...)"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by makotoMikeness on 2011-07-06
Hello. I would like you guys to help.
I updated Ubuntu this morning and It didn't work right.I'm not sure what version it was before I start updating, but I'm sure to say it was version 10.xx. and I'm running Ubuntu by VMWare.

After finished updating, Ubuntu had restarted then it says 
--------------------------
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]

sh:grub>
--------------------------
When I started updating Ubuntu, it seemed that it's working right. I confirmed a few phases to replace some of things to finish updating. then Ubuntu had just restarted as usual.

I googled about this kind of situation, but I still can't fix it. 
There are papers to due in my Documents directly. How do you rescue those files? I checked those files were still there by using command ls (0,5)/home/user/Documents/Papers/"my files".

I need your help to fix this.
If you have any questions, please ask me.
I'm so sorry for my bad English.
Thanks for reading.

---

### Post by Rubi1200 on 2011-07-06
Hi and welcome to the forums :-)

Please post the specifications for the computer such as RAM and graphics card.

To get a better overview of the current state of the system, do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by makotoMikeness on 2011-07-07
Hi, Rubi1200! Thanks for replying.
I took a test an hour ago for my calculus class. I'm kinda tired now(btw lol).

I download Ubuntu 10.10 from Ubuntu Japan Team site as the googled results. Because I couldn't find a file called exact same as Ubuntu Live CD. After It finished downloadin the file, I mounted that downloaded ISO image file with VMWare. It automatically started installing Ubuntu on another virtual machine built with VMWare. There was no option to choose. Ubuntu 10.10 is now installed and smoothly booted. So I have just done what you told me.
--------------------------
Laptop 
--------------------------
Host OS : Windows 7 64bit
RAM : 4GB
Processor : Intel Core i3 CPU M 380 @ 2.53GHz
*I'm not sure about the graphic chip set. but, i thought it was on board. and Intel VT is already enabled. 
--------------------------

I hit the command then it created RESULTS.txt as you told.
Here's what's inside of this file.
I hope I have done all things right.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 21.5 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    40,105,983    40,103,936  83 Linux
/dev/sda2          40,108,030    41,940,991     1,832,962   5 Extended
/dev/sda5          40,108,032    41,940,991     1,832,960  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d6e3d434-908d-4734-a60a-a0e5ea00b6c7   ext4       
/dev/sda5        dcf81a95-cbe8-4ab6-9cc3-ba8deee021f8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d6e3d434-908d-4734-a60a-a0e5ea00b6c7 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d6e3d434-908d-4734-a60a-a0e5ea00b6c7 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d6e3d434-908d-4734-a60a-a0e5ea00b6c7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=d6e3d434-908d-4734-a60a-a0e5ea00b6c7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dcf81a95-cbe8-4ab6-9cc3-ba8deee021f8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.624237061 = 4.965236736    boot/grub/core.img                             1
   4.204727173 = 4.514791424    boot/grub/grub.cfg                             1
   0.516601562 = 0.554696704    boot/initrd.img-2.6.35-22-generic              2
   4.629974365 = 4.971397120    boot/vmlinuz-2.6.35-22-generic                 1
   0.516601562 = 0.554696704    initrd.img                                     2
   4.629974365 = 4.971397120    vmlinuz                                        1

```

---

### Post by Rubi1200 on 2011-07-07
Hi,
I don't see anything immediately wrong with the results text, but something may have got messed up after the updates you did.

The first thing to try is reinstall GRUB from the LiveCD:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

After rebooting and taking out the CD run this command back in Ubuntu:

```
sudo update-grub
```

---

### Post by makotoMikeness on 2011-07-09
Hi.
I accidentally installed Ubuntu to another virtual machine.  I didn't boot Ubuntu from CD. So, it didn't worked as you expected.
Now, I booted Ubuntu 10.10 form Live CD and did that command again.
Here's the result:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

&#12487;&#12451;&#12473;&#12463; /dev/sda: 37.6 GB, 37580963840 &#12496;&#12452;&#12488;
&#12504;&#12483;&#12489; 255, &#12475;&#12463;&#12479; 63, &#12471;&#12522;&#12531;&#12480; 4568, &#21512;&#35336; 73400320 &#12475;&#12463;&#12479;
Units = &#12475;&#12463;&#12479;&#25968; of 1 * 512 = 512 &#12496;&#12452;&#12488;
&#12475;&#12463;&#12479;&#12469;&#12452;&#12474; (&#35542;&#29702; / &#29289;&#29702;): 512 &#12496;&#12452;&#12488; / 512 &#12496;&#12452;&#12488;

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     1,959,929     1,959,867  82 Linux swap / Solaris
/dev/sda2           1,959,930    20,964,824    19,004,895   5 Extended
/dev/sda5           1,959,993    20,964,824    19,004,832  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        c6cb9ad0-25b5-49c6-a57c-1470d3447dff   swap       
/dev/sda5        9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
true
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9bc1e7e4-02c1-43b2-87b5-6c38bf17aa53 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=c6cb9ad0-25b5-49c6-a57c-1470d3447dff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.055504322 = 4.354564608    boot/grub/core.img                             1
   1.225231647 = 1.315582464    boot/grub/grub.cfg                             1
   3.226879597 = 3.464835584    boot/initrd.img-2.6.31-14-generic              2
   6.791069508 = 7.291855360    boot/initrd.img-2.6.31-20-generic              1
   8.771484852 = 9.418310144    boot/initrd.img-2.6.32-32-generic              2
   9.481472492 = 10.180653568   boot/initrd.img-2.6.35-30-generic              2
   2.442158222 = 2.622247424    boot/initrd.img-2.6.38-8-generic               7
   3.124050617 = 3.354423808    boot/vmlinuz-2.6.31-14-generic                 2
   3.596432209 = 3.861639680    boot/vmlinuz-2.6.31-20-generic                 2
   6.794830799 = 7.295894016    boot/vmlinuz-2.6.32-32-generic                 1
   8.775490284 = 9.422610944    boot/vmlinuz-2.6.35-30-generic                 1
   5.727871418 = 6.150255104    boot/vmlinuz-2.6.38-8-generic                  2
   2.442158222 = 2.622247424    initrd.img                                     7
   9.481472492 = 10.180653568   initrd.img.old                                 2
   5.727871418 = 6.150255104    vmlinuz                                        2
   8.775490284 = 9.422610944    vmlinuz.old                                    1


```

For these commands:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

and I could access to Documents including my papers.
So, I zipped it and sent it to my windows.

---

### Post by Rubi1200 on 2011-07-09
The final error happened because you ran the command from the LiveCD not from _within_ the installation as I told you:

> [COLOR=Red]ubuntu@ubuntu[/COLOR]:~$ sudo update-grub /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

In any event, can you now boot Ubuntu normally yes or no?

If no, what happens? Are there error messages?

Please tell us as much as you can.

Thanks.

---

### Post by makotoMikeness on 2011-07-09
Thank you! Now, it's working!
By the by, what was wrong with this?

---

### Post by Rubi1200 on 2011-07-09
Excellent! I am really pleased you got this sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

If you mean what caused the problems in the first place? I don't know; possibly something to do with the updates.

Good luck and enjoy using Ubuntu.

---

