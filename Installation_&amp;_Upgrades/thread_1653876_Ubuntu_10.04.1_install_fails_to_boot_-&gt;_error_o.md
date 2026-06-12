---
title: "Ubuntu 10.04.1 install fails to boot -&gt; error: out of disk, grub rescue"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by pacman5 on 2010-12-27
Downloaded Ubuntu 10.04.1 Desktop AMD64, tried to install it to a cleand HDD using the whole HDD, i.e. gave it permission to use the whole HDD. Installation process appeared to run OK but when it came to the restart it just fired up the message

error: out of disk
grub rescue>

I've searched this forum and found numerous references to these error messages but cannot make head nor tail of the diagnostic suggestions. Apart from anything else they suggest strings of command lines which I don't understand and can't enter anyway since they don't correspond to my keyboard layout (if I hit > or ) something completely different appears on the screen).

Is there someone here who can provide a step-by-step solution in lay language ? Or is there such a thing as a bootable file which can be downloaded and inserted into my CD drive to correct this problem ?

Thank you.

---

### Post by wilee-nilee on 2010-12-27
> **pacman5 said:**
> Downloaded Ubuntu 10.04.1 Desktop AMD64, tried to install it to a cleand HDD using the whole HDD, i.e. gave it permission to use the whole HDD. Installation process appeared to run OK but when it came to the restart it just fired up the message

error: out of disk
grub rescue>

I've searched this forum and found numerous references to these error messages but cannot make head nor tail of the diagnostic suggestions. Apart from anything else they suggest strings of command lines which I don't understand and can't enter anyway since they don't correspond to my keyboard layout (if I hit > or ) something completely different appears on the screen).

Is there someone here who can provide a step-by-step solution in lay language ? Or is there such a thing as a bootable file which can be downloaded and inserted into my CD drive to correct this problem ?

Thank you.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by pacman5 on 2010-12-27
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,238,208,511 1,238,206,464  83 Linux
/dev/sda2       1,238,210,558 1,250,263,039    12,052,482   5 Extended
/dev/sda5       1,238,210,560 1,250,263,039    12,052,480  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        fbfbca6e-caf1-4170-b284-1962db0f2200   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ae25de63-6491-4882-82d3-99755ad8df84   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fbfbca6e-caf1-4170-b284-1962db0f2200 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fbfbca6e-caf1-4170-b284-1962db0f2200 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fbfbca6e-caf1-4170-b284-1962db0f2200
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
UUID=fbfbca6e-caf1-4170-b284-1962db0f2200 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ae25de63-6491-4882-82d3-99755ad8df84 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 601.4GB: boot/grub/core.img
 395.3GB: boot/grub/grub.cfg
 601.4GB: boot/initrd.img-2.6.32-24-generic
 601.4GB: boot/vmlinuz-2.6.32-24-generic
 601.4GB: initrd.img
 601.4GB: vmlinuz
```

---

### Post by pacman5 on 2010-12-27
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

Report text just posted but I couldn't work out where to insert thanks for your help without it being interpreted as code  :-))

---

### Post by wilee-nilee on 2010-12-27
Script looks basically okay, but lets just reload the grub bootloader and see if that works. So boot the live cd of 10.04 and run these two commands in its terminal.

```
sudo mount /dev/sda1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot to the Ubuntu install make sure the cd is not in the tray. If you get into the install open a terminal there and run.
```
sudo update-grub
```

---

### Post by presence1960 on 2010-12-27
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by pacman5 on 2010-12-28
> **wilee-nilee said:**
> Script looks basically okay, but lets just reload the grub bootloader and see if that works. So boot the live cd of 10.04 and run these two commands in its terminal.

```
sudo mount /dev/sda1 /mnt
```
then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Then reboot to the Ubuntu install make sure the cd is not in the tray. If you get into the install open a terminal there and run.
```
sudo update-grub
```

Thank you.

Tried these commands, rebooted into the install and got the same error messages as before, i.e.

error: out of disk.
grub rescue>

Paddy

---

### Post by wilee-nilee on 2010-12-28
> **pacman5 said:**
> Thank you.

Tried these commands, rebooted into the install and got the same error messages as before, i.e.

error: out of disk.
grub rescue>

Paddy

I think post 6 is correct, it seems so I had looked at the link. I don't know if just another install will get it correct this time, or just purging and reinstalling grub. Sort of depends on others opinions and what you can or are willing to do.

---

### Post by pacman5 on 2010-12-28
> **presence1960 said:**
> [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

Thanks for this. I'm afraid I couldn't use it because the instructions under Temporary Solution read "At the Grub menu at boot up (you may have hold down the "shift" key during boot up or press "esc" during the count down to bring up the Grub menu):" and I don't get the GRUB menu in order to be able to execute these instructions.

So i inserted the Ubuntu CD and fired up from that and searched for a file called 10_linux and found it but nowhere in that file could I find the sequence

```
     menuentry "$1" {
     recordfail=1
     if  [ -n \${have_grubenv} ]; then save_env recordfail; fi

```

which is mentioned in the "Boot Problems:write" that you pointed me to.

So I'm still stuck.

Any other suggestions ?

Paddy

---

### Post by pacman5 on 2010-12-28
> **wilee-nilee said:**
> I think post 6 is correct, it seems so I had looked at the link. I don't know if just another install will get it correct this time, or just purging and reinstalling grub. Sort of depends on others opinions and what you can or are willing to do.

I tried Post 6 without success.

I've tried two successive installs with the same result.

How do I purge and reinstall GRUB ?

Thanks.

Paddy

---

### Post by wilee-nilee on 2010-12-28
So first if you want the grub menu it would be shift but if it doesn't show you could try the chroot purge and reload grub. Not sure if this is any of a fix hard to say.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I wonder if the CD is faulty, so using it to reload grub will cause the same problems. Same with consecutive installs.

---

### Post by pacman5 on 2010-12-28
> **wilee-nilee said:**
> So first if you want the grub menu it would be shift but if it doesn't show you could try the chroot purge and reload grub. Not sure if this is any of a fix hard to say.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I wonder if the CD is faulty, so using it to reload grub will cause the same problems. Same with consecutive installs.

Following your hint here I just downloaded and installed the latest version, 10.1, 32-bit and installed it and got the same result:

error: out of disk 
grub rescue

Paddy

---

### Post by presence1960 on 2010-12-28
> **pacman5 said:**
> Thanks for this. I'm afraid I couldn't use it because the instructions under Temporary Solution read "At the Grub menu at boot up (you may have hold down the "shift" key during boot up or press "esc" during the count down to bring up the Grub menu):" and I don't get the GRUB menu in order to be able to execute these instructions.

So i inserted the Ubuntu CD and fired up from that and searched for a file called 10_linux and found it but nowhere in that file could I find the sequence

```
     menuentry "$1" {
     recordfail=1
     if  [ -n \${have_grubenv} ]; then save_env recordfail; fi

```

which is mentioned in the "Boot Problems:write" that you pointed me to.

So I'm still stuck.

Any other suggestions ?

Paddy

When you boot the live CD don't look in File System for 10_linux. What you will find there is the live cd file system. You have to look in your hard disk's root directory for 10_linux

---

### Post by Yumi on 2010-12-28
Same problem here. I have my own thread unter "No grub menu at boot - changed install partition" and try to solve my similar problem. Will be watching here in case you find the solution first.

Michael

---

