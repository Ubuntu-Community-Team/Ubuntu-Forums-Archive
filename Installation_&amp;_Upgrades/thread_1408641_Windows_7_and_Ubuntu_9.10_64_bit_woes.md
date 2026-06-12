---
title: "Windows 7 and Ubuntu 9.10 64 bit woes"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Biscayne on 2010-02-16
I have a machine which was running Windows 7 64bit, the installation was working fine.  I decided to install Ubuntu 9.10 64 bit on a separate hard drive.  Now, Ubuntu works great, but I try to boot Windows through GRUB (2, BTW) I get the following error:

error: No Such Device 3624fcb624fc7a67

Tried running grub-update, no avail.  Also tried running a repair disk with my Windows 7 install disk-also no luck.

EDIT: Also, if it helps, I can see both the System Reserved and full Windows partitions in Ubuntu.

Any ideas?

---

### Post by darkod on 2010-02-16
Boot the computer and move on the windows entry in the menu but DON'T hit Enter. Hit 'e' instead. It will show you the lines with the commands to boot windows. You can move the cursor with the arrows. Delete the line starting with search....
Press Ctrl + X to boot windows.
If it worked, look here at simple instructions how to make the fix permanent:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

ONLY IF IT WORKED!!!

---

### Post by Biscayne on 2010-02-16
New Problem.

Did as suggested above, and a new error message presented itself

Error - No Such Partition

Again, can see the drives in Ubuntu, and grub-update does nothing

Am I screwed?

---

### Post by darkod on 2010-02-17
You're not, but more info is needed. Download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about the boot process. Post the content of the file here and wrap it in CODE tags for easier reading (with the text selected hit the # button in the toolbar above when creating a post).

---

### Post by Biscayne on 2010-02-17
Not sure what the relevant data is, so here is the whole results.txt file.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=6e269511-1809-4e64-85f8-2b8db0b680e2)/boot/grub.
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

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe188764a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34       262,177       262,144 Microsoft Windows
/dev/sdb2         264,192   758,024,191   757,760,000 Linux or Data
/dev/sdb3     758,025,088   976,773,134   218,748,047 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3624FCB624FC7A67                       ntfs       System Reserved               
/dev/sda2        A87A00E17A00AE5E                       ntfs                                     
/dev/sdb2        7A1042291041ECA7                       ntfs                                     
/dev/sdb3        6e269511-1809-4e64-85f8-2b8db0b680e2   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,3)
search --no-floppy --fs-uuid --set 6e269511-1809-4e64-85f8-2b8db0b680e2
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 6e269511-1809-4e64-85f8-2b8db0b680e2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e269511-1809-4e64-85f8-2b8db0b680e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,3)
	search --no-floppy --fs-uuid --set 6e269511-1809-4e64-85f8-2b8db0b680e2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6e269511-1809-4e64-85f8-2b8db0b680e2 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 3624fcb624fc7a67
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=6e269511-1809-4e64-85f8-2b8db0b680e2 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 391.2GB: boot/grub/core.img
 388.8GB: boot/grub/grub.cfg
 388.7GB: boot/initrd.img-2.6.31-14-generic
 388.6GB: boot/vmlinuz-2.6.31-14-generic
 388.7GB: initrd.img
 388.6GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

EDIT: I realized I had a bunch of external hard drives plugged in, which made the file a mess, I removed the drives, and re-ran the program

Thanks a lot for your help!

---

### Post by darkod on 2010-02-17
OK, you see this:

/dev/sdb1                   1   976,773,167   976,773,167  ee [COLOR=Red]GPT[/COLOR]

New large hdds started using GPT partition table instead of "old" type DOS. This can confuse grub.

Try this. Because you can't boot the hdd ubuntu, boot the live desktop and to reach your hdd ubuntu do:

sudo mount /dev/sdb3 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
gedit /etc/default/grub

At the end of the file add the line:
GRUB_PRELOAD_MODULES="part_msdos"
Save and close the file.
In the terminal continue running:

update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
(if terminal is still open again execute) exit

Reboot and see if it helped. You also have the bootloaders on opposite drives but it's not a big issue right now, we'll sort it once you can boot ubuntu, hopefully after these commands.

---

### Post by meierfra. on 2010-02-17
> Because you can't boot the hdd ubuntu,

???  The OP is able to boot into Ubuntu. In fact, according to the "mount" data on RESULTS.txt, the boot info script was run from Ubuntu:

> /dev/sdb3        /                        ext4       (rw,errors=remount-ro)


So  just do this part of darkrod's instruction:


```
gksudo gedit /etc/default/grub

```
At the end of the file add the line: 

GRUB_PRELOAD_MODULES="part_msdos"

Save and close the file.
In the terminal continue running:

```
update-grub
```

---

### Post by darkod on 2010-02-17
Sorry, my bad. The first post says the error is there only when trying to boot windows. And it makes the commands much simple. :oops:

That's what happens when reading too many threads. :(

---

### Post by Biscayne on 2010-02-17
That worked!  Thanks a lot

Now, on a somewhat unrelated note, how do I change the default OS in the new GRUB?  I used to know how in the old GRUB, but things have apparently changed since 8.04.

Again, thanks a lot for the help!

---

### Post by darkod on 2010-02-17
> **Biscayne said:**
> That worked!  Thanks a lot

Now, on a somewhat unrelated note, how do I change the default OS in the new GRUB?  I used to know how in the old GRUB, but things have apparently changed since 8.04.

Again, thanks a lot for the help!

You can install a package called startupmanager which allows you to easy change default OS and timeout.
sudo apt-get install startupmanager

I don't use it, and not sure how well it works with the new grub2.

Personally I prefer the editing of the config files. Write down what your windows entry is called in the grub menu, exactly.
Then open
sudo gedit /etc/default/grub

and in the line GRUB_DEFAULT="exact text of your windows entry"

Save and close. Run
sudo update-grub

That should do it and will stay default even if new ubuntu kernels are added with updates. You could also use GRUB_DEFAULT=n but you have to adjust after every new kernel because you probably know it relates to the position of the windows entry. Your choice. :)

---

