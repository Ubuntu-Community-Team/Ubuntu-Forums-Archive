---
title: "installing both windows 7 and ubuntu (newbie)"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by luckyvictor on 2010-11-04
Hi all

I am a newbie, and would like to start using ubuntu.

I have windows 7 installed on C driver my computer already, and a D drive for data, and I would like to create a partition (F driver) for installing ubuntu.

Now my question is

what file system should I create for ubuntu to install please? FAT32/NTFS/Ext2/Ext3?

My windows 7 is on NTFS, and what file system should my data drive be in order to let both windows 7 and ubuntu to be able to read and write please?

(if the above is impossible due to different file system, is there a third party solution?)
Many thanks

---

### Post by wilee-nilee on 2010-11-04
> **luckyvictor said:**
> Hi all

I am a newbie, and would like to start using ubuntu.

I have windows 7 installed on C driver my computer already, and a D drive for data, and I would like to create a partition (F driver) for installing ubuntu.

Now my question is

what file system should I create for ubuntu to install please? FAT32/NTFS/Ext2/Ext3?

My windows 7 is on NTFS, and what file system should my data drive be in order to let both windows 7 and ubuntu to be able to read and write please?

(if the above is impossible due to different file system, is there a third party solution?)
Many thanks

In Linux speak the letters for partitions mean nothing just so you know. It is confusing enough that we want to be on the same page.;)

Boot a live cd of Ubuntu go to gparted and take a screen shot and post it.

You have two options a wubi install which is a psuedo virtual install inside of Windows, has its merits and drawbacks, no partitioning needed and is installed inside a live windows setup.

The second is a dualboot with a install to the HD directly alongside another OS. Generally this is the stablest way to install, but the wubi is usable but a little more tricky, and much more difficult to get help with on the forum due to low usage, probably.

You have asked some questions I have not answered and wont really be able to unless I see your set up.

It probably would be helpful to post the bootscript in my signature, read the site link on how to run the script. Come back and post the text in code tags as described in my signature. Some computers come with newer bootloaders that can be tricky so we just want to know as much as we can before proceeding just to be safe.

---

### Post by luckyvictor on 2010-11-05
Thank you for replying me.

I read your reply, but the bootinfo script requires me to Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection, which I dun have one yet (not have ubuntu download to run as live or to install)

the reason is I m still preparing the hard disk environment for installing ubuntu, the following is my current setting (all in one single disk)

C: windows 7 install, NTFS
D: data, NTFS
E: will be used for ubuntu installed, NTFS/FAT32/Ext2/Ext3

so my question is what file system I should use on E for ubuntu to install successfully? as I know NTFS probably won't work, as it is windows structure.

and my second question is whether I could change the file system of D: so that it can be read/write from both windows 7 and ubuntu.

Once again thank you

---

### Post by Mark Phelps on 2010-11-05
BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD. You will need this later to repair the Win7 boot loader should something go wrong during your dual-boot setup.

Since it looks like you're already using the Win7 Disk Management utility to shrink your current partitions to make room for Ubuntu, you'll be OK.  Just don't let the Ubuntu installer shrink the partitions.

Finally, be very careful during the installation.  The new installer is much more confusing than the old one in that it has lead folks to accidentally reformat their Win7 partitions.

---

### Post by celldweller1591 on 2010-11-05
Depending upon the size of E and your choice of partitioning, you can do the following : 
Format E and make it a 60-80% of it as EXT4 and set mount point as root. Make another partition of exactly double the size of your ram and make mount point Swap filesystem. If you ahve disk space still left, then create EXT4 partition and set mount point /home. Done. 
This should be easiest workable partition table for your Ubuntu system. Install Ubuntu and enjoy. If after install, ubuntu wont show your win7 boot entry, then open the terminal and type "sudo update-grub" and reboot.

For details see [here]("www.linoob.com/2009/12/wubi-windows-based-ubuntu-installer") (screenshots available)

---

### Post by luckyvictor on 2010-11-05
> **Mark Phelps said:**
> BEFORE you do anything else, boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD. You will need this later to repair the Win7 boot loader should something go wrong during your dual-boot setup.

Since it looks like you're already using the Win7 Disk Management utility to shrink your current partitions to make room for Ubuntu, you'll be OK.  Just don't let the Ubuntu installer shrink the partitions.

Finally, be very careful during the installation.  The new installer is much more confusing than the old one in that it has lead folks to accidentally reformat their Win7 partitions.

so should I use NTFS or FAT32 or Ext2 or Ext3 for this empty partition prepared for ubuntu to install?

---

### Post by luckyvictor on 2010-11-05
> **celldweller1591 said:**
> Depending upon the size of E and your choice of partitioning, you can do the following : 
Format E and make it a 60-80% of it as EXT4 and set mount point as root. Make another partition of exactly double the size of your ram and make mount point Swap filesystem. If you ahve disk space still left, then create EXT4 partition and set mount point /home. Done. 
This should be easiest workable partition table for your Ubuntu system. Install Ubuntu and enjoy. If after install, ubuntu wont show your win7 boot entry, then open the terminal and type "sudo update-grub" and reboot.

For details see [here]("www.linoob.com/2009/12/wubi-windows-based-ubuntu-installer") (screenshots available)

I have only NTFS, FAT32, Ext2 and Ext3, but no Ext4, so does it mean I can't do what you taught me?

by the way, how to set mount point please?

---

### Post by wilee-nilee on 2010-11-05
> **luckyvictor said:**
> I have only NTFS, FAT32, Ext2 and Ext3, but no Ext4, so does it mean I can't do what you taught me?

by the way, how to set mount point please? 

Please read my post and Mark Phelps, I think you may be acting to quick without the proper understanding.

You are going to need  Ubuntu Live cd even if you install inside of windows with wubi. Stop what your doing download it burn it or load a thumb run the bootscript and post the txt.

---

### Post by wilee-nilee on 2010-11-05
> **celldweller1591 said:**
> Depending upon the size of E and your choice of partitioning, you can do the following : 
Format E and make it a 60-80% of it as EXT4 and set mount point as root. Make another partition of exactly double the size of your ram and make mount point Swap filesystem. If you ahve disk space still left, then create EXT4 partition and set mount point /home. Done. 
This should be easiest workable partition table for your Ubuntu system. Install Ubuntu and enjoy. If after install, ubuntu wont show your win7 boot entry, then open the terminal and type "sudo update-grub" and reboot.

For details see [here]("www.linoob.com/2009/12/wubi-windows-based-ubuntu-installer") (screenshots available)

**Your mixing together a discussion of partitioning and using a wubi link this is bad information in the way it is mixed together, especially for a user that may not recognize this. **

You do not do any partitioning for a wubi install, which it seems the OP is trying, but doesn't understand the whole parameters of this type of install. I.E the difference between a wubi and a standard dual boot.

---

### Post by luckyvictor on 2010-11-05
> **wilee-nilee said:**
> Please read my post and Mark Phelps, I think you may be acting to quick without the proper understanding.

You are going to need  Ubuntu Live cd even if you install inside of windows with wubi. Stop what your doing download it burn it or load a thumb run the bootscript and post the txt.

ok, I am downloading the ubuntu now and will do it in 10 mins.

I was thinking I can just install it on a partition like installing windows.

---

### Post by wilee-nilee on 2010-11-05
> **luckyvictor said:**
> ok, I am downloading the ubuntu now and will do it in 10 mins.

I was thinking I can just install it on a partition like installing windows.

You probably can but there has been a mixture of wubi and real dual installs to a partition that seemed mixed up. My concern is
#1 You don't lose anything
#2 That you understand what your doing.

I think the understanding is a bit of part of the problem, no big deal we have all been there.;)

It seemed as though you didn't recognize needing the live cd to install to a actual partition=a true dual boot.

---

### Post by luckyvictor on 2010-11-05
```

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

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    15,958,015    15,955,968  83 Linux
/dev/sda2          15,960,062    16,775,167       815,106   5 Extended
/dev/sda5          15,960,064    16,775,167       815,104  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ae8eb20f-4e04-478d-b1c2-4ca630922a9f   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        60dde7d8-20aa-47a7-a25e-66c7369555b4   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/VBOXADDITIONS_3.2.8_64453 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
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
search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
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
	search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ae8eb20f-4e04-478d-b1c2-4ca630922a9f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ae8eb20f-4e04-478d-b1c2-4ca630922a9f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ae8eb20f-4e04-478d-b1c2-4ca630922a9f
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
UUID=ae8eb20f-4e04-478d-b1c2-4ca630922a9f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=60dde7d8-20aa-47a7-a25e-66c7369555b4 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/core.img
   4.9GB: boot/grub/grub.cfg
   4.9GB: boot/initrd.img-2.6.32-24-generic
   1.1GB: boot/vmlinuz-2.6.32-24-generic
   4.9GB: initrd.img
   1.1GB: vmlinuz

```

Thanks for helping again, I don't know the world of linux much, what I want is when I start up my computer, there is a menu for me to select either Windows 7 or Ubuntu, does it mean I want a dual boot with the ubuntu actually installed on my empty partition E: please?

---

### Post by luckyvictor on 2010-11-05
I run this ubuntu in VirtualBox, in case it may affect the result.

---

### Post by wilee-nilee on 2010-11-05
> **luckyvictor said:**
> I run this ubuntu in VirtualBox, in case it may affect the result.

You need to burn a cd or load a thumb drive. I have run the script from a virtual with the guest additions enabled and had it read correctly. **But I wont help you if you don't run it off a booted live environment**; I feel that is leaving to much to chance.

The script you posted is only showing the vbox.

---

### Post by luckyvictor on 2010-11-05
ok, will run another soon

---

### Post by wilee-nilee on 2010-11-05
> **luckyvictor said:**
> ok, will run another soon

Thanks, Do you have your W7 backed up and do you have a recovery disc or install disc for W7?

---

### Post by wilee-nilee on 2010-11-06
I am going to assume here that you have everything covered and remove the auto-email. Hope this is the case.;)

---

### Post by luckyvictor on 2010-11-07
I was away for a few days...so didn't get any step further.

However, in the mean time, a friend of mine send me the following to help me, so should I just follow this tutorial in my case?

[http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)

I just wonder is GRUB came with Ubuntu, so once I install ubuntu and restart it, GRUB boot loader will start automatically every time I start up my computer?

---

