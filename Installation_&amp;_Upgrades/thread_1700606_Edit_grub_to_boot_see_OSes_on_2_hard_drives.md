---
title: "Edit grub to boot see OSes on 2 hard drives?"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by jondiced on 2011-03-05
So here is my issue:

I have normally run Ubuntu but recently installed Fedora on my second hard drive. Not knowing what to do with the boot sector, I just did a full installation on the drive. In order to switch operating systems, I have to enter the BIOS and change the boot order of the hard drives. How can I set up grub on the first hard drive (with Ubuntu) to allow me to choose which OS to boot?

Thanks.

---

### Post by YesWeCan on 2011-03-05
Just boot Ubuntu and run 'sudo update-grub'.
This scans all your drives and adds OSes to the grub boot menu, which will now appear at boot (it doesn't appear at boot if there is only 1 OS listed - which is dumb).

---

### Post by jondiced on 2011-03-05
> **YesWeCan said:**
> Just boot Ubuntu and run 'sudo update-grub'.
This scans all your drives and adds OSes to the grub boot menu, which will now appear at boot (it doesn't appear at boot if there is only 1 OS listed - which is dumb).


Thanks very much. Unfortunately, this didn't work; at boot, Grub still does not see Fedora. Maybe the drive is not being mounted in time? Fedora created a 500 MB ext4 boot partition (/boot) on sdb1 and used the rest of the drive for  an LVM2 physical volume at sdb2. In Ubuntu after login I only see the boot partition, not the LVM2.

What information would be most helpful?

Edit: 
1) update-grub only looks in /boot on sda. Is there a way to tell it to look in /boot on sdb as well?
2) Here is the output for update-grub. The kernels listed all come from my Ubuntu installation.
```
$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-29-generic
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.31-21-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

---

### Post by oldfred on 2011-03-05
You seem to have a lot of old kernels. It may be time to houseclean.
It also says updating menu.lst. You must be using old grub legacy. Grub legacy was not good at finding other installs. You will probably have to manually add your own entry to menu.lst.

This was my old entry to chainload to the MBR, I find which ever drive I boot it is hd0, then drives are in order. If you boot sda then sdb will be hd1.

title       Ubuntu 9.04 Jaunty 32 bit @ sdb
root        (hd1)
chainloader +1

The easiest way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

See grubcleanup for removing old kernels
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by YesWeCan on 2011-03-05
This tells you how to upgrade to Grub2: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2011-03-05
+1 on YesWeCan's suggest to upgrade to grub2.

Grub2 is a bit more complex but handles multiOS's a lot better/simpler. Old grub legacy has not been maintained for years.

---

### Post by jondiced on 2011-03-05
Thanks for all the suggestions. I upgraded to Grub2 and ran update-grub, but the output was as before:

```
--> sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

I added an entry to /etc/grub.d/40_custom to chainload the grub installed on sdb:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 14" {
    set root=(hd1,0)
    chainloader +1
}

```
(note, also tried with root=(hd1) and root=(hd1,1)

ran update-grub again and checked that it was added to grub.cfg (scroll to bottom):
```

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
search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
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
search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=8
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c60c0f69-04e5-472d-91b8-f06778ca570f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c60c0f69-04e5-472d-91b8-f06778ca570f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 14" {
    set root=(hd1,0)
    chainloader +1
}
### END /etc/grub.d/40_custom ###

```

and ran update-grub again for good measure. Still I was not able to boot from sdb. 

Here is a screenshot of the information from Disk Utility, on the off chance that it helps. (sorry for the size, can't find how to modify the img tages) 
[IMG]http://i.imgur.com/VgDhg.png[/IMG]


Any more suggestions?

Lastly, I'm pretty tired and getting to the point where I could easily do something bad by mistake, so I may wait to continue this until tomorrow morning. I appreciate all the help and attention.

---

### Post by oldfred on 2011-03-05
In grub2 there is not partition 0. You can only chainload to a location with another boot loader. If hd1 did not work are you booting with more that 2 devices. Sometimes a USB key or other device may be inserted as a lower number device.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by YesWeCan on 2011-03-05
You really shouldn't need to mess about with chainloading. As I understand it, update-grub should find the fedora boot files and put an entry in grub.cfg automatically. I wonder if your os-prober is new enough or if your fedora /boot contains the right files.

---

### Post by jondiced on 2011-03-06
> **oldfred said:**
> In grub2 there is not partition 0. You can only chainload to a location with another boot loader. If hd1 did not work are you booting with more that 2 devices. Sometimes a USB key or other device may be inserted as a lower number device.

Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.


Alright, I'm not sure what happened but Grub2 started finding the Fedora entry I made by hand and gave me an option in the boot menu. I stopped getting an error message when I changed from root=(hd1,0) to root=(hd1). However, when I select Fedora, it just hangs with a cursor blinking in the upper left corner of a blank screen.

Here is the output of bootinfoscript:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 32636 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub in the file /mbr.bin looks at sector 1 of the 
                       same hard drive for the stage2 file, but no stage2 
                       files can be found at this location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sdb2: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   937,167,839   937,167,777  83 Linux
/dev/sda2         937,167,840   976,768,064    39,600,225   5 Extended
/dev/sda5         937,167,903   976,768,064    39,600,162  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     1,026,047     1,024,000  83 Linux
/dev/sdb2           1,026,048   976,773,119   975,747,072  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c60c0f69-04e5-472d-91b8-f06778ca570f   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        887de4aa-74b8-4a0e-a0eb-4b5d85649f37   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        639d96cd-6f0c-4a0b-9959-f3039b0ecf50   ext4                                     
/dev/sdb2        qN4azz-Tzyz-adBf-62jr-3Tnc-zw4H-qPiOEA LVM2_member                               
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb1        /media/639d96cd-6f0c-4a0b-9959-f3039b0ecf50 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
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
search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=8
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c60c0f69-04e5-472d-91b8-f06778ca570f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=c60c0f69-04e5-472d-91b8-f06778ca570f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set c60c0f69-04e5-472d-91b8-f06778ca570f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Fedora 14" {
    set root=(hd1)
    chainloader +1
}
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c60c0f69-04e5-472d-91b8-f06778ca570f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=887de4aa-74b8-4a0e-a0eb-4b5d85649f37 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.1GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   3.0GB: boot/initrd.img-2.6.32-29-generic
 222.1GB: boot/vmlinuz-2.6.32-29-generic
   3.0GB: initrd.img
 222.1GB: vmlinuz

============================= sdb1/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_mal-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sdb
default=0
timeout=0
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
	root (hd0,0)
	kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/vg_mal-lv_root rd_LVM_LV=vg_mal/lv_root rd_LVM_LV=vg_mal/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.35.6-45.fc14.i686.img

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initramfs-2.6.35.6-45.fc14.i686.img
    .0GB: initrd-plymouth.img
    .0GB: vmlinuz-2.6.35.6-45.fc14.i686

```

It looks like Fedora is running Grub 0.97. Perhaps I should upgrade that to Grub 2 as well? I'll see what Fedora has to say about it. 

Thanks for all your patience everyone.

---

### Post by carvish on 2011-03-06
after updating to grub2 you "may" still have to install the os prober.

check in your terminal first, if not,

sudo aptget install-os-prober

I dualboot win7 and ubuntu10.10, grub2 didn't see the 2 os's until i installed the prober

don't  forget to update grub2 afterwords.

for customization go into your software center and install " grub customizer" I use this program and it's pretty slick

enjoy

---

### Post by jondiced on 2011-03-06
> **carvish said:**
> after updating to grub2 you "may" still have to install the os prober.


Does it really need to be installed on both systems?

As for grub customizer, which repository is it in? I don't see it in my software center or the package manager.

---

### Post by carvish on 2011-03-06
> **jondiced said:**
> Does it really need to be installed on both systems?

As for grub customizer, which repository is it in? I don't see it in my software center or the package manager.

[http://myubuntu.info/grub-customizer-2-0-can-change-the-default-grub2-boot-entry-menu-colors-background-image-and-lots-more/](http://myubuntu.info/grub-customizer-2-0-can-change-the-default-grub2-boot-entry-menu-colors-background-image-and-lots-more/)

check  there for installation

enjoy

---

### Post by YesWeCan on 2011-03-06
> **jondiced said:**
> Does it really need to be installed on both systems?

As for grub customizer, which repository is it in? I don't see it in my software center or the package manager.
No. If you use Ubuntu's Grub2 to directly boot (not chainload) fedora then fedora's Grub is not used at all.
The problem, I imagine, is that your Ubuntu (which Ubuntu are you using?) has a version of os-prober that is not able to recognize the fedora boot files. So you need to make sure your os-prober is up to date.

There are several other methods, see "Custom Boot Entries" here: [http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

### Post by YesWeCan on 2011-03-06
> **jondiced said:**
> Alright, I'm not sure what happened but Grub2 started finding the Fedora entry I made by hand and gave me an option in the boot menu. I stopped getting an error message when I changed from root=(hd1,0) to root=(hd1). However, when I select Fedora, it just hangs with a cursor blinking in the upper left corner of a blank screen.
My guess is that your attempt to chainload is not working because your fedora Grub install is not working:
```
=> Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 32636 [COLOR="Red"]on 
    boot drive #1[/COLOR] for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /grub/grub.conf.

```
My guess is that when you boot your Ubuntu drive, the bios sets that drive as "boot drive #1". When you chainload to fedora's MBR its Grub erroneously looks on the Ubuntu drive for its files. There is a way to resolve this in your Grub2 so that the fedora drive looks like boot drive #1 - you'll have to look this up.

Grub2 is smarter than old grub. So if you were to update your fedora drive to use Grub2 then I imagine the chainload would just work as you have it now (assuming Grub2 and fedora are compatible - you have to wonder why it is being distributed with the old Grub at all). I recommend disconnecting the Ubuntu drive while you do this to guarantee nothing is accidentally referenced to it.

---

### Post by oldfred on 2011-03-06
When you use BIOS to choose which drive to boot Fedora does it work ok?

Fedora thinks it is on hd0. Both the MBR as mentioned by YesWeCan and its grub file say hd0. If booting sda and then chainbooting that drive becomes hd1, which then confuses its loading. Not sure if adding a mapdevice command would then make it work or not.

If you installed 10.04, it should have the osprober and find the Fedora. Another way is to copy the Fedora boot from grub legacy and convert it to grub2  format just as the osprober would do it.

---

