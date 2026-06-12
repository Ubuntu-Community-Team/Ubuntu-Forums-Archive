---
title: "Can't reinstall GRUB after installing Windows 7"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by spoons on 2011-02-06
I have Ubuntu 10.10 and Windows 7. I've tried to reinstall GRUB using a Ubuntu 10.10 LiveCD. None of the guides I have found online work, it bombs out when it comes to trying to mount /dev in some way or another. I'll be able to post more details later. Does anyone have a foolproof way of fixing this?

Thanks.

---

### Post by oldfred on 2011-02-06
How does it bomb out. (off topic can we even use that word anymore?)

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by spoons on 2011-02-06
I tried using this guide:
[http://www.elfnet.org/2010/10/21/ubuntu-10-10-recover-grub-windows/](http://www.elfnet.org/2010/10/21/ubuntu-10-10-recover-grub-windows/)

But when I try and paste the commands into terminal when using my LiveCD the terminal lectures me on "Usage"

Here's the output of that script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   507,798,584   507,798,522   7 HPFS/NTFS
/dev/sda2         509,758,515   625,137,344   115,378,830   5 Extended
/dev/sda5         509,758,578   625,137,344   115,378,767  83 Linux
/dev/sda3         507,798,585   509,758,514     1,959,930  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,770,143   976,770,081   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        BE5CEC195CEBCA6B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3                                               swap                                     
/dev/sda5        d17cc72c-d0c7-4c4a-a539-b2c674fd5e56   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9E70C9EB70C9CA6B                       ntfs       SEAGATE                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-20-generic ...'
	linux	/boot/vmlinuz-2.6.32-20-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-19-generic ...'
	linux	/boot/vmlinuz-2.6.32-19-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-16-generic ...'
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	echo	'Loading Linux 2.6.32-14-generic ...'
	linux	/boot/vmlinuz-2.6.32-14-generic root=UUID=d17cc72c-d0c7-4c4a-a539-b2c674fd5e56 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set d17cc72c-d0c7-4c4a-a539-b2c674fd5e56
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 2242bd3042bd0995
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    errors=remount-ro 0       1
# /mediadrive was on /dev/sdb1 during installation
UUID=9E70C9EB70C9CA6B /mediadrive     ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=2242BD3042BD0995 /windows        ntfs    defaults,umask=007,gid=46 0       0
/dev/sda3       none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 289.9GB: boot/grub/core.img
 289.1GB: boot/grub/grub.cfg
 289.1GB: boot/initrd.img-2.6.32-14-generic
 289.1GB: boot/initrd.img-2.6.32-16-generic
 289.2GB: boot/initrd.img-2.6.32-19-generic
 289.1GB: boot/initrd.img-2.6.32-20-generic
 289.2GB: boot/initrd.img-2.6.32-21-generic
 311.2GB: boot/initrd.img-2.6.32-22-generic
 292.9GB: boot/initrd.img-2.6.32-23-generic
 289.9GB: boot/initrd.img-2.6.32-24-generic
 289.1GB: boot/vmlinuz-2.6.32-14-generic
 289.0GB: boot/vmlinuz-2.6.32-16-generic
 289.0GB: boot/vmlinuz-2.6.32-19-generic
 289.0GB: boot/vmlinuz-2.6.32-20-generic
 289.1GB: boot/vmlinuz-2.6.32-21-generic
 279.9GB: boot/vmlinuz-2.6.32-22-generic
 289.1GB: boot/vmlinuz-2.6.32-23-generic
 289.9GB: boot/vmlinuz-2.6.32-24-generic
 289.9GB: initrd.img
 292.9GB: initrd.img.old
 289.9GB: vmlinuz
 289.1GB: vmlinuz.old
```

---

### Post by Quackers on 2011-02-06
Can you explain what you mean by "the terminal lectures me on "Usage"" please?

---

### Post by kansasnoob on 2011-02-06
The **[COLOR="Red"]grldr[/COLOR]** here makes me wonder what's up:

> sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /**[COLOR="Red"]grldr[/COLOR]**


But just try to copy-n-paste these commands:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

That should work if the 320GB drive is set to boot first in BIOS. If it's not you may need to repeat that with "grub-install /dev/sdb" as the second command.

---

### Post by spoons on 2011-02-06
Kansasnoob, I get this error:

ubuntu@ubuntu:~$ grub-install /dev/sda
cp: cannot create regular file `/boot/grub/915resolution.mod': Permission denied

So I use sudo:

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by spoons on 2011-02-06
> **Quackers said:**
> Can you explain what you mean by "the terminal lectures me on "Usage"" please?

I get the usual "usage" information like I'm giving it bad parameters. But I was just following the guide.

---

### Post by Quackers on 2011-02-06
Thanks.
Have you tried kansasnoob's commands in post #5?

---

### Post by spoons on 2011-02-06
Above you'll see the grub-install command doesn't seem to be working.

Also, if I just carry on..

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I'm at a loss.

---

### Post by Quackers on 2011-02-06
If you are getting the ubuntu@ubuntu prompt in the terminal, you haven't chrooted into your installation - if you had, you would be getting the root@ubuntu terminal prompt. That is the problem.

---

### Post by spoons on 2011-02-06
Here's the output:

root@ubuntu:~# grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

It trips up here, I don't know why.

---

### Post by Quackers on 2011-02-06
See post #10

---

### Post by kansasnoob on 2011-02-06
> **spoons said:**
> Here's the output:

root@ubuntu:~# grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

It trips up here, I don't know why.

Reboot the Live CD as it appears that you're partly mounted, then copy-n-paste the commands I posted in post #5.

If anything fails we need to see the entire output of the terminal!

---

### Post by solitaire on 2011-02-06
There's a round about way to reinstall grub (it's actually more simple in my view)

Boot into Win7
Stick in the Ubuntu CD/USB and run WUBI to install Ubuntu in windows.
Run through the install and reboot when asked. (just give it the default values since you'll not actually be using it)

you'll now see the Win7 boot loader with 3 options
- Win7
- Wubi's install of Ubuntu
- and your original Ubuntu install
At this point you can either boot into win7 to finish the wubi install 
Or
Boot into your original Ubuntu install then go to Synaptic and reinstall GRUB

If you like you can then boot back into windows and remove Wubi's ubuntu

---

### Post by kansasnoob on 2011-02-06
> **solitaire said:**
> There's a round about way to reinstall grub (it's actually more simple in my view)

Boot into Win7
Stick in the Ubuntu CD/USB and run WUBI to install Ubuntu in windows.
Run through the install and reboot when asked. (just give it the default values since you'll not actually be using it)

you'll now see the Win7 boot loader with 3 options
- Win7
- Wubi's install of Ubuntu
- and your original Ubuntu install
At this point you can either boot into win7 to finish the wubi install 
Or
Boot into your original Ubuntu install then go to Synaptic and reinstall GRUB

If you like you can then boot back into windows and remove Wubi's ubuntu

And that is simpler how :confused:

---

### Post by solitaire on 2011-02-06
> **kansasnoob said:**
> And that is simpler how :confused:
It does away with all the problems the original poster is having with the commands.

---

### Post by spoons on 2011-02-06
> **kansasnoob said:**
> Reboot the Live CD as it appears that you're partly mounted, then copy-n-paste the commands I posted in post #5.

If anything fails we need to see the entire output of the terminal!

Thanks, everything's fixed now! :D ):P

---

### Post by kansasnoob on 2011-02-06
> **solitaire said:**
> It does away with all the problems the original poster is having with the commands.

I'll not bother getting into detail but that can actually create problems that would require considerably more time to remedy.

---

### Post by wilee-nilee on 2011-02-06
> **kansasnoob said:**
> I'll not bother getting into detail but that can actually create problems that would require considerably more time to remedy.

That's for sure, :lolflag:

---

### Post by Quackers on 2011-02-06
I'm glad you got things sorted out :-)

---

### Post by a. Ramzy on 2011-07-12
> **spoons said:**
> Thanks, everything's fixed now! :D ):P
@[spoons]("http://ubuntuforums.org/member.php?u=421366") could you please tell me how you did sort out things cuz, I have the same problems since I did install windows again and yet I can't solve it! : (

---

### Post by YannBuntu on 2011-07-13
> **kansasnoob said:**
> just try to copy-n-paste these commands:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
grub-install /dev/sda
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

That should work if the 320GB drive is set to boot first in BIOS. If it's not you may need to repeat that with "grub-install /dev/sdb" as the second command.

Hi
FYI there is now a little tool to do this (and more) in 1 click : [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") :guitar:

---

