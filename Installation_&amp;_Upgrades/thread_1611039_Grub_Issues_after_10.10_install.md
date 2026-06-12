---
title: "Grub Issues after 10.10 install"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by reidthesteed on 2010-11-01
Firstly, I am running a dual boot system with windows 7 and Ubuntu.  Both have run smoothly on my machine (Core 2 quad core on Gigabyte board)

I recently upgraded to 10.10 from 10.04 via the update manager within 10.04.  Following the upgrade the initial boot failed at the login screen ( i simply got the purple colored screen with a white box in the center of it).  

Instead of trying to figure out what went wrong, I simply re-installed 10.10 from live CD on top of the upgraded Ubuntu that was failing at the login screen.

The live CD install seemed to fix everything for the most part ( I did notice some quickly flashing text right before the login screen.  I think it was an error message but it was too fast to read)

My problem now is that I am trying to remove some of my old kernels from the Grub2 boot screen and I cant.  I have read many posts on how to remove the old kernels, but my system is proving to be difficult.

The old kernels definitely show during boot, but whenever I go into Synaptic they are not there.  I have downloaded Ubuntu Tweak, and they do not show in it either.
I have read the information at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and it doesn't seem to help my problem.

I went to [http://www.fixthecode.com/remove-hug...sts-in-ubuntu/]("http://www.fixthecode.com/remove-huge-kernel-lists-in-ubuntu/") and thought this would fix my problem but I keep getting an error:
 "awk: 1: unexpected character 0xe2" 
when i try to run:
[FONT=Arial]"[/FONT][B][I][FONT=Arial]dpkg -l | grep ^ii | grep 2.6.3x-xx | awk -F’ ‘ ‘{ print $2 }’[/FONT]

[/I][/B] I am running kernel 2.6.35-22
The kernels i want to remove are 2.6.32-23 and 2.6.32-24.

I have considered just reformatting and trying a completely clean install but I would really like to learn whats going on here.   Please let me know if I need to post any more info.
Thanks in advance.  I appreciate your time.

---

### Post by oldfred on 2010-11-01
Welcome to the forums.

If the kernels are not showing are they because when you reinstalled, you installed to another partition and they really are elsewhere?

To see what is where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by kansasnoob on 2010-11-01
Have you tried simply running:

```
sudo update-grub
```

I'd be interested to see the output of that :)

---

### Post by reidthesteed on 2010-11-01
Thank you very much for your replies.

Here are the results from the boot_info_script:

     ```
           Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   819,202,544   614,405,925   7 HPFS/NTFS
/dev/sda3         819,204,094 1,250,263,039   431,058,946   5 Extended
/dev/sda5         819,204,096   834,828,287    15,624,192  82 Linux swap / Solaris
/dev/sda6         834,830,336   864,124,927    29,294,592  83 Linux
/dev/sda7         864,126,976 1,250,263,039   386,136,064  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        903878E33878CA2C                       ntfs                                     
/dev/sda2        94C0623CC06224A8                       ntfs       New Volume                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        f36ce3bc-a72d-44af-adfb-2a240b9634f9   swap                                     
/dev/sda6        81a95620-3363-40eb-a224-28572b219f57   ext4                                     
/dev/sda7        8516d903-77a2-4006-969b-74dc64f3943e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="10"
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro  splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	echo	'Loading Linux 2.6.32-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=81a95620-3363-40eb-a224-28572b219f57 ro single  splash quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 81a95620-3363-40eb-a224-28572b219f57
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 903878e33878ca2c
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=81a95620-3363-40eb-a224-28572b219f57 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f36ce3bc-a72d-44af-adfb-2a240b9634f9 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 439.0GB: boot/grub/core.img
 434.3GB: boot/grub/grub.cfg
 438.9GB: boot/initrd.img-2.6.32-23-generic-pae
 439.1GB: boot/initrd.img-2.6.32-24-generic-pae
 432.1GB: boot/initrd.img-2.6.32-25-generic-pae
 429.0GB: boot/initrd.img-2.6.35-22-generic-pae
 438.8GB: boot/vmlinuz-2.6.32-23-generic-pae
 439.0GB: boot/vmlinuz-2.6.32-24-generic-pae
 438.9GB: boot/vmlinuz-2.6.32-25-generic-pae
 439.1GB: boot/vmlinuz-2.6.35-22-generic-pae
 429.0GB: initrd.img
 439.1GB: vmlinuz
```

Here is the result from sudo update-grub:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-22-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```

Thanks again.

---

### Post by oldfred on 2010-11-01
It shows your files here:

 438.9GB: boot/initrd.img-2.6.32-23-generic-pae
 439.1GB: boot/initrd.img-2.6.32-24-generic-pae
 432.1GB: boot/initrd.img-2.6.32-25-generic-pae
 429.0GB: boot/initrd.img-2.6.35-22-generic-pae
 438.8GB: boot/vmlinuz-2.6.32-23-generic-pae
 439.0GB: boot/vmlinuz-2.6.32-24-generic-pae
 438.9GB: boot/vmlinuz-2.6.32-25-generic-pae
 439.1GB: boot/vmlinuz-2.6.35-22-generic-pae

If these do not work:
HOWTO: Remove Older Kernels via GUI
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
Command line:
[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

Then just drill down to /boot and remove the 2.6.32-** kernels & initrds, just be sure not to delete your current 2.6.35 versions.
Then rerun: 
sudo update-grub

---

### Post by reidthesteed on 2010-11-01
Thanks Oldfred,

Okay, so in my case none of the old kernels show in the Synaptic Package Manager nor in the Ubuntu Tweak program.  So the only thing I need to do is delete the 2.6.32-** kernels & initrds files in the boot folder and then run sudo update-grub?

If this is correct, is there a way to explain why the kernel files still exist but they arent actually installed on my system?

Thank you so much. :)

---

### Post by oldfred on 2010-11-01
I do not know, I think I remember one or two others with similar issues. 

Somehow the update thinks it deleted them, so its not in the history. Or the new install rebuilds everything, but does not delete kernels like it does with other apps and only builds a history of all the newly installed software.

---

### Post by reidthesteed on 2010-11-02
Okay,

So I just deleted all the uneccessary kernel files in the boot folder and then ran sudo update-grub.

It seems to have accomplished what I wanted.  Thank you for your help :)

---

