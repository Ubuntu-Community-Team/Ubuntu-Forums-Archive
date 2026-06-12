---
title: "Multiboot-what distro's mess up your bootloader?"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2011-02-28
Hi, I have Linux Mint installed on my 2nd hdd & it's the one that boot's my system. I've read about distro's like Fedora will mess up your boot-loader. 

Can anyone tell me how I can know which ones are safe to install & how to install the ones that aren't?

I know all the Ubuntu based distro's are ok, but by Ubuntu based, does that also mean Debian based, since Ubuntu is Debian based?

Anyone have any good info for this?  

Pic of hdd if it helps...as you can see, I'm just getting started. :-) I'm open for tips & suggestions too.

---

### Post by sikander3786 on 2011-02-28
Any distro that doesn't give you a choice to 'install' or 'not install' the bootloader can mess up your existing setup. You are running Linux Mint and probably it comes with Grub2 so all you need to do with any distro either Ubuntu based, Debian based or Fedora or any other is to do the complete install _without_ the installation of boot loader. Then from Linux Mint's Terminal,

```
sudo update-grub
```

And the new installs should be added to your existing Grub menu.

However if any of those distro's messes up your boot by over-writing the MBR, recovery is not much difficult. All it takes is 2 commands to re-install Grub for your favorite distro. See here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

And in case anything goes wrong, we can give you exact commands to follow if you could post the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net").

---

### Post by Dutch70 on 2011-02-28
> **sikander3786 said:**
> Any distro that doesn't give you a choice to 'install' or 'not install' the bootloader can mess up your existing setup. You are running Linux Mint and probably it comes with Grub2 so all you need to do with any distro either Ubuntu based, Debian based or Fedora or any other is to do the complete install _without_ the installation of boot loader. Then from Linux Mint's Terminal,

```
sudo update-grub
```

And the new installs should be added to your existing Grub menu.

However if any of those distro's messes up your boot by over-writing the MBR, recovery is not much difficult. All it takes is 2 commands to re-install Grub for your favorite distro. See here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

[http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html](http://ubuntu4beginners.blogspot.com/2011/01/re-installing-grub2.html)

And in case anything goes wrong, we can give you exact commands to follow if you could post the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net").


Thank you sikander, and not a moment to soon. :P
 I installed PCLinuxOS & it took over my bootloader. (Luckily I unplugged my first hhd, the one with vista & ubuntu) But Mint is the one that handled everything, and PCLinuxOS doesn't seem to recognize Mint. although it did Kubuntu. 

Now If I can get this figured out with the links  you gave I'll be set. 
Booting to the live cd now.

Can't help but wonder if I can plug in my Ubuntu/Vista hdd and use Ubuntu to update-grub & fix it, but I need to know how to do this.

---

### Post by Dutch70 on 2011-02-28
Well, that got my boot-loader fixed, I can log into Mint & Kubuntu, but now I get a kernel panic when I try to log into PCLinuxOS. I have no idea how to fix that. 

Does anyone have any ideas? Is it because PCLinuxOS still uses grub legacy? and if so, wouldn't that make it next to, if not impossible to boot with my Ubuntu based distro's?

---

### Post by sikander3786 on 2011-02-28
> **Dutch70 said:**
> Well, that got my boot-loader fixed, I can log into Mint & Kubuntu, but now I get a kernel panic when I try to log into PCLinuxOS. I have no idea how to fix that. 

Does anyone have any ideas? Is it because PCLinuxOS still uses grub legacy? and if so, wouldn't that make it next to, if not impossible to boot with my Ubuntu based distro's?
Perhaps, Grub Legacy shouldn't be causing problems to Grub2.

Can you please post the output of bootinfoscript to let us dig deep in your Kernel Panic problem.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by Dutch70 on 2011-02-28
> **sikander3786 said:**
> Perhaps, Grub Legacy shouldn't be causing problems to Grub2.

Can you please post the output of bootinfoscript to let us dig deep in your Kernel Panic problem.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Wow, this is a monster...No real urgency here though. Everything except PCLinuxOS boots fine (including Fefora...lol) I could always just delete PCLinuxOS, but that wouldn't help me learn or keep me from making the same mistake. 

So here it is...
(the "Ubuntu" showing up on sda2 is actually Kubuntu)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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
    Operating System:  PCLinuxOS release 2010 
                       (PCLinuxOS) for i586 Kernel 2.6.33.7-pclos6.bfs on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    41,945,087    41,943,040  83 Linux
/dev/sda2          41,945,088   136,316,927    94,371,840  83 Linux
/dev/sda3         136,318,974   976,773,119   840,454,146   5 Extended
/dev/sda5         968,386,560   976,773,119     8,386,560  82 Linux swap / Solaris
/dev/sda6         136,318,976   167,776,255    31,457,280  83 Linux
/dev/sda7         167,778,304   199,235,583    31,457,280  83 Linux
/dev/sda8         199,237,632   230,694,911    31,457,280  83 Linux
/dev/sda9         230,696,960   262,154,239    31,457,280  83 Linux
/dev/sda10        262,156,288   293,613,567    31,457,280  83 Linux
/dev/sda11        293,615,616   325,072,895    31,457,280  83 Linux
/dev/sda12        325,074,944   534,790,143   209,715,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   481,722,367   481,722,305   7 HPFS/NTFS
/dev/sdb2         481,725,151   683,678,204   201,953,054   5 Extended
/dev/sdb5         481,725,153   512,441,369    30,716,217  83 Linux
/dev/sdb6         679,485,303   683,678,204     4,192,902  82 Linux swap / Solaris
/dev/sdb7         512,441,433   679,485,239   167,043,807  83 Linux
/dev/sdb3         683,678,205   703,281,151    19,602,947   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       31678a5b-d73b-4a14-ab90-40c7772e5f5a   ext4                                     
/dev/sda11       52112621-f8f5-4145-a5dc-d8546846f50e   ext4                                     
/dev/sda12       6B512471223DAEF6                       ntfs       data                          
/dev/sda1        d1a051c5-7492-4f69-8de1-569738af55dc   ext4       linux mint                    
/dev/sda2        4de43706-aa69-493f-8808-6988b53f1fe2   ext4       Kubuntu MM                    
/dev/sda3: PTTYPE="dos" 
/dev/sda5        8316ec3c-6153-427c-bb21-884dc8b29de6   swap                                     
/dev/sda6        3f399271-92e3-4683-827d-45125fea0d8c   ext4       PCLinuxOS                     
/dev/sda7        69b83ba8-5231-4142-8e17-2ea50eca237d   ext4       Fedora-14                     
/dev/sda8        d7eb60ae-8d1d-4b0f-a7bb-1d377e912c41   ext4                                     
/dev/sda9        edda272b-1b93-493e-9e48-51d60f577fd6   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ACFE2CAFFE2C73AC                       ntfs       COMPAQ                        
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        2C88743C8874071C                       ntfs       FACTORY_IMAGE                 
/dev/sdb5        ff39fd44-0914-4af5-969b-e90ce4ab8c27   ext4       Ubuntu Mav- /                 
/dev/sdb6        0f789bee-bcdb-4fcd-8a61-ba6624f660f6   swap                                     
/dev/sdb7        88457893-f070-4384-b6e1-b09fa6ec54ab   ext2       Ubuntu Mav /home              
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro  vga=792  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro single  vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "linux (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
	initrd (hd0,5)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6
	initrd (hd0,5)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=3f399271-92e3-4683-827d-45125fea0d8c failsafe
	initrd (hd0,5)/boot/initrd.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 69b83ba8-5231-4142-8e17-2ea50eca237d
	linux /boot/vmlinuz-2.6.35.11-83.fc14.x86_64 root=/dev/sda7
	initrd /boot/initramfs-2.6.35.11-83.fc14.x86_64.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda7)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 69b83ba8-5231-4142-8e17-2ea50eca237d
	linux /boot/vmlinuz-2.6.35.6-45.fc14.x86_64 root=/dev/sda7
	initrd /boot/initramfs-2.6.35.6-45.fc14.x86_64.img
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set acfe2caffe2c73ac
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff39fd44-0914-4af5-969b-e90ce4ab8c27 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sdb5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=ff39fd44-0914-4af5-969b-e90ce4ab8c27 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
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
UUID=d1a051c5-7492-4f69-8de1-569738af55dc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.1GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  13.2GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
  13.2GB: vmlinuz

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
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
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro vga=792 splash quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro single vga=792 splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "linux (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
	initrd (hd0,5)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6
	initrd (hd0,5)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=3f399271-92e3-4683-827d-45125fea0d8c failsafe
	initrd (hd0,5)/boot/initrd.img
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=4de43706-aa69-493f-8808-6988b53f1fe2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  64.7GB: boot/grub/core.img
  47.7GB: boot/grub/grub.cfg
  22.8GB: boot/initrd.img-2.6.35-25-generic
  64.7GB: boot/vmlinuz-2.6.35-25-generic
  22.8GB: initrd.img
  64.7GB: vmlinuz

=========================== sda6/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,5)/boot/gfxmenu
default 0

title linux
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c  resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=3f399271-92e3-4683-827d-45125fea0d8c  resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=3f399271-92e3-4683-827d-45125fea0d8c  failsafe
initrd (hd0,5)/boot/initrd.img

# This is a divider, added to separate the menu items below from the PCLINUXOS standard grub entries
title		Other operating systems:


# This entry automatically added by the PCLinuxOS redo-mbr for an existing
# linux installation on /dev/sda2.
title		Ubuntu 10.10 (10.10) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 
initrd		/boot/initrd.img-2.6.35-25-generic
savedefault
boot


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda6 :
UUID=3f399271-92e3-4683-827d-45125fea0d8c	/	ext4	defaults	1	1
#Entry for /dev/sda12 :
UUID=6B512471223DAEF6	/media/data	ntfs-3g	defaults,locale=en_US.UTF-8,umask=000	0	0
none	/proc	proc	defaults	0	0
#Entry for /dev/sda5 :
UUID=8316ec3c-6153-427c-bb21-884dc8b29de6	swap	swap	defaults	0	0
none	/dev/pts	devpts	defaults	0	0



=================== sda6: Location of files loaded by Grub: ===================


  72.3GB: boot/grub/menu.lst
  82.8GB: boot/grub/stage2
  70.9GB: boot/initrd-2.6.33.7-pclos6.bfs.img
  70.9GB: boot/initrd.img
  82.8GB: boot/vmlinuz
  82.8GB: boot/vmlinuz-2.6.33.7-pclos6.bfs

=============================== sda7/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Mon Feb 28 13:01:11 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=69b83ba8-5231-4142-8e17-2ea50eca237d /                       ext4    defaults        1 1
UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


  89.5GB: boot/initramfs-2.6.35.11-83.fc14.x86_64.img
  88.2GB: boot/initramfs-2.6.35.6-45.fc14.x86_64.img
  89.2GB: boot/initrd-plymouth.img
  89.1GB: boot/vmlinuz-2.6.35.11-83.fc14.x86_64
  87.0GB: boot/vmlinuz-2.6.35.6-45.fc14.x86_64

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
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
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ff39fd44-0914-4af5-969b-e90ce4ab8c27 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=ff39fd44-0914-4af5-969b-e90ce4ab8c27 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set ff39fd44-0914-4af5-969b-e90ce4ab8c27
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1) (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro vga=792 quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set d1a051c5-7492-4f69-8de1-569738af55dc
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=d1a051c5-7492-4f69-8de1-569738af55dc ro single vga=792
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda2)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 4de43706-aa69-493f-8808-6988b53f1fe2
	linux /boot/vmlinuz-2.6.35-25-generic root=UUID=4de43706-aa69-493f-8808-6988b53f1fe2 ro single
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set acfe2caffe2c73ac
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set 2c88743c8874071c
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ff39fd44-0914-4af5-969b-e90ce4ab8c27 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=88457893-f070-4384-b6e1-b09fa6ec54ab /home           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=0f789bee-bcdb-4fcd-8a61-ba6624f660f6 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 257.5GB: boot/grub/core.img
 253.7GB: boot/grub/grub.cfg
 258.6GB: boot/initrd.img-2.6.35-25-generic
 257.8GB: boot/vmlinuz-2.6.35-25-generic
 258.6GB: initrd.img
 257.8GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by wilee-nilee on 2011-02-28
On the main subject I keep a distro like Maverick as of now as the grub2 control. So for example I installed several distros with grub legacy lately, and lilo; I let them install the grub legacy boot loader in the mbr. I then pull out my trusty supergrub on a thumb and boot straight to maverick and run.
sudo grub-install /dev/sda    (sda is my hd)
then 
sudo update-grub
This puts grub2 back in the mbr and auto finds the other OS's with the older grub and boots them.

I could reload the mbr with a live Ubuntu cd of Maverick and point it at it but this other method is quicker.

It is not the distro's exactly it is understanding the 3 main Linux bootloaders lilo, grub legacy, and grub2

---

### Post by Dutch70 on 2011-02-28
Hi willie-nillie, 
 
 That's exactly what I did, and it fixed my boot-loader. 

 I can boot into every OS except for PCLinuxOS. That's when I get the kernel panic, after reinstalling Grub2.

---

### Post by wilee-nilee on 2011-02-28
Here is a link I am downloading PclinuxOS right now having some space on my HD, it is grub legacy.
[http://ubuntuforums.org/showthread.php?t=1547193](http://ubuntuforums.org/showthread.php?t=1547193)

---

### Post by Dutch70 on 2011-02-28
> **wilee-nilee said:**
> Here is a link I am downloading PclinuxOS right now having some space on my HD, it is grub legacy.
[http://ubuntuforums.org/showthread.php?t=1547193](http://ubuntuforums.org/showthread.php?t=1547193)

Hahaa, thanks wilee-nilee. That link led me to the answer.

Post #4 UncleV says
> GRUB counts partitions starting from (hdx,0) and GRUB2 starts from (hdx,1).

So, I edited /boot/grub/grub.cfg. 
I changed the parts in bold/red from (hd0,5) to (hd0,6) and now it boots nicely.

```
menuentry "linux (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
	initrd **[COLOR="Red"](hd0,6)[/COLOR]**/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6
	initrd **[COLOR="Red"](hd0,6)[/COLOR]**/boot/initrd.img
}
menuentry "failsafe (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=3f399271-92e3-4683-827d-45125fea0d8c failsafe
	initrd **[COLOR="Red"](hd0,6)[/COLOR]**/boot/initrd.img
``` 

Now to figure out how to keep it from changing back every time I update-grub 

Also, in my grub menu, when I'm booting... 
 Kubuntu shows up as Ubuntu, and PCLinuxOS as you can see above just shows up as "linux". 
Can I just change the names in the list above to make them show correctly?

---

### Post by wilee-nilee on 2011-02-28
I haven't used the grub customizer but I suspect it will do what you need.
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by Dutch70 on 2011-03-01
> **wilee-nilee said:**
> I haven't used the grub customizer but I suspect it will do what you need.
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

 Thanks for all your help wilee-nilee & Sikander :D

That's a nice little tool & tutorial. Don't rename Fedora with it though, every time I did, it came up with a new entry when I updated grub. Everything else I used on it so far has worked flawlessly. 

I think I can safely mark this thread solved now.
Thanks again!!!

:popcorn:

---

