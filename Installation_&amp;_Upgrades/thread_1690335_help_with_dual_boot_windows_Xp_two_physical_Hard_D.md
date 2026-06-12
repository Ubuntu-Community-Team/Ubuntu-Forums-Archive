---
title: "help with dual boot windows Xp two physical Hard Disks"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by jonathantalisman on 2011-02-18
Hi,
I'll try to give as much information and still be brief...
I have an (AMD 64bit)  machine with two hard disks and had windows XP 64 bit on the one drive and ubuntu 9.04 on the second . I wanted to start a clean install to replace the ubuntu 9.04 with 10.10 . Booted from CD and I think I pressed the erase and use entire disk for the ubuntu one.
After that I could not login into my windows Xp.[Grub loaded without the windows]
I then booted with windows CD and fixed the MBR.
I am guessing that the Grub was installed on the second disk and did not see the windows disk.

What I want is to use the second disk for Ubuntu and for grub to control the boot, I can then set the windows to be the default [my girlfriend/better half gets upset if she needs to call me to ask for assistance.]



The questions are:
1. should I use the specify partitions manually 
2. if so - what would be the recommended ratio/sizes for swap '/' and /home ?
3. where and how  do I set the grub to be installed?

Thanks , Jonathan


Here is the output from *sudo fdisk -lu *

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000edba6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011195

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   469968895   234983424   83  Linux
/dev/sdb2       469970942   488396799     9212929    5  Extended
/dev/sdb5       469970944   488396799     9212928   82  Linux swap / Solaris

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x57b4fd21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   586083329   293041633+   7  HPFS/NTFS
```

---

### Post by YesWeCan on 2011-02-18
It looks to me like you have 3 disks, 2x 250GB and 300GB. Do you have two Windows installations?

Anyhow, it doesn't matter.

What you probably want is for your Windows disks to be untouched. You want to boot off the Ubuntu disk and have the Windows installation(s) appear on the Grub menu, and to default to booting Windows.

The safe any easy way I use is to:
1. Disconnect the Windows disks. Only have the Ubuntu disk plugged in.
2. Install 10.10. Use the whole disk, do automatic partitioning.
3. After Ubuntu is intalled and you can reboot it ok (you wont see a grub menu this time), shut the PC down and reconnect the other 2 disks.
4. Configure the bios to boot the Ubuntu disk first and boot it (you won't see a grub menu this time either).
5. In a Ubuntu console type 'sudo update-grub'. This will cause grub to scan all your disks and add the Windows OSes to its menu.
6. Reboot. This time you should get a grub menu. Select Windows and make sure it boots it.

To tell grub which OS to boot as default you need to change the entry "GRUB_DEFAULT=" in the file /etc/default/grub.
I believe the default is the number of the OS in the grub boot menu list minus 1. So the first OS listed will be number 0, the next 1 and so on. When you reboot, count the entries in the menu. Then boot into ubuntu and edit the /etc/default/grub file and add the appropriate GRUB_DEFAULT= number. Then run 'sudo update-grub' again to activate the change. The next time you reboot it should default to the chosen OS.

Note, you should still be able to boot Windows directly by telling the bios to boot the Windows disk. So your original Windows installation(s) remain unchanged.

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums *jonathantalisman* :-)

Yes there seem to be 3 hard disk present in the PC.

I will agree with *YesWeCan*. For safety purposes, you can disconnect the XP HDD and install Ubuntu or if you feel confident, you can leave them plugged in but a little mistake might make you lose all the data unless you are doing a manual/advanced partitioning as there is a bug in 10.10 installer. I will recommend reading this page also. It will tell your about the bugs, partition sizes, mount points and all that stuff.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Grub needs to be installed to the MBR of the Ubuntu HDD. I say drive and not the partition. There is a section for Grub at the bottom of page I linked above.

And secondly, in order to give us a better overview of your system, you can boot an Ubuntu Live CD and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It is not absolutely necessary but will help us understand your XP install and all that stuff. No problem if you decide not to post that output.

Feel free to ask if you've any doubts :-)

---

### Post by jonathantalisman on 2011-02-18
Thanks sikander3786 & YesWeCan,
of course you are right I do have 3 disks - one is a Usb external HD [the 300Gb one].
I would rather not disconnect the Windows disk if possible.
I have looked at the ubuntu4beginners.blogspot.com post - which is great.
So if I am comfortable with doing a manual/advanced partition I should go with that, install Grub on the same disk [I think it's sdb as you'll see below ] , switch in the bios to boot in from the ubuntu HD and then [sudo] update-grub in order to add the windows entry to the grub menu ?
Any reccomendations regarding /home swap and / partitions ?
Below is the results from boot_info script . btw - all of this from the live CD.
Thanks Jonathan.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   469,968,895   469,966,848  83 Linux
/dev/sdb2         469,970,942   488,396,799    18,425,858   5 Extended
/dev/sdb5         469,970,944   488,396,799    18,425,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FA8C24C38C247BEF                       ntfs       Local Disk                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        25d82dbc-58cd-40df-b247-8a59ecde995c   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        46daa6bd-dd14-4384-bac0-fc8e610c4767   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 

multi(0)disk(0)rdisk(0)partition()\Windows="Windows XP" /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=25d82dbc-58cd-40df-b247-8a59ecde995c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=25d82dbc-58cd-40df-b247-8a59ecde995c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25d82dbc-58cd-40df-b247-8a59ecde995c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=25d82dbc-58cd-40df-b247-8a59ecde995c ro single 
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
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 25d82dbc-58cd-40df-b247-8a59ecde995c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=25d82dbc-58cd-40df-b247-8a59ecde995c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=46daa6bd-dd14-4384-bac0-fc8e610c4767 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


 118.2GB: boot/grub/core.img
 137.8GB: boot/grub/grub.cfg
   1.6GB: boot/initrd.img-2.6.35-22-generic
   1.7GB: boot/initrd.img-2.6.35-25-generic
 118.2GB: boot/vmlinuz-2.6.35-22-generic
 118.2GB: boot/vmlinuz-2.6.35-25-generic
   1.7GB: initrd.img
   1.6GB: initrd.img.old
 118.2GB: vmlinuz
 118.2GB: vmlinuz.old
```

---

### Post by YesWeCan on 2011-02-18
I see what you did now. You installed 10.10 to sdb and it put the grub MBR on sda. You then reinstalled the Windows MBR on sda. So now you cannot boot sdb.

What you are proposing seems good to me. I don't think you have to do manual partitioning though. I think you can do automatic but on the partitioning window I think there is an "advanced" button you can click and it then gives you a choice of where the grub MBR is put.

Or, if someone else can instruct you, you don't need to reinstall 10.10, instead you can use the live CD to boot sdb. Once running 10.10 on sdb you can do a grub-install /dev/sdb.

---

### Post by sikander3786 on 2011-02-18
Yes you just need to install the Grub loader and not the whole OS. Follow these commands from a Live CD.

```
sudo mount /dev/sdb1 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sd[COLOR="Red"]b[/COLOR]
```

Note, for the second one it is just sdb without an integer.

Then reboot, choose your Ubuntu HDD as the first boot device and run this command from inside your Ubuntu install.

```
sudo update-grub
```

If you want to re-install the whole Operating System, let us know so we can guide you there.

---

### Post by YesWeCan on 2011-02-18
That's nice sikander. Simpler than I thought.

---

### Post by oldfred on 2011-02-18
You also asked for some advice on partitions. Each of us have different ideas and none is wrong. Even my own "best" partitioning scheme changes every couple of years. More data, different desires (test other systems) or other changes. I like to keep system partitions small (slight performance improvement) & keep data separate (easier to backup).

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

While you have already done it, this site has lots of info so you can understand what is going on.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by jonathantalisman on 2011-02-21
Thank you all for your assistance ! Much appreciated.
I ended up re-installing- I wanted to set a different partition for my /home.
I guess my mistake in the previous install was to set grub in the first disk [sda] ... you learn something new every day.
Grub2 identified my windows with no problem.
I then found  [grub-customizer]("https://launchpad.net/~danielrichter2007") by Daniel Richter and used that.
Many thanks again. Jonathan.

---

