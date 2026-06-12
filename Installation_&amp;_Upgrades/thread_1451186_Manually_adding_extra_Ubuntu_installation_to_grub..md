---
title: "Manually adding extra Ubuntu installation to grub."
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by Marc55 on 2010-04-10
Hi there,
I decided to try out a Lucid development release, and figured I'd install it to an extra partition (sda4) on my system, which currently Runs Kubuntu Karmic on sda1. The installation went well, but ended up installing its boot manager into the system. This worked, but I'd prefer to have the 'old' boot menu belonging to the primary install. I got the old boot menu back, but now I'm at loss trying to add the other installation to grub's menu.

I copied and edited one of the auto-generated items in grub's menu.lst, and made this:

```

title           KUbuntu 10.04 beta 1                                            
uuid            7e87b610-8d50-44a7-9b7c-da80e4db380e                      
kernel          (hd0,3)/boot/vmlinuz-2.6.32-16-generic root=UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e ro quiet nosplash                            
initrd          (hd0,3)/boot/initrd.img-2.6.32-16-generic     

```

The id in the uuid and kernel lines is that of sda4 (as reported by blkid) and the paths in the kernel and initrd lines are also adjusted, i.e. the vmlinuz and initrd files exist on sda4. hd0,3 is what grub calls sda4.

The uuid command works, I've tried this manually on the grub command line. I also know that it uses the correct partition, because sda4 is the only ext4 partition on my system, and the file system type is mentioned in the output of uuid.

After that, the kernel command fails with "Error 15: File not found".
I have no idea why it fails or what else to try...

Can anybody help me out?

---

### Post by tommcd on 2010-04-10
> **Marc55 said:**
> 
 I got the old boot menu back, but now I'm at loss trying to add the other installation to grub's menu.

How did you "[get] the old boot menu back"? If the Lucid install on /dev/sda4 took over the MBR, and you wish to have the Karmic install on /dev/sda1 regain control of the MBR to boot your system, all you have to do is boot Karmic on /dev/sda1 and run:
```
sudo grub-install /dev/sda
```
Then run:
```
sudo update-grub
```
This will restore Karmic's on /dev/sda1 control of the MBR to boot your system, and update the grub.cfg file to include the Lucid install on /dev/sda4.
If you have already managed to reinstall Karmic's grub to the MBR and wish to update it to include the Lucid install on /dev/sda4, then just boot up Karmic and run: 
```
sudo update-grub
```
and you should be good.

---

### Post by Marc55 on 2010-04-10
Thanks for the reply!

> **tommcd said:**
> How did you "[get] the old boot menu back"? If the Lucid install on /dev/sda4 took over the MBR, and you wish to have the Karmic install on /dev/sda1 regain control of the MBR to boot your system, all you have to do is boot Karmic on /dev/sda1 and run:
```
sudo grub-install /dev/sda
```

I did it through the grub console, but yes.

> **tommcd said:**
> 
Then run:
```
sudo update-grub
```

update-grub does not seem to find the kernel on sda4. I've added an entry for sda4 to fstab so it is mounted to /mnt/sda4, but that doesn't seem to help.
I've looked at the source of update-grub, but couldn't figure out where it looks for kernels apart from /boot. Is there a fixed place the other partition has to be mounted to?

---

### Post by oldfred on 2010-04-10
Is your Karmic an upgrade as the entry you are showing is for grub legacy?

To see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I recommend the script for anyone with multiple installs so they can know where everything is at for booting. I run it before and after any changes so I can be sure where my boot loaders  are and to document my system's boot.

---

### Post by Marc55 on 2010-04-10
> **oldfred said:**
> Is your Karmic an upgrade as the entry you are showing is for grub legacy?

Yes, it's grub legacy on karmic.

Thanks for the link. Here's the output from the boot info script:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x77777777

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    83,891,429    83,891,367  83 Linux
/dev/sda2         470,174,417   488,392,064    18,217,648   5 Extended
/dev/sda5         470,174,418   488,392,064    18,217,647  82 Linux swap / Solaris
/dev/sda3          83,891,430   465,981,389   382,089,960  83 Linux
/dev/sda4    *    465,981,390   470,174,354     4,192,965  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        d5677094-c049-4df2-bbae-a8fac07758a1   ext3       sys                           
/dev/sda3        db72eb64-c24c-4eda-8a38-b381c00c1b0d   ext3       data                          
/dev/sda4        7e87b610-8d50-44a7-9b7c-da80e4db380e   ext4                                     
/dev/sda5        79a83231-1718-4040-a4aa-0060c32fe112   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda3        /home                    ext3       (rw)
/dev/sda4        /mnt/sda4                ext4       (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

hiddenmenu
default 0
timeout 3

title		KUbuntu 10.04, kernel 2.6.32-16-generic
uuid		7e87b610-8d50-44a7-9b7c-da80e4db380e
kernel		(hd0,3)/boot/vmlinuz-2.6.32-16-generic root=UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e ro quiet nosplash 
initrd		(hd0,3)/boot/initrd.img-2.6.32-16-generic

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d5677094-c049-4df2-bbae-a8fac07758a1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet nosplash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		d5677094-c049-4df2-bbae-a8fac07758a1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d5677094-c049-4df2-bbae-a8fac07758a1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=79a83231-1718-4040-a4aa-0060c32fe112 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# data
/dev/sda3	/home	auto	auto,rw
# alternative linux install
UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e	/mnt/sda4	ext4	auto,rw

=================== sda1: Location of files loaded by Grub: ===================


  30.0GB: boot/grub/menu.lst
  28.7GB: boot/grub/stage2
  30.0GB: boot/initrd.img-2.6.31-14-generic
  30.0GB: boot/initrd.img-2.6.31-15-generic
  30.0GB: boot/initrd.img-2.6.31-16-generic
  30.0GB: boot/initrd.img-2.6.31-17-generic
  30.1GB: boot/initrd.img-2.6.31-19-generic
  30.2GB: boot/initrd.img-2.6.31-20-generic
  28.6GB: boot/vmlinuz-2.6.31-14-generic
  30.0GB: boot/vmlinuz-2.6.31-15-generic
  30.0GB: boot/vmlinuz-2.6.31-16-generic
  30.0GB: boot/vmlinuz-2.6.31-17-generic
  28.6GB: boot/vmlinuz-2.6.31-19-generic
  30.1GB: boot/vmlinuz-2.6.31-20-generic
  30.2GB: initrd.img
  30.1GB: initrd.img.old
  30.1GB: vmlinuz
  28.6GB: vmlinuz.old

=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
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
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7e87b610-8d50-44a7-9b7c-da80e4db380e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-16-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-15-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 9.10, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set d5677094-c049-4df2-bbae-a8fac07758a1
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda4       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=79a83231-1718-4040-a4aa-0060c32fe112 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 240.6GB: boot/grub/core.img
 240.6GB: boot/grub/grub.cfg
 240.6GB: boot/initrd.img-2.6.32-16-generic
 240.6GB: boot/vmlinuz-2.6.32-16-generic
 240.6GB: initrd.img
 240.6GB: vmlinuz

```

---

### Post by oldfred on 2010-04-10
I have not tried using menu.lst to boot lucid.

I would make it exactly like you current entries with updated UUIDs.
You have the extra (hd0,3) at the beginning of your lines.

title        KUbuntu 10.04, kernel 2.6.32-16-generic
uuid        7e87b610-8d50-44a7-9b7c-da80e4db380e
kernel        [COLOR=DarkRed](hd0,3)[/COLOR]/boot/vmlinuz-2.6.32-16-generic root=UUID=7e87b610-8d50-44a7-9b7c-da80e4db380e ro quiet nosplash 
initrd        [COLOR=DarkRed](hd0,3)[/COLOR]/boot/initrd.img-2.6.32-16-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d5677094-c049-4df2-bbae-a8fac07758a1
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d5677094-c049-4df2-bbae-a8fac07758a1 ro quiet nosplash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

---

### Post by Marc55 on 2010-04-10
> **oldfred said:**
> I have not tried using menu.lst to boot lucid.
Hmm, Lucid does not force an upgrade to Grub2, does it? So it should work in theory.

EDIT: Either way, the error seems a little more fundamental, since grub does not even find the kernel. Grub 0.97 does support ext4, right?

> **oldfred said:**
> You have the extra (hd0,3) at the beginning of your lines.
I tried with and without them, doesn't make a difference.

---

### Post by oldfred on 2010-04-10
Ubuntu updated old grub with 9.04 to recognize ext4 partitions. That was when they first started supporting ext4. 

Other distributions may not support 0.97. Grub legacy has not be maintained for years and each distribution made tweaks that may or may not have been incorporated by others.

---

### Post by Marc55 on 2010-04-11
Ok, so if nobody else has an idea of what could be the problem here, I can either reinstall the Lucid beta using ext3, or update to grub2.
I'm not that hot about messing (even more) with the bootloader, but sticking to ext3 isn't exactly a solution either. Mmh.. :-k

---

### Post by tommcd on 2010-04-11
> **Marc55 said:**
> ...  I can either reinstall the Lucid beta using ext3, or update to grub2.
I'm not that hot about messing (even more) with the bootloader, but sticking to ext3 isn't exactly a solution either. ...
I think that your best bet (short of a reinstall of Lucid) would be a full upgrade to grub2 for your Karmic install. The fact that you are still dealing with grub-legacy is clearly the problem here (thanks to Old Fred for spotting this!!!).
To do a full upgrade to grub2 for your Karmic install, follow this section of the grub2 tutorial from the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%20and%20newer%29](https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%20and%20newer%29)
I have no direct experience with upgrading from grub-legacy to grub2 since I always do clean installs when upgrading Ubuntu. (Clean installs avoid problems like this, among many others).
Once you are fully converted to grub2, then the **sudo update-grub** command  should be all that is needed to add your Lucid install to Karmic's grub2 /boot/grub/grub.cfg file.
I recently installed Lucid Lubuntu beta1 (Ubuntu with the LXDE desktop) to my laptop. Running **sudo update-grub** was all that was needed to add Lubuntu Lucid beta to my Ubuntu Karmic's grub2 boot menu. 
As always though, I had done a clean install of Karmic, so I had no remnants of grub-legacy on my system.

---

### Post by Marc55 on 2010-04-13
So, I just upgraded to Grub2, and everything worked flawlessly.

Thanks a lot to everybody who helped!

---

