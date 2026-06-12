---
title: "Unable to Load windows after ubuntu install - grub problem"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Chrishannah8386 on 2011-03-13
Hello


I have just installed Ubuntu, now  when logging into my laptop i am able to sucsessfully load ubuntu but i  am unable to load the original OS (windows 7).


The grub 1.9 bootloader gives me the option


"Windows 7 (loader) (on /dev/sda2)"


when selecting this option it goes to a black screen with a - in the top left of the screen then the grub screen re-appears


i have ran the boot_info_script.


```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 952725680 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  





```I think I know what is going wrong the above info stated that windows 7 is on sda3 however the code in the grub menu says that it points to SDA2.

i have tried to edit the grub config file in the /boot/grub/grub.cfg directory to point to SDA3 and this had no effect

I am also concerned because there are no directories in the BOOT files/dirs: for windows 7 (Shown above) and i have seen other posts on this site that list boot directories 

i.e /bootmgr  /boot/bcd  /windows/system32/winload.exe

the code in the grub edit menu is
[
CODE]

menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7e7435407434fd09
    chainloader +1
}
[/CODE]

i have also ran the
```

sudo update-grub

```

this had no effect 

I have A Dell 1558 

so i'm thinking that if i can get it to point to the correct SDA and then get it too look in the right place for the boot file this will work

can anyone help as i cannot find out how to do this.


Thanks

---

### Post by Hippytaff on 2011-03-13
When you edit the grub.cfg file, I think you need to do sudo update-grub for it to take effect

---

### Post by kagerato on 2011-03-13
I don't know what the Grub module "part_msdos" does exactly, although it very probably has something to do with DOS-style partitions.  I haven't seen a case where it was necessary to explicitly load it using `insmod`, as in your example.  Also, I don't recall seeing something like (hd0,msdos2) specified as the root partition.  /dev/sda3 is represented as (hd0,3) normally.

Is there anything strange or otherwise notable about the partition scheme you're using?  If not, you should be able to get away with simply changing the (hd0,msdos2) to (hd0,3) and see what happens.

Oh, and one other important thing: when you run `update-grub`, it overwrites the contents of /boot/grub/grub.cfg with the result of a series of scripts in /etc/grub.d/  .  That would destroy any changes you made to grub.cfg earlier.  (Normally, you're supposed to modify either /etc/default/grub  or the scripts in the grub.d directory in order to apply your changes.)

If you want to bypass all that nonsense and modify grub.cfg directly (I do it myself sometimes), make sure _not_ to run update-grub .  Note that during certain package updates, it's possible for your configuration to get clobbered because some other update script or program saw it fit to run 'update-grub' on its own.  That's mainly why it's not recommended to modify it directly.

---

### Post by Hippytaff on 2011-03-13
> **kagerato said:**
> 
If you want to bypass all that nonsense and modify grub.cfg directly (I do it myself sometimes), make sure _not_ to run update-grub.

I got it the wrong way around :?

---

### Post by kansasnoob on 2011-03-13
That doesn't appear to be the full output of the Boot Info Script, but I can see two problems already:

> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    [B][COLOR="Red"]Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 952725680 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.[/COLOR][/B] No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD


And I rather assume that sda3 should have the "/windows/system32/winload.exe" but that's a wild guess without seeing the rest of the RESULTS.txt.

The first error is explained here (along with a testdisk method to fix it):

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If I'm also right about the missing "/windows/system32/winload.exe" files you'll need to use a Windows repair disc as described here:

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

NOTE: that includes a download location for a repair disc.

But without seeing the full output I could be missing something ;)

---

### Post by kansasnoob on 2011-03-13
If you prefer you can attach the full BIS RESULTS.txt by right-clicking the file, selecting compress, and then use the little paper-clip thingy at the top of this reply box to attach the tar.gz :)

I should look to be certain you don't also have additional problems.

---

### Post by Chrishannah8386 on 2011-03-13
Hey guys thanks for the replys, i'll be back online tomorrow working through any suggestions but i have the file you requested

i have emailed it to my windows pc so sorry if the text is all screwed

---

### Post by kansasnoob on 2011-03-14
Thanks, I'll look at this closer directly. I'm pasting it here so others can have a look:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 952725680 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325    36,944,324    36,864,000   7 HPFS/NTFS
/dev/sda3          36,944,325   600,422,348   563,478,024   7 HPFS/NTFS
/dev/sda4         600,422,398   976,771,071   376,348,674   f W95 Ext d (LBA)
/dev/sda5         922,951,680   976,771,071    53,819,392  83 Linux
/dev/sda6         600,422,400   909,776,895   309,354,496  83 Linux
/dev/sda7         909,778,944   922,949,631    13,170,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        7E7435407434FD09                       ntfs       RECOVERY                      
/dev/sda3        82B037B1B037AA95                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ad527b2c-d773-4baf-92f4-24d518d6dfe9   ext4                                     
/dev/sda6        e54b3939-d122-4a92-a965-7eab16dc7abb   ext4                                     
/dev/sda7        46868ffc-2042-462c-bbf2-4359667b7a79   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	echo	'Loading Linux 2.6.35-27-generic ...'
	linux	/boot/vmlinuz-2.6.35-27-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e7435407434fd09
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 487.7GB: boot/grub/core.img
 496.5GB: boot/grub/grub.cfg
 473.6GB: boot/initrd.img-2.6.35-22-generic
 496.7GB: boot/initrd.img-2.6.35-27-generic
 487.8GB: boot/vmlinuz-2.6.35-22-generic
 487.8GB: boot/vmlinuz-2.6.35-27-generic
 496.7GB: initrd.img
 473.6GB: initrd.img.old
 487.8GB: vmlinuz
 487.8GB: vmlinuz.old

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e54b3939-d122-4a92-a965-7eab16dc7abb ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=e54b3939-d122-4a92-a965-7eab16dc7abb ro single 
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
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set e54b3939-d122-4a92-a965-7eab16dc7abb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 7e7435407434fd09
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-27-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux /boot/vmlinuz-2.6.35-27-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro single
	initrd /boot/initrd.img-2.6.35-27-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set ad527b2c-d773-4baf-92f4-24d518d6dfe9
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=ad527b2c-d773-4baf-92f4-24d518d6dfe9 ro single
	initrd /boot/initrd.img-2.6.35-22-generic
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
UUID=e54b3939-d122-4a92-a965-7eab16dc7abb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=46868ffc-2042-462c-bbf2-4359667b7a79 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 440.7GB: boot/grub/core.img
 423.5GB: boot/grub/grub.cfg
 308.3GB: boot/initrd.img-2.6.35-22-generic
 440.6GB: boot/vmlinuz-2.6.35-22-generic
 308.3GB: initrd.img
 440.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  1b ba 72 04 49 7a 63 af  36 03 15 b6 58 2b 52 11  |..r.Izc.6...X+R.|
00000010  88 db 60 22 ec 07 a3 01  c6 53 f2 00 5f f9 7f 0e  |..`".....S.._...|
00000020  92 6b ac 86 fd 9e c5 d8  ce d9 c6 c6 1c 63 7c 42  |.k...........c|B|
00000030  42 11 04 d7 2a 4a 79 e6  82 a2 34 5c 89 42 63 11  |B...*Jy...4\.Bc.|
00000040  60 b0 64 00 10 c2 4e b9  26 b2 46 6a 0b 01 05 50  |`.d...N.&.Fj...P|
00000050  b1 a4 15 e4 08 8b b7 10  a3 b0 f0 06 71 d5 43 76  |............q.Cv|
00000060  c2 6a 10 5c d8 22 07 05  e0 10 20 53 ce 69 8c 0c  |.j.\.".... S.i..|
00000070  84 66 dc 33 71 f8 05 f6  ba d4 e9 33 08 d1 52 aa  |.f.3q......3..R.|
00000080  ec b8 87 73 3a 4a 71 07  7e 01 0e 3d 88 68 90 cd  |...s:Jq.~..=.h..|
00000090  e5 7e d0 e6 5c f9 66 26  8c 0c ab 7b ad 1d 74 15  |.~..\.f&...{..t.|
000000a0  10 05 b3 3b fe e6 39 15  9d 8d a0 6c e6 3b 16 37  |...;..9....l.;.7|
000000b0  03 ed 11 f7 21 40 23 e5  22 00 59 09 da 68 ba 01  |....!@#.".Y..h..|
000000c0  9f 82 ad 86 35 5e 5d ce  01 91 98 b3 ea 19 84 95  |....5^].........|
000000d0  0b e4 09 e0 87 08 43 d4  4c f8 72 0b 9b 95 42 d8  |......C.L.r...B.|
000000e0  39 8e 19 f8 12 d3 81 c1  c0 98 18 74 ef 27 87 b9  |9..........t.'..|
000000f0  00 29 71 40 f6 94 0d 62  fb 14 22 86 fd ea 43 38  |.)q@...b.."...C8|
00000100  92 e1 8b ee ba 07 73 03  b0 67 12 67 5c a2 71 0b  |......s..g.g\.q.|
00000110  d0 7b 0d 37 84 89 55 4f  9b 0d 8c e2 27 09 e9 98  |.{.7..UO....'...|
00000120  9c 22 3c 49 32 69 c4 80  bb ce 1c 37 86 8e d1 c4  |."<I2i.....7....|
00000130  9e 4e 9b 97 c5 cd 81 ba  9b 53 09 c5 50 10 d5 2a  |.N.......S..P..*|
00000140  e3 b8 aa c3 1d ca 47 70  96 2e 19 cd 60 3c 43 8e  |......Gp....`<C.|
00000150  aa b4 9a 70 ff f4 38 ab  e0 ce ba 6c 45 86 0e ab  |...p..8....lE...|
00000160  54 00 7e 12 b8 cc 64 e1  2f 8f 61 10 38 75 30 19  |T.~...d./.a.8u0.|
00000170  f1 82 00 be 15 10 81 82  0a 4d 30 2e 82 a3 ca 11  |.........M0.....|
00000180  18 bd ad ed 18 f2 92 d9  38 96 1e 85 13 9d 85 6c  |........8......l|
00000190  7f 27 10 45 63 a5 14 a6  23 38 b6 42 27 e2 29 bb  |.'.Ec...#8.B'.).|
000001a0  11 b2 17 1c 5b d6 55 a5  68 1e 54 43 48 53 37 10  |....[.U.h.TCHS7.|
000001b0  98 11 49 aa d4 d8 4b 4c  9c 40 f7 aa 48 6b 00 fe  |..I...KL.@..Hk..|
000001c0  ff ff 83 fe ff ff 02 68  39 13 00 38 35 03 00 fe  |.......h9..85...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 60 70 12 00 00  |...........`p...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Chrishannah8386 on 2011-03-14
I initially loaded ubuntu onto a 30gb drive but as this did not load i was advise that re-loading it and using the "Default settings" that this might solve my issue.
 
so i did this and i believe i now have 2 installs of ubuntu one of which i will remove when i get everything up and running.
 
i have some important family photos and such on my machine (sadly almost everything else is backed up) so i would like to avoid a re-install and wipe of the drives were possible. I would be willing to do this if i could get the data off the windows section of the drive, i will do some searches when i get home see if this is possible from ubuntu
 
thanks in advance

---

### Post by kansasnoob on 2011-03-14
Don't worry about the two Ubuntu's right now :)

I'm pretty sure what I posted in post #5 is correct. Do you understand both of those procedures?

edit: I believe if you follow those two procedures there should be no need to reinstall Windows.

---

### Post by Chrishannah8386 on 2011-03-14
I ran through the first procedure that you gave me using the fixboot and i think i made it slightly worse...

i copied the recovery file to the main boot drive which is what i thought i was supposed to, then re-booted selected windows 7 and then got some very strange text sufficed to say it did not work, i am going to try the recovery option. i have a recovery disc but when i put it in it gives me no options to repair the startup, so i am currently downloading the other recovery disc and hope to have more luck

i have not given up

---

### Post by kansasnoob on 2011-03-14
I'm not quite sure what you're calling "fixboot" here:

> I ran through the first procedure that you gave me using the fixboot and i think i made it slightly worse...

There is a true fixboot repair option but I didn't say to do that. If you ran through this procedure:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

And fixed /dev/sda2 as described there I would certainly still expect an error because you also need to do this:

[http://ubuntuforums.org/showpost.php?p=8929988&postcount=357](http://ubuntuforums.org/showpost.php?p=8929988&postcount=357)

It's typical for Win7 to spread boot files over two partitions. I don't know why.

NOTE: you may have to repeat the latter of the two at least twice because the repair disc tends to fix one problem at a time.

---

### Post by oldfred on 2011-03-14
Do you still have boot flag on sda2? Windows repairs only work on the partition with the boot flag.

The testdisk procedure that kansasnoob linked you to, is the best to repair the boot sector in sda2.

Win7 changed to a separate (hidden in windows) partition supposedly so you can encrypt the main install. Also when we convert to gpt (as opposed to MBR/msdos) we have a small efi or grub_bios boot partition even with grub. Of course current versions of windows will not boot with gpt.

---

### Post by Chrishannah8386 on 2011-03-14
yes i defiantly made it worse,there was no option for

Sixth   screen:  "BackupBS" in the list inside testdisk for SDA3

the 3rd one in the list so insted i went to sda2 this was called [Recovery] sda 3 was called [OS] i selected the sda2 and recovery and it gae me the option for backup BS and gave me the caption something like "Copy backup boot sector over BOOT SECTOR"

and i thought well thats the option that makes sense so did it. 

then i went to the windows recovery disc stage did the repair

then logged into ubuntu and then ran the update grub this did update but did not work. and windows would not boot however this time insted aof a blinking hyphen i get sime text at least

i have since put in the windows disc again and when i tried to run it again as you suggested. i was unable to go into the repair again as it said "you have recently had a usb disk into this computer please re-boot and re-try" i have done this several times and to no effect.

i have test disc open now, and i have the options to 

rebuild BS
Repair MTF

at this point i'm considering a re-install.
however it may be possible to "recover" using the original windows recovery disc i have then re-try the above

---

### Post by oldfred on 2011-03-15
As kansasnoob mentioned before you also are missing this in sda3.

missing "/windows/system32/winload.exe" 

If this file there in sda3 and the folders with windows and system32? If not that is your main install and repair may not fix it. If you can see your files you want to back them up now.

If so script missed it because of some other error in the windows system.

I would try chkdsk from a windows repair CD.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by kansasnoob on 2011-03-15
Absolutely listen to oldfred. He can run circles around me regarding these Windows boot issues :)

I'm always glad to see him come around.

---

### Post by kansasnoob on 2011-03-16
I'm curious where we ended up on this?

---

### Post by Chrishannah8386 on 2011-03-16
Hello
Thanks for your help so far but i dont appear to be getting anywhere.

the chkdsk c: /f/r did run fine without any errors (the c drive is the name of my system drive in this context i hope this is correct)
no problems were found


is there a way i can just edit the grub to point at that location that appears to be missing? 

i do get a beep when trying to start windows now, which is a slight improvment. think i might have to give into a re-install

if i do re-install i would format the whole drive again and then install windows _but_ how could in ensure that this issue did not re-occur if i re-installed ubuntu.

if anyone has some more suggestions i would be glad of it

thanks

---

### Post by kansasnoob on 2011-03-16
Just now looked back here. Give me a bit to regroup.

I need to better explain a few things :)

---

### Post by kansasnoob on 2011-03-16
Actually, in order that I can better help you, please post a new output from the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

In case you wonder why go back to my post #5. I wanted you to only run the testdisk procedure here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

on sda2 to correct this:

> sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Grub 2
Boot sector info: Grub 2 is installed in the boot sector of sda2 and
looks at sector 952725680 of the same hard drive for
core.img, but core.img can not be found at this
location. No errors found in the Boot Parameter Block.
Operating System:
Boot files/dirs: /bootmgr /Boot/BCD 

But in post #14 you said:

> yes i defiantly made it worse,there was no option for

Sixth screen: "BackupBS" in the list inside testdisk for SDA3


You weren't supposed to use the testdisk procedure on sda3! Only on sda2!

So, ultimately, my instructions sucked :(

I needed to be more detailed and I'll hopefully still get you out of this :)

You needed to use this procedure:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

only on sda2, then you needed an appropriate Win7 repair disc to fix the boot files on sda3 :D

---

