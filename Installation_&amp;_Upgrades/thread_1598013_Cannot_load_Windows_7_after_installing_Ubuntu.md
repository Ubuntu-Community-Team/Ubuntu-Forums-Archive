---
title: "Cannot load Windows 7 after installing Ubuntu"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by error691 on 2010-10-16
I have Windows 7 on SSD and have installed Ubuntu on a separate HDD.
When the PC boots, I get the boot manager menu, if I choose Windows 7 it fails with error "no such device or partition".

I can mount the SSD and see all the Windows files still there, I think that the boot manager just needs to be pointed in the right direction but not sure how.
Please help!

---

### Post by garvinrick4 on 2010-10-16
Download this script to desktop and then open a terminal and copy and paste code.
Will put a text file on desktop copy and paste whole thing to this thread. Highlight the whole
text file and hit the # sign in upper right side and will make easy to read. Make sure
you download script to DESKTOP. Takes about 10 seconds.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
 ```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by error691 on 2010-10-16
Done.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   117,227,519   117,020,672   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048         4,095         2,048 Bios Boot Partition
/dev/sdb2           4,096 3,887,382,527 3,887,378,432 Linux or Data
/dev/sdb3   3,887,382,528 3,907,028,991    19,646,464 Linux Swap

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3A38546938542663                       ntfs       System Reserved               
/dev/sda2        4E345FD7345FC11F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb2        0642d92c-f42d-4a83-b47d-af92043ea3fc   ext4                                     
/dev/sdb3        1bbe8797-5ac7-4902-af64-85f5e5f7a840   swap                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


=========================== sdb2/boot/grub/menu.lst: ===========================

title windows 7 beta (Loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0642d92c-f42d-4a83-b47d-af92043ea3fc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=0642d92c-f42d-4a83-b47d-af92043ea3fc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0642d92c-f42d-4a83-b47d-af92043ea3fc ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=0642d92c-f42d-4a83-b47d-af92043ea3fc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 0642d92c-f42d-4a83-b47d-af92043ea3fc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 3a38546938542663
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=0642d92c-f42d-4a83-b47d-af92043ea3fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=1bbe8797-5ac7-4902-af64-85f5e5f7a840 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


1237.0GB: boot/grub/core.img
 281.4GB: boot/grub/grub.cfg
 474.7GB: boot/grub/menu.lst
1237.1GB: boot/initrd.img-2.6.32-24-generic
1237.1GB: boot/initrd.img-2.6.32-25-generic
1237.1GB: boot/vmlinuz-2.6.32-24-generic
1237.0GB: boot/vmlinuz-2.6.32-25-generic
1237.1GB: initrd.img
1237.1GB: initrd.img.old
1237.0GB: vmlinuz
1237.1GB: vmlinuz.old

---

### Post by error691 on 2010-10-16
I also tried:

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

but I'm not sure that /dev/sda1 is correct, or how to change these things to test...

---

### Post by garvinrick4 on 2010-10-16
```
Put in live Cd (ubuntu install cd and choose try ubuntu)
when it boots up open a terminal Applications/Accessories/terminal
and copy and paste these:
[CODE]sudo mkdir /media/boot
```
```
sudo mkdir /media/root
```
```
sudo mount /dev/sdb1 /media/boot
```
```
sudo mount /dev/sdb2 /media/root
```
```
sudo grub-install --recheck --root-directory=/media/root /dev/sdb
```
```
sudo umount /media/boot
```
```
sudo umount /media/root
```
Now restart and take out cd boot into Ubuntu and
```
sudo update-grub
```
Can now boot into Ubuntu install and Windows from sdb install.

Need Windows grub installed:
Vista and 7 fix boot 
How to restore the Windows install grub / Vista or 7 bootloader To restore the Windows install grub bootloader, you must first boot off your Windows install grub Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows install grub Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 
```
 bootrec.exe /fixboot
``` 
 ```
bootrec.exe /fixmbr
``` 
and click "Restart."
If your sdb is a external USB drive unplug to be safe when install windows grub.
You can now use your BIOS to boot which ever drive you want. In sdb you can choose from either Ubuntu or Windows. In sda Windows will boot. If you have not learned to set you BIOS to boot in a particular order do so now. It can be set to boot and you can also select which one to boot from. usually from F10 or F2 at boot. Mine is HP and I select esc and the F9 to select which drive at boot. If you do not have Windows dvd let me know. 
[/CODE]

---

### Post by error691 on 2010-10-16
Hmm, I have done more troubleshooting:

Disk1=60Gb Windows
Disk2=2Tb Ubuntu

Tried changing BIOSS to boot from Disk2, get the Grub boot loader screen saying it is loading the OS and just hangs there, need to ctrl-alt-del to restart.

If I change BIOSS back to boot from Disk1, I can get into Ubuntu fine but cannot load Windows...

It seems I have a boot loader on each HDD, and when I change settings I think it is changing the wrong one somehow... =(

---

### Post by garvinrick4 on 2010-10-16
> **error691 said:**
> I also tried:

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

but I'm not sure that /dev/sda1 is correct, or how to change these things to test...It will say sda1 even though it is in sda2 because you have a boot partition.

---

### Post by garvinrick4 on 2010-10-16
Some pertinent sites.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

---

### Post by efflandt on 2010-10-16
Just curious where the legacy grub menu.lst came from (not used by grub2) and why that says "Windows 7 beta".  Do you have a regular Win7 version now, or possibly an expired beta version?  Other than that, everything looks correct to me.

---

### Post by error691 on 2010-10-16
I copied and pasted that config from somewhere which is why it says beta.
I think I had grub1 then I upgraded to grub2 to try and get that working.
Now I am at a loss, I need the Windows installation to work alongside Ubuntu, I tried reinstalling Ubuntu with no luck, and I can't reinstall Windows without a lot of pain.

This is really frustrating!! Is there some other boot loader apart from Grub as it doesn't seem to recognise the Windows 7 partitions or something?

---

### Post by error691 on 2010-10-16
I just noticed that I did not enter all the commands in properly, now I have and get the following error, maybe a clue?

sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

error: must specify the filesystem type


So I checked the man pages and tried that command with '-t' option and every filesystem type possible, but nothing works.

---

### Post by srs5694 on 2010-10-16
GRUB 2 has problems with mixed MBR-and-GPT systems. To fix this, add the following line to /etc/default/grub file and then type "sudo update-grub":

GRUB_PRELOAD_MODULES="part_msdos"

---

### Post by Irony on 2010-10-16
Perhaps I am missing something here but simply boot into ubuntu and do;

```
sudo grub-install /dev/sdb
sudo update-grub
```

Then reboot but go into the BIOS and make sure that the first disk booted is sdb.

Check you can boot into windows and then check you can boot into ubuntu.

---

### Post by error691 on 2010-10-16
Bugger, I just ran the Windows Cd so I could get bootrec.exe to reinstate the Winwdows boot loader.
Now I can't get back into Ubuntu at all, just gives me a 'grub>' prompt.

Can I still add that configuration by loading Ubuntu from CD or by grub menu?

---

### Post by srs5694 on 2010-10-16
Try using [Super GRUB Disk](http://www.supergrubdisk.org/) to get booted, then re-install GRUB ("sudo grub-install /dev/sda").

---

### Post by Irony on 2010-10-16
> **error691 said:**
> Bugger
Using your ubuntu cd;

```
sudo mount /dev/sdb2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo grub-install /dev/sdb
```

then;

```
sudo update-grub
```

Make sure to change BIOS to boot from sdb.

---

### Post by godwinnishanth on 2010-10-16
i got the same problem .. i repaired my win 7 with the win7 cd

---

### Post by garvinrick4 on 2010-10-16
Grub2 does not work nicely with grub legacy, If you copy and pasted anything get rid of it.
 Right now you can boot into Windows on sda, you replaced its bootloader. Linux on sdb has a boot partition in sdb1 so it has
to be mounted when you install grub2 to mbr of sdb.
Once you install grub2 to sdb you will be able to boot both Ubuntu and Windows on sdb booting first in order. If you boot sda Windows first in Bios order only Windows will boot. No linux on sda to use grub2.
You can make also choose on every boot which to boot from, CD, HDD, USB along with permanent settings. 
I gave you the instructions to install grub2 to sdb earlier with Live CD. Give that a try and
it is a little long because Boot partition needs a directory and to be mounted along with ubuntu partition and then install grub in sdb looking in sdb2 for grub. It will then be in sdb's mbr where it should be. The grub legacy is the only thing that could interfere with this
process from not working. When you boot into Ubuntu make sure you.
```
 
sudo update-grub

```to probe for Other operating systems to put in grub config and menu.
If it does not work then it has to do with the entries for grub legacy interfering and we can look there.
Grub2 and Grub legacy info from Ubuntu site.
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

---

### Post by error691 on 2010-10-19
Thanks guys. ^_^

I can get Windows 7 and Ubuntu working by doing this:
-Boot from SSD on channel 0, I get Windows boot menu and can run Windows 7 but not Ubuntu (get Grub prompt).
-Boot from HDD on channel 1, I get Grub boot menu and I can run Ubuntu but not Windows (partition not found).


Not sure if there is a more elegant solution, I tried reinstalling Ubuntu from scratch but get the same results. Maybe an issue with the way Windows 7 partitions itself or how my SSD and HDD are setup?

---

### Post by error691 on 2010-10-19
Oh yeah. this was a lifesaver: GRUB_PRELOAD_MODULES="part_msdos".
Thank you!!

Now I have two boot menus but I can load both Windows and Ubuntu. =)

---

