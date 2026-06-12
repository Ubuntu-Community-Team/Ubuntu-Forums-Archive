---
title: "Win 7 not booting after Ubuntu 10.04 LTS install"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by waratte on 2012-01-06
Hello,

Yesterday, I've tried to install Ubuntu 10.04 LTS on my system. I've installed it successfully however, it seems that I had made Windows 7 unable to start up. When I select Windows 7 from the GRUB menu, it starts to show the logo but halfway before it displays the full logo, the screen flickers. It then shows some information at the top of the screen in white text but it moves much much too quickly to be able to be read. Then, my computer starts back up again and reaches the GRUB menu.

I should also tell how I went about installing ubuntu. In windows, I had used the disk manager that comes with windows to shrink down my main partition to make room for ubuntu. I had created exactly 32GB (I believe this is the right measurement) of unallocated free space. There were also other partitions, one named SYSTEM and the other was a ~14GB HP system restore partition or something of that nature. I then had restarted my computer and inserted my flash drive into it, which held a live version of Ubuntu 10.04 LTS. I continued on with installing ubuntu, though, when I got to where you select/resize the partitions, no option had come up with asking me if I wanted to install Ubuntu alongside windows. Only an option to do it manually or wipe my hard drive. I thought this was weird as the last time I installed ubuntu on a friend's system, the former option had came up. I proceeded anyways, selecting to manually select/resize partitions and whatnot. When I came to the screen, my free space was much bigger than I had made it, 48GB if I can remember correctly. Also, I think my HP partition wasn't there, though I'm not sure. I then installed ubuntu to the freespace and left 4GB for swap. Afterwards, I decided to boot back into Windows and here we are.

I've ran the "boot script" or whatever it's called, so here is the results:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sdb starts 
                       at sector 129. But according to the info from fdisk, 
                       sdb starts at sector 0.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   529,911,807   529,502,208  42 SFS
/dev/sda4         529,913,854   574,360,500    44,446,647   5 Extended
/dev/sda5         541,157,376   574,360,500    33,203,125  83 Linux
/dev/sda6         529,913,856   537,726,355     7,812,500  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        B81E9DEB1E9DA344                       ntfs       SYSTEM
/dev/sda3        C422F8DC22F8D480                       ntfs       
/dev/sda5        8729e4dc-78fc-4ad4-8d5e-e968494a3e14   ext4       
/dev/sda6        18005b3d-87d9-48d7-bba9-6f9ebe6aa27d   swap       
/dev/sdb         E0FD-1813                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb         /media/E0FD-1813         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
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
search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=8729e4dc-78fc-4ad4-8d5e-e968494a3e14 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=8729e4dc-78fc-4ad4-8d5e-e968494a3e14 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 8729e4dc-78fc-4ad4-8d5e-e968494a3e14
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	 

```

---

### Post by waratte on 2012-01-07
I'm sorry for the double post but, can no one help me? Have I posted in the wrong category?

---

### Post by darkod on 2012-01-07
In the fdisk results the SFS means your disk in windows is dynamic, not basic. Ubuntu can't install on dynamic. SFS is a MS format.

You could try repairing the windows boot process with the win7 dvd and the Repair This Computer option.

Then you would need to find a way to convert the disk from dynamic to basic without losing the data on it. Try finding info on Google of windows forums.

---

### Post by waratte on 2012-01-08
Huh, is that so? Well, that sucks...

So, is the disk being dynamic the cause of why Windows 7 won't boot?

---

### Post by darkod on 2012-01-08
It has something to do with it. I don't have much experience with dynamic disks but from what we have seen here they don't play nice with linux.

---

### Post by Mark Phelps on 2012-01-08
You can try using Boot-Repair to see if it will repair Win7 enough to let you boot into it:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

If that works, you can try then booting into Command Mode in Win7 (hold down F8 and keep pressing it until you get a selection menu).

Once you get into command mode, you can use the Diskpart command to do the filesystem conversion:

[http://support.microsoft.com/kb/309044]("http://support.microsoft.com/kb/309044")

---

### Post by waratte on 2012-01-08
After searching a bit of time on Google, I've stumbled onto a page that led me to a solution. [http://petri.co.il/forums/showthread.php?t=3844](http://petri.co.il/forums/showthread.php?t=3844)

Using the instructions on the third post solved my problem; I've converted my disk back to basic without losing any data. I've now successfully booted up Windows 7 without any problems.

Thank you darkod for leading me into the right direction.

---

### Post by MadMaxe on 2012-01-09
Hi Waratte, I have a very similar problem. Couple of questions - where/how did you install dskprobe? and where did you download it from?

Thanks!

---

### Post by waratte on 2012-01-09
Ah, well instead of that program, I had used similar program for Ubuntu. It was a command line hex editor capable of opening hard disks. Here it is here: [https://launchpad.net/ubuntu/hardy/amd64/ncurses-hexedit/0.9.7-13/](https://launchpad.net/ubuntu/hardy/amd64/ncurses-hexedit/0.9.7-13/)

---

