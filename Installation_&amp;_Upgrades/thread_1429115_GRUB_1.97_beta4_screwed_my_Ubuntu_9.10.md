---
title: "GRUB 1.97 beta4 screwed my Ubuntu 9.10"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by failmerc on 2010-03-13
Hey guys,

A few days ago I jumped from Windows 7 to Ubuntu 9.10 and I was very impressed. It was the first time I tried Linux and it instantly got my atention. 

Today I was reading on the official Ubuntu site that it has many free games in the software center and I even saw a nice FPS on their pic on the site. So I decided to check out some games and eventually I was installing 3 games from the software center. 

After one game was finished I decided to check it out. After I pressed "Quit Game" my Ubuntu froze up. I decided to leave it on while I went for dinner. When I came back it was still frozen, so I went for a reset. 

After that I couldn't enter Ubuntu anymore. After having selected Ubuntu it doesn't bring me to the next screen anymore where I chose what particular Ubuntu I want to boot in. I get the "Minimal BASH-like line editing is supported" error. 

Since I'm new I have no idea what to do now. I have, however, checked out many topics and many ways to "fix" it and tried it myself but no luck. This is really pissing me off because I am now on Windows 7 and it sucks compared to Ubuntu. Can anyone tell me what to do? I'd like to get my Ubuntu back. 

I've already tried replacing the "wubildr" file with one provided on sites that said it would fix it but it didn't. I've also tried various lines inside the GRUB menu as well as with the Live CD but still no luck. I don't really feel like reinstalling Ubuntu so if anyone has any ideas they are all appreciated.

---

### Post by presence1960 on 2010-03-13
More info is needed about your setup- do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by failmerc on 2010-03-13
Here's the results. 

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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30d430d3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,405,324    80,405,262   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc394c394

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   312,576,061   312,575,999   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        22F83170F8314379                       ntfs                                     
/dev/sdb1        520C48250C480707                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

```

---

### Post by presence1960 on 2010-03-13
Your wubi install seems to be gone. Here is my boot info script. I have wubi installed on sda1 w/vista. Note the red, and scroll down to see wubi grub.cfg also in red: 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

[COLOR="Red"]sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab[/COLOR]

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 8 Helena - x64 
                       Edition
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda7 and 
                       looks at sector 325098505 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/grub.conf.
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7408b4a2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   146,801,969   146,801,907   7 HPFS/NTFS
/dev/sda2         146,801,970   396,371,744   249,569,775   5 Extended
/dev/sda5         146,802,033   209,712,509    62,910,477  83 Linux
/dev/sda6         209,712,573   272,623,049    62,910,477  83 Linux
/dev/sda7         272,623,113   335,533,589    62,910,477  83 Linux
/dev/sda8         335,533,653   343,935,584     8,401,932  82 Linux swap / Solaris
/dev/sda9         343,935,648   396,371,744    52,436,097  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00009028

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 1,048,578,614 1,048,578,552  83 Linux
/dev/sdc2       1,048,578,615 1,258,291,124   209,712,510   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       be56ee14-353d-4f00-af8b-577fe3f0bbbe   ext4                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        1E47E31A54CBB211                       ntfs       vista                         
/dev/sda5        101653d6-6dc9-4c4f-8487-eee283357676   ext4       mint                          
/dev/sda6        e0b415e6-168b-49e7-b62b-0fc42c83a6d7   ext4       karmic                        
/dev/sda7        35f50606-c5dc-4981-b609-cc08aa8aa6ef   ext4       sabayon                       
/dev/sda8        e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8   swap                                     
/dev/sda9        b732f52f-9f80-4272-8db0-8e586348ac14   ext4       lucid                         
/dev/sdb1        bd4ff60f-606d-43ac-81f2-6713bed14313   ext4       backup                        
/dev/sdc1        a9ce88a4-7a81-492e-958c-75ed13b54e0a   ext4       data                          
/dev/sdc2        790BFB1526B4964C                       ntfs       win-data                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/data              ext4       (rw,nosuid,nodev,uhelper=devkit)


[COLOR="Red"]======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1e47e31a54cbb211
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Other Operating System - Microsoft Windows (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 35f50606-c5dc-4981-b609-cc08aa8aa6ef
	linux /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   3.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   3.5GB: boot/initrd.img-2.6.31-19-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   3.1GB: boot/vmlinuz-2.6.31-19-generic
   3.5GB: initrd.img
    .8GB: initrd.img.old
   3.1GB: vmlinuz
   2.3GB: vmlinuz.old[/COLOR]

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
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
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 101653d6-6dc9-4c4f-8487-eee283357676
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
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
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 0452923552922c04
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
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
# / was on /dev/sda5 during installation
UUID=101653d6-6dc9-4c4f-8487-eee283357676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  78.9GB: boot/grub/core.img
  80.8GB: boot/grub/grub.cfg
  81.5GB: boot/initrd.img-2.6.31-17-generic
  76.2GB: boot/vmlinuz-2.6.31-17-generic
  81.5GB: initrd.img
  76.2GB: vmlinuz

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-19-generic
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (/dev/sda5) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Linux Mint 8 Helena x64, linux 2.6.31-17-generic (recovery mode) (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=101653d6-6dc9-4c4f-8487-eee283357676 ro single
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
}
menuentry "Other Operating System - Microsoft Windows (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	linux /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
}
menuentry "Ubuntu lucid (development branch) (10.04) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	linux /boot/vmlinuz-2.6.32-14-generic root=/dev/sda9
	initrd /boot/initrd.img-2.6.32-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 110.4GB: boot/grub/core.img
 112.2GB: boot/grub/grub.cfg
 120.3GB: boot/initrd.img-2.6.31-19-generic
 124.4GB: boot/initrd.img-2.6.31-20-generic
 115.6GB: boot/vmlinuz-2.6.31-19-generic
 113.5GB: boot/vmlinuz-2.6.31-20-generic
 124.4GB: initrd.img
 120.3GB: initrd.img.old
 113.5GB: vmlinuz
 115.6GB: vmlinuz.old

========================== sda7/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,6)
#          kernel /boot/kernel-genkernel real_root=/dev/sda7
#          initrd /boot/initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sda7
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd0,6)/boot/grub/splash.xpm.gz


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda8 real_resume=/dev/sda8 gentoo=nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Other Operating System - Microsoft Windows
	rootnoverify (hd7,0)
	chainloader +1
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefault
title=Sabayon Linux (kernel-genkernel-x86_64-2.6.32-sabayon)
	root (hd0,6)
	kernel /boot/kernel-genkernel-x86_64-2.6.32-sabayon BOOT_IMAGE=/boot/kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/sda7 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda8 real_resume=/dev/sda8
	initrd /boot/initramfs-genkernel-x86_64-2.6.32-sabayon
	savedefault


=============================== sda7/etc/fstab: ===============================

/dev/sda7               /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
/dev/sda8               swap                    swap    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


 157.6GB: boot/grub/grub.conf
 157.6GB: boot/grub/menu.lst
 166.4GB: boot/grub/stage2
 166.6GB: boot/initramfs-genkernel-x86_64-2.6.31-sabayon
 166.6GB: boot/initramfs-genkernel-x86_64-2.6.32-sabayon

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=b732f52f-9f80-4272-8db0-8e586348ac14 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=e11071ea-cf4b-47db-b0b8-e1eb9d3ccad8 none            swap    sw              0       0

=================== sda9: Location of files loaded by Grub: ===================


 195.6GB: boot/initrd.img-2.6.32-14-generic
 195.5GB: boot/vmlinuz-2.6.32-14-generic
 195.6GB: initrd.img
 195.5GB: vmlinuz


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg
```

---

### Post by failmerc on 2010-03-14
So how do I fix this? I'm pretty new to Ubuntu.

---

### Post by failmerc on 2010-03-14
Alright I figured I'd just download Wubi and reinstall again, but now it says the permission is denied and I have to view the log at 

c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log

```
02-24 15:42 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-24 15:42 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-24 15:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
02-24 15:42 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\data
02-24 15:42 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\bin\7z.exe
02-24 15:42 DEBUG  CommonBackend: Fetching basic info...
02-24 15:42 DEBUG  CommonBackend: original_exe=G:\wubi.exe
02-24 15:42 DEBUG  CommonBackend: platform=win32
02-24 15:42 DEBUG  CommonBackend: osname=nt
02-24 15:42 DEBUG  CommonBackend: language=nl_NL
02-24 15:42 DEBUG  CommonBackend: encoding=cp1252
02-24 15:42 DEBUG  WindowsBackend: arch=amd64
02-24 15:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\data\isolist.ini
02-24 15:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-24 15:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-24 15:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-24 15:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-24 15:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-24 15:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-24 15:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-24 15:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-24 15:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-24 15:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-24 15:42 DEBUG  WindowsBackend: Fetching host info...
02-24 15:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-24 15:42 DEBUG  WindowsBackend: windows version=vista
02-24 15:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-24 15:42 DEBUG  WindowsBackend: windows_sp=None
02-24 15:42 DEBUG  WindowsBackend: windows_build=7600
02-24 15:42 DEBUG  WindowsBackend: gmt=1
02-24 15:42 DEBUG  WindowsBackend: country=IT
02-24 15:42 DEBUG  WindowsBackend: timezone=Europe/Rome
02-24 15:42 DEBUG  WindowsBackend: windows_username=Pascal
02-24 15:42 DEBUG  WindowsBackend: user_full_name=Pascal
02-24 15:42 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
02-24 15:42 DEBUG  WindowsBackend: windows_language_code=1043
02-24 15:42 DEBUG  WindowsBackend: windows_language=Dutch
02-24 15:42 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
02-24 15:42 DEBUG  WindowsBackend: bootloader=vista
02-24 15:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20528.1875 mb free ntfs)
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(C: hd 20528.1875 mb free ntfs)
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(D: hd 21688.9648438 mb free ntfs)
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
02-24 15:42 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
02-24 15:42 DEBUG  WindowsBackend: uninstaller_path=None
02-24 15:42 DEBUG  WindowsBackend: previous_target_dir=None
02-24 15:42 DEBUG  WindowsBackend: previous_distro_name=None
02-24 15:42 DEBUG  WindowsBackend: keyboard_id=-268368877
02-24 15:42 DEBUG  WindowsBackend: keyboard_layout=it
02-24 15:42 DEBUG  WindowsBackend: keyboard_variant=
02-24 15:42 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
02-24 15:42 DEBUG  CommonBackend: locale=nl_NL.UTF-8
02-24 15:42 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
02-24 15:42 DEBUG  CommonBackend: Searching ISOs on USB devices
02-24 15:42 DEBUG  CommonBackend: Searching for local CDs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Ubuntu Netbook Remix CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Kubuntu Netbook CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-24 15:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 15:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-24 15:42 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-24 15:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-24 15:42 INFO   Distro: Found a valid CD for Ubuntu: G:\
02-24 15:42 INFO   root: Running the CD menu...
02-24 15:42 DEBUG  WindowsFrontend: __init__...
02-24 15:42 DEBUG  WindowsFrontend: on_init...
02-24 15:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\translations, languages=['nl_NL', 'nl']
02-24 15:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl46A8.tmp\translations, languages=['nl_NL', 'nl']
02-24 15:43 DEBUG  WindowsFrontend: frontend.on_quit
02-24 15:43 DEBUG  root: application.on_quit
02-24 15:43 INFO   root: sys.exit
03-06 16:27 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-06 16:27 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-06 16:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
03-06 16:27 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\data
03-06 16:27 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\bin\7z.exe
03-06 16:27 DEBUG  CommonBackend: Fetching basic info...
03-06 16:27 DEBUG  CommonBackend: original_exe=G:\wubi.exe
03-06 16:27 DEBUG  CommonBackend: platform=win32
03-06 16:27 DEBUG  CommonBackend: osname=nt
03-06 16:27 DEBUG  CommonBackend: language=nl_NL
03-06 16:27 DEBUG  CommonBackend: encoding=cp1252
03-06 16:27 DEBUG  WindowsBackend: arch=amd64
03-06 16:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\data\isolist.ini
03-06 16:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-06 16:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-06 16:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-06 16:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-06 16:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-06 16:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-06 16:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-06 16:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-06 16:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-06 16:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-06 16:27 DEBUG  WindowsBackend: Fetching host info...
03-06 16:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-06 16:27 DEBUG  WindowsBackend: windows version=vista
03-06 16:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-06 16:27 DEBUG  WindowsBackend: windows_sp=None
03-06 16:27 DEBUG  WindowsBackend: windows_build=7600
03-06 16:27 DEBUG  WindowsBackend: gmt=1
03-06 16:27 DEBUG  WindowsBackend: country=IT
03-06 16:27 DEBUG  WindowsBackend: timezone=Europe/Rome
03-06 16:27 DEBUG  WindowsBackend: windows_username=Pascal
03-06 16:27 DEBUG  WindowsBackend: user_full_name=Pascal
03-06 16:27 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-06 16:27 DEBUG  WindowsBackend: windows_language_code=1043
03-06 16:27 DEBUG  WindowsBackend: windows_language=Dutch
03-06 16:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-06 16:27 DEBUG  WindowsBackend: bootloader=vista
03-06 16:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18773.9296875 mb free ntfs)
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(C: hd 18773.9296875 mb free ntfs)
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(D: hd 22626.4570313 mb free ntfs)
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-06 16:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-06 16:27 DEBUG  WindowsBackend: uninstaller_path=None
03-06 16:27 DEBUG  WindowsBackend: previous_target_dir=None
03-06 16:27 DEBUG  WindowsBackend: previous_distro_name=None
03-06 16:27 DEBUG  WindowsBackend: keyboard_id=-268368877
03-06 16:27 DEBUG  WindowsBackend: keyboard_layout=it
03-06 16:27 DEBUG  WindowsBackend: keyboard_variant=
03-06 16:27 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-06 16:27 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-06 16:27 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-06 16:27 DEBUG  CommonBackend: Searching ISOs on USB devices
03-06 16:27 DEBUG  CommonBackend: Searching for local CDs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Ubuntu Netbook Remix CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Kubuntu Netbook CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-06 16:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-06 16:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-06 16:27 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-06 16:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-06 16:27 INFO   Distro: Found a valid CD for Ubuntu: G:\
03-06 16:27 INFO   root: Running the CD menu...
03-06 16:27 DEBUG  WindowsFrontend: __init__...
03-06 16:27 DEBUG  WindowsFrontend: on_init...
03-06 16:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\translations, languages=['nl_NL', 'nl']
03-06 16:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl6C3A.tmp\translations, languages=['nl_NL', 'nl']
03-06 16:27 DEBUG  WindowsFrontend: frontend.on_quit
03-06 16:27 DEBUG  root: application.on_quit
03-06 16:27 INFO   root: sys.exit
03-09 19:35 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 19:35 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 19:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-09 19:35 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\data
03-09 19:35 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\bin\7z.exe
03-09 19:35 DEBUG  CommonBackend: Fetching basic info...
03-09 19:35 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-09 19:35 DEBUG  CommonBackend: platform=win32
03-09 19:35 DEBUG  CommonBackend: osname=nt
03-09 19:35 DEBUG  CommonBackend: language=nl_NL
03-09 19:35 DEBUG  CommonBackend: encoding=cp1252
03-09 19:35 DEBUG  WindowsBackend: arch=amd64
03-09 19:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\data\isolist.ini
03-09 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:35 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:35 DEBUG  WindowsBackend: Fetching host info...
03-09 19:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:35 DEBUG  WindowsBackend: windows version=vista
03-09 19:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:35 DEBUG  WindowsBackend: windows_sp=None
03-09 19:35 DEBUG  WindowsBackend: windows_build=7600
03-09 19:35 DEBUG  WindowsBackend: gmt=1
03-09 19:35 DEBUG  WindowsBackend: country=IT
03-09 19:35 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:35 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:35 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:35 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:35 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:35 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:35 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:35 DEBUG  WindowsBackend: bootloader=vista
03-09 19:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20230.5351563 mb free ntfs)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(C: hd 20230.5351563 mb free ntfs)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
03-09 19:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:35 DEBUG  WindowsBackend: uninstaller_path=None
03-09 19:35 DEBUG  WindowsBackend: previous_target_dir=None
03-09 19:35 DEBUG  WindowsBackend: previous_distro_name=None
03-09 19:35 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:35 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:35 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:35 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-09 19:35 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-09 19:35 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:35 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:35 DEBUG  CommonBackend: Searching for local CDs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Ubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Ubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Kubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Kubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Kubuntu Netbook CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Xubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Xubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Mythbuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp is a valid Mythbuntu CD
03-09 19:35 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:35 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-09 19:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-09 19:35 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 19:35 INFO   root: Running the CD menu...
03-09 19:35 DEBUG  WindowsFrontend: __init__...
03-09 19:35 DEBUG  WindowsFrontend: on_init...
03-09 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:36 INFO   root: CD menu finished
03-09 19:36 INFO   root: Running the installer...
03-09 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:37 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=9000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=pascal
03-09 19:37 INFO   root: Received settings
03-09 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:37 DEBUG  TaskList: # Running tasklist...
03-09 19:37 DEBUG  TaskList: ## Running select_target_dir...
03-09 19:37 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 19:37 DEBUG  TaskList: ## Finished select_target_dir
03-09 19:37 DEBUG  TaskList: ## Running create_dir_structure...
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 19:37 DEBUG  TaskList: ## Finished create_dir_structure
03-09 19:37 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 19:37 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 19:37 DEBUG  TaskList: ## Running create_uninstaller...
03-09 19:37 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 19:37 DEBUG  TaskList: ## Finished create_uninstaller
03-09 19:37 DEBUG  TaskList: ## Running copy_installation_files...
03-09 19:37 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 19:37 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\winboot -> C:\ubuntu\winboot
03-09 19:37 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCDF9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 19:37 DEBUG  TaskList: ## Finished copy_installation_files
03-09 19:37 DEBUG  TaskList: ## Running get_iso...
03-09 19:37 DEBUG  TaskList: New task copy_file
03-09 19:37 DEBUG  TaskList: ### Running copy_file...
03-09 19:37 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 19:37 DEBUG  TaskList: # Cancelling tasklist
03-09 19:37 DEBUG  TaskList: New task check_iso
03-09 19:37 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 19:37 DEBUG  CommonBackend: Searching for local ISO
03-09 19:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 19:37 DEBUG  TaskList: New task get_metalink
03-09 19:37 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-09 19:37 DEBUG  TaskList: # Cancelling tasklist
03-09 19:37 DEBUG  TaskList: # Finished tasklist
03-09 19:37 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 19:37 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 19:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-09 19:37 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\data
03-09 19:37 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\bin\7z.exe
03-09 19:37 DEBUG  CommonBackend: Fetching basic info...
03-09 19:37 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-09 19:37 DEBUG  CommonBackend: platform=win32
03-09 19:37 DEBUG  CommonBackend: osname=nt
03-09 19:37 DEBUG  CommonBackend: language=nl_NL
03-09 19:37 DEBUG  CommonBackend: encoding=cp1252
03-09 19:37 DEBUG  WindowsBackend: arch=amd64
03-09 19:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\data\isolist.ini
03-09 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:37 DEBUG  WindowsBackend: Fetching host info...
03-09 19:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:37 DEBUG  WindowsBackend: windows version=vista
03-09 19:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:37 DEBUG  WindowsBackend: windows_sp=None
03-09 19:37 DEBUG  WindowsBackend: windows_build=7600
03-09 19:37 DEBUG  WindowsBackend: gmt=1
03-09 19:37 DEBUG  WindowsBackend: country=IT
03-09 19:37 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:37 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:37 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:37 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:37 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:37 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:37 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:37 DEBUG  WindowsBackend: bootloader=vista
03-09 19:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20223.6992188 mb free ntfs)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(C: hd 20223.6992188 mb free ntfs)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
03-09 19:37 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:37 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-09 19:37 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-09 19:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 19:37 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:37 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:37 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:37 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-09 19:37 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-09 19:37 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:37 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:37 DEBUG  CommonBackend: Searching for local CDs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu Netbook CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Xubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Xubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Mythbuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Mythbuntu CD
03-09 19:37 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:37 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-09 19:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-09 19:37 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 19:37 INFO   root: Running the CD menu...
03-09 19:37 DEBUG  WindowsFrontend: __init__...
03-09 19:37 DEBUG  WindowsFrontend: on_init...
03-09 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:37 INFO   root: CD menu finished
03-09 19:37 INFO   root: Already installed, running the uninstaller...
03-09 19:37 INFO   root: Running the uninstaller...
03-09 19:37 INFO   CommonBackend: This is the uninstaller running
03-09 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:38 INFO   root: Received settings
03-09 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:38 DEBUG  TaskList: # Running tasklist...
03-09 19:38 DEBUG  TaskList: ## Running Back-up-ISO...
03-09 19:38 DEBUG  TaskList: ## Finished Back-up-ISO
03-09 19:38 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
03-09 19:38 DEBUG  WindowsBackend: Could not find bcd id
03-09 19:38 DEBUG  WindowsBackend: undo_bootini C:
03-09 19:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 20223.6992188 mb free ntfs)
03-09 19:38 DEBUG  WindowsBackend: undo_bootini D:
03-09 19:38 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:38 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
03-09 19:38 DEBUG  TaskList: ## Running Doelmap verwijderen...
03-09 19:38 DEBUG  CommonBackend: Deleting C:\ubuntu
03-09 19:38 DEBUG  TaskList: ## Finished Doelmap verwijderen
03-09 19:38 DEBUG  TaskList: ## Running Registersleutel verwijderen...
03-09 19:38 DEBUG  TaskList: ## Finished Registersleutel verwijderen
03-09 19:38 DEBUG  TaskList: # Finished tasklist
03-09 19:38 INFO   root: Almost finished uninstalling
03-09 19:38 INFO   root: Finished uninstallation
03-09 19:38 DEBUG  CommonBackend: Fetching basic info...
03-09 19:38 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-09 19:38 DEBUG  CommonBackend: platform=win32
03-09 19:38 DEBUG  CommonBackend: osname=nt
03-09 19:38 DEBUG  WindowsBackend: arch=amd64
03-09 19:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\data\isolist.ini
03-09 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:38 DEBUG  WindowsBackend: Fetching host info...
03-09 19:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:38 DEBUG  WindowsBackend: windows version=vista
03-09 19:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:38 DEBUG  WindowsBackend: windows_sp=None
03-09 19:38 DEBUG  WindowsBackend: windows_build=7600
03-09 19:38 DEBUG  WindowsBackend: gmt=1
03-09 19:38 DEBUG  WindowsBackend: country=IT
03-09 19:38 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:38 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:38 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:38 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:38 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:38 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:38 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:38 DEBUG  WindowsBackend: bootloader=vista
03-09 19:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20227.1210938 mb free ntfs)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(C: hd 20227.1210938 mb free ntfs)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
03-09 19:38 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:38 DEBUG  WindowsBackend: uninstaller_path=None
03-09 19:38 DEBUG  WindowsBackend: previous_target_dir=None
03-09 19:38 DEBUG  WindowsBackend: previous_distro_name=None
03-09 19:38 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:38 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:38 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:38 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:38 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:38 DEBUG  CommonBackend: Searching for local CDs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Kubuntu Netbook CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Xubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Xubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Mythbuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp is a valid Mythbuntu CD
03-09 19:38 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:38 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 19:38 INFO   root: Running the installer...
03-09 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=9000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=pascal
03-09 19:39 INFO   root: Received settings
03-09 19:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:39 DEBUG  TaskList: # Running tasklist...
03-09 19:39 DEBUG  TaskList: ## Running select_target_dir...
03-09 19:39 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 19:39 DEBUG  TaskList: ## Finished select_target_dir
03-09 19:39 DEBUG  TaskList: ## Running create_dir_structure...
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 19:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 19:39 DEBUG  TaskList: ## Finished create_dir_structure
03-09 19:39 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 19:39 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 19:39 DEBUG  TaskList: ## Running create_uninstaller...
03-09 19:39 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 19:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 19:39 DEBUG  TaskList: ## Finished create_uninstaller
03-09 19:39 DEBUG  TaskList: ## Running copy_installation_files...
03-09 19:39 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 19:39 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\winboot -> C:\ubuntu\winboot
03-09 19:39 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylCECA.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 19:39 DEBUG  TaskList: ## Finished copy_installation_files
03-09 19:39 DEBUG  TaskList: ## Running get_iso...
03-09 19:39 DEBUG  TaskList: New task copy_file
03-09 19:39 DEBUG  TaskList: ### Running copy_file...
03-09 19:39 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 19:39 DEBUG  TaskList: # Cancelling tasklist
03-09 19:39 DEBUG  TaskList: New task check_iso
03-09 19:39 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-09 19:39 DEBUG  CommonBackend: Searching for local ISO
03-09 19:39 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-09 19:39 DEBUG  TaskList: New task get_metalink
03-09 19:39 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-09 19:39 DEBUG  TaskList: # Cancelling tasklist
03-09 19:39 DEBUG  TaskList: # Finished tasklist
03-09 19:40 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 19:40 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 19:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-09 19:40 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\data
03-09 19:40 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\bin\7z.exe
03-09 19:40 DEBUG  CommonBackend: Fetching basic info...
03-09 19:40 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-09 19:40 DEBUG  CommonBackend: platform=win32
03-09 19:40 DEBUG  CommonBackend: osname=nt
03-09 19:40 DEBUG  CommonBackend: language=nl_NL
03-09 19:40 DEBUG  CommonBackend: encoding=cp1252
03-09 19:40 DEBUG  WindowsBackend: arch=amd64
03-09 19:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\data\isolist.ini
03-09 19:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:40 DEBUG  WindowsBackend: Fetching host info...
03-09 19:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:40 DEBUG  WindowsBackend: windows version=vista
03-09 19:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:40 DEBUG  WindowsBackend: windows_sp=None
03-09 19:40 DEBUG  WindowsBackend: windows_build=7600
03-09 19:40 DEBUG  WindowsBackend: gmt=1
03-09 19:40 DEBUG  WindowsBackend: country=IT
03-09 19:40 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:40 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:40 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:40 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:40 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:40 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:40 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:40 DEBUG  WindowsBackend: bootloader=vista
03-09 19:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20229.1445313 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(C: hd 20229.1445313 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-09 19:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-09 19:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-09 19:40 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:40 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:40 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:40 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-09 19:40 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-09 19:40 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:40 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:40 DEBUG  CommonBackend: Searching for local CDs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu Netbook CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-09 19:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-09 19:40 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 19:40 INFO   root: Running the CD menu...
03-09 19:40 DEBUG  WindowsFrontend: __init__...
03-09 19:40 DEBUG  WindowsFrontend: on_init...
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 INFO   root: CD menu finished
03-09 19:40 INFO   root: Already installed, running the uninstaller...
03-09 19:40 INFO   root: Running the uninstaller...
03-09 19:40 INFO   CommonBackend: This is the uninstaller running
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 INFO   root: Received settings
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 DEBUG  TaskList: # Running tasklist...
03-09 19:40 DEBUG  TaskList: ## Running Back-up-ISO...
03-09 19:40 DEBUG  TaskList: ## Finished Back-up-ISO
03-09 19:40 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
03-09 19:40 DEBUG  WindowsBackend: Could not find bcd id
03-09 19:40 DEBUG  WindowsBackend: undo_bootini C:
03-09 19:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 20229.1445313 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: undo_bootini D:
03-09 19:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:40 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
03-09 19:40 DEBUG  TaskList: ## Running Doelmap verwijderen...
03-09 19:40 DEBUG  CommonBackend: Deleting C:\ubuntu
03-09 19:40 DEBUG  TaskList: ## Finished Doelmap verwijderen
03-09 19:40 DEBUG  TaskList: ## Running Registersleutel verwijderen...
03-09 19:40 DEBUG  TaskList: ## Finished Registersleutel verwijderen
03-09 19:40 DEBUG  TaskList: # Finished tasklist
03-09 19:40 INFO   root: Almost finished uninstalling
03-09 19:40 INFO   root: Finished uninstallation
03-09 19:40 DEBUG  CommonBackend: Fetching basic info...
03-09 19:40 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-09 19:40 DEBUG  CommonBackend: platform=win32
03-09 19:40 DEBUG  CommonBackend: osname=nt
03-09 19:40 DEBUG  WindowsBackend: arch=amd64
03-09 19:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\data\isolist.ini
03-09 19:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:40 DEBUG  WindowsBackend: Fetching host info...
03-09 19:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:40 DEBUG  WindowsBackend: windows version=vista
03-09 19:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:40 DEBUG  WindowsBackend: windows_sp=None
03-09 19:40 DEBUG  WindowsBackend: windows_build=7600
03-09 19:40 DEBUG  WindowsBackend: gmt=1
03-09 19:40 DEBUG  WindowsBackend: country=IT
03-09 19:40 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:40 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:40 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:40 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:40 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:40 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:40 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:40 DEBUG  WindowsBackend: bootloader=vista
03-09 19:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20230.6640625 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(C: hd 20230.6640625 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
03-09 19:40 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:40 DEBUG  WindowsBackend: uninstaller_path=None
03-09 19:40 DEBUG  WindowsBackend: previous_target_dir=None
03-09 19:40 DEBUG  WindowsBackend: previous_distro_name=None
03-09 19:40 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:40 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:40 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:40 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:40 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:40 DEBUG  CommonBackend: Searching for local CDs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Kubuntu Netbook CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:40 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-09 19:40 INFO   root: Running the installer...
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl2B2.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:40 INFO   WindowsFrontend: Operation cancelled
03-09 19:40 DEBUG  WindowsFrontend: frontend.quit
03-09 19:40 DEBUG  WindowsFrontend: frontend.on_quit
03-09 19:40 DEBUG  root: application.on_quit
03-09 19:40 INFO   root: sys.exit
03-09 19:41 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-09 19:41 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-09 19:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
03-09 19:41 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\data
03-09 19:41 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\bin\7z.exe
03-09 19:41 DEBUG  CommonBackend: Fetching basic info...
03-09 19:41 DEBUG  CommonBackend: original_exe=G:\wubi.exe
03-09 19:41 DEBUG  CommonBackend: platform=win32
03-09 19:41 DEBUG  CommonBackend: osname=nt
03-09 19:41 DEBUG  CommonBackend: language=nl_NL
03-09 19:41 DEBUG  CommonBackend: encoding=cp1252
03-09 19:41 DEBUG  WindowsBackend: arch=amd64
03-09 19:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\data\isolist.ini
03-09 19:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-09 19:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-09 19:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-09 19:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-09 19:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-09 19:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-09 19:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-09 19:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-09 19:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-09 19:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-09 19:41 DEBUG  WindowsBackend: Fetching host info...
03-09 19:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-09 19:41 DEBUG  WindowsBackend: windows version=vista
03-09 19:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-09 19:41 DEBUG  WindowsBackend: windows_sp=None
03-09 19:41 DEBUG  WindowsBackend: windows_build=7600
03-09 19:41 DEBUG  WindowsBackend: gmt=1
03-09 19:41 DEBUG  WindowsBackend: country=IT
03-09 19:41 DEBUG  WindowsBackend: timezone=Europe/Rome
03-09 19:41 DEBUG  WindowsBackend: windows_username=Pascal
03-09 19:41 DEBUG  WindowsBackend: user_full_name=Pascal
03-09 19:41 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-09 19:41 DEBUG  WindowsBackend: windows_language_code=1043
03-09 19:41 DEBUG  WindowsBackend: windows_language=Dutch
03-09 19:41 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-09 19:41 DEBUG  WindowsBackend: bootloader=vista
03-09 19:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20313.2304688 mb free ntfs)
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(C: hd 20313.2304688 mb free ntfs)
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-09 19:41 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-09 19:41 DEBUG  WindowsBackend: uninstaller_path=None
03-09 19:41 DEBUG  WindowsBackend: previous_target_dir=None
03-09 19:41 DEBUG  WindowsBackend: previous_distro_name=None
03-09 19:41 DEBUG  WindowsBackend: keyboard_id=-268368877
03-09 19:41 DEBUG  WindowsBackend: keyboard_layout=it
03-09 19:41 DEBUG  WindowsBackend: keyboard_variant=
03-09 19:41 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-09 19:41 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-09 19:41 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-09 19:41 DEBUG  CommonBackend: Searching ISOs on USB devices
03-09 19:41 DEBUG  CommonBackend: Searching for local CDs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Ubuntu Netbook Remix CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Kubuntu Netbook CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-09 19:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-09 19:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-09 19:41 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-09 19:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-09 19:41 INFO   Distro: Found a valid CD for Ubuntu: G:\
03-09 19:41 INFO   root: Running the CD menu...
03-09 19:41 DEBUG  WindowsFrontend: __init__...
03-09 19:41 DEBUG  WindowsFrontend: on_init...
03-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:41 INFO   root: CD menu finished
03-09 19:41 INFO   root: Running the installer...
03-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=9000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=pascal
03-09 19:42 INFO   root: Received settings
03-09 19:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:42 DEBUG  TaskList: # Running tasklist...
03-09 19:42 DEBUG  TaskList: ## Running select_target_dir...
03-09 19:42 INFO   WindowsBackend: Installing into C:\ubuntu
03-09 19:42 DEBUG  TaskList: ## Finished select_target_dir
03-09 19:42 DEBUG  TaskList: ## Running create_dir_structure...
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-09 19:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-09 19:42 DEBUG  TaskList: ## Finished create_dir_structure
03-09 19:42 DEBUG  TaskList: ## Running uncompress_target_dir...
03-09 19:42 DEBUG  TaskList: ## Finished uncompress_target_dir
03-09 19:42 DEBUG  TaskList: ## Running create_uninstaller...
03-09 19:42 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-09 19:42 DEBUG  TaskList: ## Finished create_uninstaller
03-09 19:42 DEBUG  TaskList: ## Running copy_installation_files...
03-09 19:42 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-09 19:42 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\winboot -> C:\ubuntu\winboot
03-09 19:42 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-09 19:42 DEBUG  TaskList: ## Finished copy_installation_files
03-09 19:42 DEBUG  TaskList: ## Running get_iso...
03-09 19:42 DEBUG  TaskList: New task copy_file
03-09 19:42 DEBUG  TaskList: ### Running copy_file...
03-09 19:42 DEBUG  TaskList: ### Finished copy_file
03-09 19:42 DEBUG  TaskList: New task check_iso
03-09 19:42 DEBUG  TaskList: ### Running check_iso...
03-09 19:42 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-09 19:42 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-09 19:42 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-09 19:42 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
03-09 19:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
03-09 19:42 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-09 19:42 DEBUG  TaskList: New task get_metalink
03-09 19:42 DEBUG  TaskList: #### Running get_metalink...
03-09 19:42 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
03-09 19:42 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
03-09 19:42 DEBUG  downloader: download finished (read 26651 bytes)
03-09 19:42 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
03-09 19:42 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-09 19:42 DEBUG  downloader: download finished (read 562 bytes)
03-09 19:42 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-09 19:42 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-09 19:42 DEBUG  downloader: download finished (read 189 bytes)
03-09 19:42 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-09 19:42 INFO   saplog: Checking block bindings..
03-09 19:42 INFO   saplog: Key verified successfully.
03-09 19:42 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-09 19:42 DEBUG  TaskList: #### Finished get_metalink
03-09 19:42 DEBUG  TaskList: New task get_file_md5
03-09 19:42 DEBUG  TaskList: #### Running get_file_md5...
03-09 19:42 DEBUG  TaskList: #### Finished get_file_md5
03-09 19:42 DEBUG  TaskList: ### Finished check_iso
03-09 19:42 DEBUG  TaskList: ## Finished get_iso
03-09 19:42 DEBUG  TaskList: ## Running extract_kernel...
03-09 19:42 DEBUG  CommonBackend: Copying files from CD G:\
03-09 19:42 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-09 19:42 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
03-09 19:42 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
03-09 19:42 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
03-09 19:42 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
03-09 19:42 DEBUG  TaskList: ## Finished extract_kernel
03-09 19:42 DEBUG  TaskList: ## Running choose_disk_sizes...
03-09 19:42 DEBUG  WindowsBackend: total size=9000
  root=8744
  swap=256
  home=0
  usr=0
03-09 19:42 DEBUG  TaskList: ## Finished choose_disk_sizes
03-09 19:42 DEBUG  TaskList: ## Running create_preseed...
03-09 19:42 DEBUG  TaskList: ## Finished create_preseed
03-09 19:42 DEBUG  TaskList: ## Running modify_bootloader...
03-09 19:42 DEBUG  TaskList: New task modify_bcd
03-09 19:42 DEBUG  TaskList: ### Running modify_bcd...
03-09 19:42 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20313.2304688 mb free ntfs)
03-09 19:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {9fb1fe8a-0f16-11df-b786-e8fc26988c24}
03-09 19:42 DEBUG  TaskList: ### Finished modify_bcd
03-09 19:42 DEBUG  TaskList: New task modify_bcd
03-09 19:42 DEBUG  TaskList: ### Running modify_bcd...
03-09 19:42 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 19052.1757813 mb free ntfs)
03-09 19:42 DEBUG  WindowsBackend: BCD has already been modified
03-09 19:42 DEBUG  TaskList: ### Finished modify_bcd
03-09 19:42 DEBUG  TaskList: ## Finished modify_bootloader
03-09 19:42 DEBUG  TaskList: ## Running modify_grub_configuration...
03-09 19:42 DEBUG  TaskList: ## Finished modify_grub_configuration
03-09 19:42 DEBUG  TaskList: ## Running create_virtual_disks...
03-09 19:42 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 8744MB
03-09 19:42 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
03-09 19:42 DEBUG  TaskList: ## Finished create_virtual_disks
03-09 19:42 DEBUG  TaskList: ## Running uncompress_files...
03-09 19:42 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
03-09 19:42 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
03-09 19:42 DEBUG  TaskList: ## Finished uncompress_files
03-09 19:42 DEBUG  TaskList: ## Running eject_cd...
03-09 19:42 DEBUG  TaskList: ## Finished eject_cd
03-09 19:42 DEBUG  TaskList: # Finished tasklist
03-09 19:42 INFO   root: Almost finished installing
03-09 19:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl3362.tmp\translations, languages=['nl_NL', 'nl']
03-09 19:43 INFO   root: Finished installation
03-09 19:43 INFO   root: Rebooting
03-09 19:43 DEBUG  TaskList: # Running tasklist...
03-09 19:43 DEBUG  TaskList: ## Running reboot...
03-09 19:43 DEBUG  TaskList: ## Finished reboot
03-09 19:43 DEBUG  TaskList: # Finished tasklist
03-09 19:43 DEBUG  root: application.quit
03-09 19:43 DEBUG  WindowsFrontend: frontend.quit
03-09 19:43 DEBUG  WindowsFrontend: frontend.on_quit
03-09 19:43 DEBUG  root: application.on_quit
03-09 19:43 INFO   root: sys.exit
03-14 11:50 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-14 11:50 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-14 11:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pascal\\Desktop\\wubi.exe"']
03-14 11:50 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\data
03-14 11:50 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\bin\7z.exe
03-14 11:50 DEBUG  CommonBackend: Fetching basic info...
03-14 11:50 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:50 DEBUG  CommonBackend: platform=win32
03-14 11:50 DEBUG  CommonBackend: osname=nt
03-14 11:50 DEBUG  CommonBackend: language=nl_NL
03-14 11:50 DEBUG  CommonBackend: encoding=cp1252
03-14 11:50 DEBUG  WindowsBackend: arch=amd64
03-14 11:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\data\isolist.ini
03-14 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:50 DEBUG  WindowsBackend: Fetching host info...
03-14 11:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:50 DEBUG  WindowsBackend: windows version=vista
03-14 11:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:50 DEBUG  WindowsBackend: windows_sp=None
03-14 11:50 DEBUG  WindowsBackend: windows_build=7600
03-14 11:50 DEBUG  WindowsBackend: gmt=1
03-14 11:50 DEBUG  WindowsBackend: country=IT
03-14 11:50 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:50 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:50 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:50 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:50 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:50 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:50 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:50 DEBUG  WindowsBackend: bootloader=vista
03-14 11:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9426.234375 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(C: hd 9426.234375 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-14 11:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-14 11:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-14 11:50 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:50 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:50 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:50 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-14 11:50 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-14 11:50 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:50 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:50 DEBUG  CommonBackend: Searching for local CDs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Kubuntu Netbook CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:50 INFO   root: Running the CD menu...
03-14 11:50 DEBUG  WindowsFrontend: __init__...
03-14 11:50 DEBUG  WindowsFrontend: on_init...
03-14 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:50 INFO   root: CD menu finished
03-14 11:50 INFO   root: Already installed, running the uninstaller...
03-14 11:50 INFO   root: Running the uninstaller...
03-14 11:50 INFO   CommonBackend: This is the uninstaller running
03-14 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylCDBE.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:50 INFO   WindowsFrontend: Operation cancelled
03-14 11:50 DEBUG  WindowsFrontend: frontend.quit
03-14 11:50 DEBUG  WindowsFrontend: frontend.on_quit
03-14 11:50 DEBUG  root: application.on_quit
03-14 11:50 INFO   root: sys.exit
03-14 11:50 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-14 11:50 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-14 11:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pascal\\Desktop\\wubi.exe"']
03-14 11:50 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\data
03-14 11:50 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\bin\7z.exe
03-14 11:50 DEBUG  CommonBackend: Fetching basic info...
03-14 11:50 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:50 DEBUG  CommonBackend: platform=win32
03-14 11:50 DEBUG  CommonBackend: osname=nt
03-14 11:50 DEBUG  CommonBackend: language=nl_NL
03-14 11:50 DEBUG  CommonBackend: encoding=cp1252
03-14 11:50 DEBUG  WindowsBackend: arch=amd64
03-14 11:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\data\isolist.ini
03-14 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:50 DEBUG  WindowsBackend: Fetching host info...
03-14 11:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:50 DEBUG  WindowsBackend: windows version=vista
03-14 11:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:50 DEBUG  WindowsBackend: windows_sp=None
03-14 11:50 DEBUG  WindowsBackend: windows_build=7600
03-14 11:50 DEBUG  WindowsBackend: gmt=1
03-14 11:50 DEBUG  WindowsBackend: country=IT
03-14 11:50 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:50 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:50 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:50 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:50 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:50 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:50 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:50 DEBUG  WindowsBackend: bootloader=vista
03-14 11:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9426.0703125 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(C: hd 9426.0703125 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-14 11:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-14 11:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-14 11:50 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:50 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:50 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:50 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-14 11:50 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-14 11:50 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:50 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:50 DEBUG  CommonBackend: Searching for local CDs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Kubuntu Netbook CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:50 INFO   root: Running the CD menu...
03-14 11:50 DEBUG  WindowsFrontend: __init__...
03-14 11:50 DEBUG  WindowsFrontend: on_init...
03-14 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl4B0C.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:50 INFO   WindowsFrontend: Operation cancelled
03-14 11:50 DEBUG  WindowsFrontend: frontend.quit
03-14 11:50 DEBUG  WindowsFrontend: frontend.on_quit
03-14 11:50 DEBUG  root: application.on_quit
03-14 11:50 INFO   root: sys.exit
03-14 11:52 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-14 11:52 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-14 11:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pascal\\Desktop\\wubi.exe"']
03-14 11:52 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\data
03-14 11:52 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\bin\7z.exe
03-14 11:52 DEBUG  CommonBackend: Fetching basic info...
03-14 11:52 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:52 DEBUG  CommonBackend: platform=win32
03-14 11:52 DEBUG  CommonBackend: osname=nt
03-14 11:52 DEBUG  CommonBackend: language=nl_NL
03-14 11:52 DEBUG  CommonBackend: encoding=cp1252
03-14 11:52 DEBUG  WindowsBackend: arch=amd64
03-14 11:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\data\isolist.ini
03-14 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:52 DEBUG  WindowsBackend: Fetching host info...
03-14 11:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:52 DEBUG  WindowsBackend: windows version=vista
03-14 11:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:52 DEBUG  WindowsBackend: windows_sp=None
03-14 11:52 DEBUG  WindowsBackend: windows_build=7600
03-14 11:52 DEBUG  WindowsBackend: gmt=1
03-14 11:52 DEBUG  WindowsBackend: country=IT
03-14 11:52 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:52 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:52 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:52 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:52 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:52 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:52 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:52 DEBUG  WindowsBackend: bootloader=vista
03-14 11:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9425.4453125 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(C: hd 9425.4453125 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-14 11:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-14 11:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-14 11:52 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:52 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:52 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:52 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-14 11:52 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-14 11:52 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:52 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:52 DEBUG  CommonBackend: Searching for local CDs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu Netbook CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:52 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:52 INFO   root: Running the CD menu...
03-14 11:52 DEBUG  WindowsFrontend: __init__...
03-14 11:52 DEBUG  WindowsFrontend: on_init...
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 INFO   root: CD menu finished
03-14 11:52 INFO   root: Already installed, running the uninstaller...
03-14 11:52 INFO   root: Running the uninstaller...
03-14 11:52 INFO   CommonBackend: This is the uninstaller running
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 INFO   root: Received settings
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 DEBUG  TaskList: # Running tasklist...
03-14 11:52 DEBUG  TaskList: ## Running Back-up-ISO...
03-14 11:52 DEBUG  TaskList: ## Finished Back-up-ISO
03-14 11:52 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
03-14 11:52 DEBUG  WindowsBackend: Removing bcd entry {9fb1fe8a-0f16-11df-b786-e8fc26988c24}
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
03-14 11:52 DEBUG  WindowsBackend: undo_bootini C:
03-14 11:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 9425.4453125 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: undo_bootini D:
03-14 11:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:52 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
03-14 11:52 DEBUG  TaskList: ## Running Doelmap verwijderen...
03-14 11:52 DEBUG  CommonBackend: Deleting C:\ubuntu
03-14 11:52 DEBUG  TaskList: ## Finished Doelmap verwijderen
03-14 11:52 DEBUG  TaskList: ## Running Registersleutel verwijderen...
03-14 11:52 DEBUG  TaskList: ## Finished Registersleutel verwijderen
03-14 11:52 DEBUG  TaskList: # Finished tasklist
03-14 11:52 INFO   root: Almost finished uninstalling
03-14 11:52 INFO   root: Finished uninstallation
03-14 11:52 DEBUG  CommonBackend: Fetching basic info...
03-14 11:52 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:52 DEBUG  CommonBackend: platform=win32
03-14 11:52 DEBUG  CommonBackend: osname=nt
03-14 11:52 DEBUG  WindowsBackend: arch=amd64
03-14 11:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\data\isolist.ini
03-14 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:52 DEBUG  WindowsBackend: Fetching host info...
03-14 11:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:52 DEBUG  WindowsBackend: windows version=vista
03-14 11:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:52 DEBUG  WindowsBackend: windows_sp=None
03-14 11:52 DEBUG  WindowsBackend: windows_build=7600
03-14 11:52 DEBUG  WindowsBackend: gmt=1
03-14 11:52 DEBUG  WindowsBackend: country=IT
03-14 11:52 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:52 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:52 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:52 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:52 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:52 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:52 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:52 DEBUG  WindowsBackend: bootloader=vista
03-14 11:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10117.8085938 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(C: hd 10117.8085938 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:52 DEBUG  WindowsBackend: uninstaller_path=None
03-14 11:52 DEBUG  WindowsBackend: previous_target_dir=None
03-14 11:52 DEBUG  WindowsBackend: previous_distro_name=None
03-14 11:52 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:52 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:52 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:52 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:52 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:52 DEBUG  CommonBackend: Searching for local CDs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Kubuntu Netbook CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:52 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:52 INFO   root: Running the installer...
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=4000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=pascal
03-14 11:52 INFO   root: Received settings
03-14 11:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:52 DEBUG  TaskList: # Running tasklist...
03-14 11:52 DEBUG  TaskList: ## Running select_target_dir...
03-14 11:52 INFO   WindowsBackend: Installing into C:\ubuntu
03-14 11:52 DEBUG  TaskList: ## Finished select_target_dir
03-14 11:52 DEBUG  TaskList: ## Running create_dir_structure...
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-14 11:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-14 11:52 DEBUG  TaskList: ## Finished create_dir_structure
03-14 11:52 DEBUG  TaskList: ## Running uncompress_target_dir...
03-14 11:52 DEBUG  TaskList: ## Finished uncompress_target_dir
03-14 11:52 DEBUG  TaskList: ## Running create_uninstaller...
03-14 11:52 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Pascal\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-14 11:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-14 11:52 DEBUG  TaskList: ## Finished create_uninstaller
03-14 11:52 DEBUG  TaskList: ## Running copy_installation_files...
03-14 11:52 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-14 11:52 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\winboot -> C:\ubuntu\winboot
03-14 11:52 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylDD84.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-14 11:52 DEBUG  TaskList: ## Finished copy_installation_files
03-14 11:52 DEBUG  TaskList: ## Running get_iso...
03-14 11:52 DEBUG  TaskList: New task copy_file
03-14 11:52 DEBUG  TaskList: ### Running copy_file...
03-14 11:55 DEBUG  TaskList: ### Finished copy_file
03-14 11:55 DEBUG  TaskList: New task check_iso
03-14 11:55 DEBUG  TaskList: ### Running check_iso...
03-14 11:55 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
03-14 11:55 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
03-14 11:55 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
03-14 11:55 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:55 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
03-14 11:55 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
03-14 11:55 DEBUG  TaskList: New task get_metalink
03-14 11:55 DEBUG  TaskList: #### Running get_metalink...
03-14 11:55 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink > C:\ubuntu\install
03-14 11:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
03-14 11:55 DEBUG  downloader: download finished (read 26455 bytes)
03-14 11:55 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
03-14 11:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-14 11:55 DEBUG  downloader: download finished (read 562 bytes)
03-14 11:55 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
03-14 11:55 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-14 11:55 DEBUG  downloader: download finished (read 189 bytes)
03-14 11:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-14 11:55 INFO   saplog: Checking block bindings..
03-14 11:55 INFO   saplog: Key verified successfully.
03-14 11:55 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-14 11:55 DEBUG  TaskList: #### Finished get_metalink
03-14 11:55 DEBUG  TaskList: New task get_file_md5
03-14 11:55 DEBUG  TaskList: #### Running get_file_md5...
03-14 11:55 DEBUG  TaskList: #### Finished get_file_md5
03-14 11:55 DEBUG  TaskList: ### Finished check_iso
03-14 11:55 DEBUG  TaskList: ## Finished get_iso
03-14 11:55 DEBUG  TaskList: ## Running extract_kernel...
03-14 11:55 DEBUG  CommonBackend: Copying files from CD E:\
03-14 11:56 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 508, in extract_kernel
  File "\lib\shutil.py", line 72, in copy
  File "\lib\shutil.py", line 40, in copyfile
  File "\lib\shutil.py", line 22, in copyfileobj
IOError: [Errno 13] Permission denied
03-14 11:56 DEBUG  TaskList: # Cancelling tasklist
03-14 11:56 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 508, in extract_kernel
  File "\lib\shutil.py", line 72, in copy
  File "\lib\shutil.py", line 40, in copyfile
  File "\lib\shutil.py", line 22, in copyfileobj
IOError: [Errno 13] Permission denied
03-14 11:56 DEBUG  TaskList: # Finished tasklist
03-14 11:56 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-14 11:56 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-14 11:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pascal\\Desktop\\wubi.exe"']
03-14 11:56 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\data
03-14 11:56 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\bin\7z.exe
03-14 11:56 DEBUG  CommonBackend: Fetching basic info...
03-14 11:56 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:56 DEBUG  CommonBackend: platform=win32
03-14 11:56 DEBUG  CommonBackend: osname=nt
03-14 11:56 DEBUG  CommonBackend: language=nl_NL
03-14 11:56 DEBUG  CommonBackend: encoding=cp1252
03-14 11:56 DEBUG  WindowsBackend: arch=amd64
03-14 11:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\data\isolist.ini
03-14 11:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:56 DEBUG  WindowsBackend: Fetching host info...
03-14 11:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:56 DEBUG  WindowsBackend: windows version=vista
03-14 11:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:56 DEBUG  WindowsBackend: windows_sp=None
03-14 11:56 DEBUG  WindowsBackend: windows_build=7600
03-14 11:56 DEBUG  WindowsBackend: gmt=1
03-14 11:56 DEBUG  WindowsBackend: country=IT
03-14 11:56 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:56 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:56 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:56 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:56 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:56 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:56 DEBUG  WindowsBackend: bootloader=vista
03-14 11:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9420.58203125 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(C: hd 9420.58203125 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-14 11:56 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-14 11:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-14 11:56 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:56 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:56 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:56 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-14 11:56 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-14 11:56 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:56 DEBUG  CommonBackend: Searching for local CDs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Kubuntu Netbook CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:56 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:56 INFO   root: Running the CD menu...
03-14 11:56 DEBUG  WindowsFrontend: __init__...
03-14 11:56 DEBUG  WindowsFrontend: on_init...
03-14 11:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pyl79F4.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:56 DEBUG  WindowsFrontend: frontend.on_quit
03-14 11:56 DEBUG  root: application.on_quit
03-14 11:56 INFO   root: sys.exit
03-14 11:56 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-14 11:56 DEBUG  root: Logfile is c:\users\pascal\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
03-14 11:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pascal\\Desktop\\wubi.exe"']
03-14 11:56 DEBUG  CommonBackend: data_dir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\data
03-14 11:56 DEBUG  WindowsBackend: 7z=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\bin\7z.exe
03-14 11:56 DEBUG  CommonBackend: Fetching basic info...
03-14 11:56 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:56 DEBUG  CommonBackend: platform=win32
03-14 11:56 DEBUG  CommonBackend: osname=nt
03-14 11:56 DEBUG  CommonBackend: language=nl_NL
03-14 11:56 DEBUG  CommonBackend: encoding=cp1252
03-14 11:56 DEBUG  WindowsBackend: arch=amd64
03-14 11:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\data\isolist.ini
03-14 11:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:56 DEBUG  WindowsBackend: Fetching host info...
03-14 11:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:56 DEBUG  WindowsBackend: windows version=vista
03-14 11:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:56 DEBUG  WindowsBackend: windows_sp=None
03-14 11:56 DEBUG  WindowsBackend: windows_build=7600
03-14 11:56 DEBUG  WindowsBackend: gmt=1
03-14 11:56 DEBUG  WindowsBackend: country=IT
03-14 11:56 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:56 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:56 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:56 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:56 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:56 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:56 DEBUG  WindowsBackend: bootloader=vista
03-14 11:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9419.953125 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(C: hd 9419.953125 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:56 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-14 11:56 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-14 11:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-14 11:56 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:56 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:56 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:56 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
03-14 11:56 DEBUG  CommonBackend: locale=nl_NL.UTF-8
03-14 11:56 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:56 DEBUG  CommonBackend: Searching for local CDs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu Netbook CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:56 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
03-14 11:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-14 11:56 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:56 INFO   root: Running the CD menu...
03-14 11:56 DEBUG  WindowsFrontend: __init__...
03-14 11:56 DEBUG  WindowsFrontend: on_init...
03-14 11:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 INFO   root: CD menu finished
03-14 11:57 INFO   root: Already installed, running the uninstaller...
03-14 11:57 INFO   root: Running the uninstaller...
03-14 11:57 INFO   CommonBackend: This is the uninstaller running
03-14 11:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 INFO   root: Received settings
03-14 11:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 DEBUG  TaskList: # Running tasklist...
03-14 11:57 DEBUG  TaskList: ## Running Back-up-ISO...
03-14 11:57 DEBUG  TaskList: ## Finished Back-up-ISO
03-14 11:57 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
03-14 11:57 DEBUG  WindowsBackend: Could not find bcd id
03-14 11:57 DEBUG  WindowsBackend: undo_bootini C:
03-14 11:57 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 9419.953125 mb free ntfs)
03-14 11:57 DEBUG  WindowsBackend: undo_bootini D:
03-14 11:57 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:57 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
03-14 11:57 DEBUG  TaskList: ## Running Doelmap verwijderen...
03-14 11:57 DEBUG  CommonBackend: Deleting C:\ubuntu
03-14 11:57 DEBUG  TaskList: ## Finished Doelmap verwijderen
03-14 11:57 DEBUG  TaskList: ## Running Registersleutel verwijderen...
03-14 11:57 DEBUG  TaskList: ## Finished Registersleutel verwijderen
03-14 11:57 DEBUG  TaskList: # Finished tasklist
03-14 11:57 INFO   root: Almost finished uninstalling
03-14 11:57 INFO   root: Finished uninstallation
03-14 11:57 DEBUG  CommonBackend: Fetching basic info...
03-14 11:57 DEBUG  CommonBackend: original_exe=C:\Users\Pascal\Desktop\wubi.exe
03-14 11:57 DEBUG  CommonBackend: platform=win32
03-14 11:57 DEBUG  CommonBackend: osname=nt
03-14 11:57 DEBUG  WindowsBackend: arch=amd64
03-14 11:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\data\isolist.ini
03-14 11:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-14 11:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-14 11:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-14 11:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-14 11:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-14 11:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-14 11:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-14 11:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-14 11:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-14 11:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-14 11:57 DEBUG  WindowsBackend: Fetching host info...
03-14 11:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-14 11:57 DEBUG  WindowsBackend: windows version=vista
03-14 11:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-14 11:57 DEBUG  WindowsBackend: windows_sp=None
03-14 11:57 DEBUG  WindowsBackend: windows_build=7600
03-14 11:57 DEBUG  WindowsBackend: gmt=1
03-14 11:57 DEBUG  WindowsBackend: country=IT
03-14 11:57 DEBUG  WindowsBackend: timezone=Europe/Rome
03-14 11:57 DEBUG  WindowsBackend: windows_username=Pascal
03-14 11:57 DEBUG  WindowsBackend: user_full_name=Pascal
03-14 11:57 DEBUG  WindowsBackend: user_directory=C:\Users\Pascal
03-14 11:57 DEBUG  WindowsBackend: windows_language_code=1043
03-14 11:57 DEBUG  WindowsBackend: windows_language=Dutch
03-14 11:57 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 4000+
03-14 11:57 DEBUG  WindowsBackend: bootloader=vista
03-14 11:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 10111.4765625 mb free ntfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(C: hd 10111.4765625 mb free ntfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(D: hd 52462.09375 mb free ntfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
03-14 11:57 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
03-14 11:57 DEBUG  WindowsBackend: uninstaller_path=None
03-14 11:57 DEBUG  WindowsBackend: previous_target_dir=None
03-14 11:57 DEBUG  WindowsBackend: previous_distro_name=None
03-14 11:57 DEBUG  WindowsBackend: keyboard_id=-268368877
03-14 11:57 DEBUG  WindowsBackend: keyboard_layout=it
03-14 11:57 DEBUG  WindowsBackend: keyboard_variant=
03-14 11:57 DEBUG  WindowsBackend: total_memory_mb=2047.3046875
03-14 11:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-14 11:57 DEBUG  CommonBackend: Searching for local CDs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Ubuntu Netbook Remix CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Kubuntu Netbook CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Xubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Xubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Mythbuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp is a valid Mythbuntu CD
03-14 11:57 DEBUG  Distro:     does not contain C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-14 11:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-14 11:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-14 11:57 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-14 11:57 INFO   root: Running the installer...
03-14 11:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=nl_NL, locale=nl_NL.UTF-8, username=pascal
03-14 11:57 INFO   root: Received settings
03-14 11:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\translations, languages=['nl_NL', 'nl']
03-14 11:57 DEBUG  TaskList: # Running tasklist...
03-14 11:57 DEBUG  TaskList: ## Running select_target_dir...
03-14 11:57 INFO   WindowsBackend: Installing into C:\ubuntu
03-14 11:57 DEBUG  TaskList: ## Finished select_target_dir
03-14 11:57 DEBUG  TaskList: ## Running create_dir_structure...
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-14 11:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-14 11:57 DEBUG  TaskList: ## Finished create_dir_structure
03-14 11:57 DEBUG  TaskList: ## Running uncompress_target_dir...
03-14 11:57 DEBUG  TaskList: ## Finished uncompress_target_dir
03-14 11:57 DEBUG  TaskList: ## Running create_uninstaller...
03-14 11:57 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Pascal\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-14 11:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-14 11:57 DEBUG  TaskList: ## Finished create_uninstaller
03-14 11:57 DEBUG  TaskList: ## Running copy_installation_files...
03-14 11:57 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-14 11:57 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\winboot -> C:\ubuntu\winboot
03-14 11:57 DEBUG  WindowsBackend: Copying C:\Users\Pascal\AppData\Local\Temp\pylA9B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-14 11:57 DEBUG  TaskList: ## Finished copy_installation_files
03-14 11:57 DEBUG  TaskList: ## Running get_iso...
03-14 11:57 DEBUG  TaskList: New task copy_file
03-14 11:57 DEBUG  TaskList: ### Running copy_file...
03-14 11:57 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-14 11:57 DEBUG  TaskList: # Cancelling tasklist
03-14 11:57 DEBUG  TaskList: New task check_iso
03-14 11:57 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
03-14 11:57 DEBUG  CommonBackend: Searching for local ISO
03-14 11:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-14 11:57 DEBUG  TaskList: New task get_metalink
03-14 11:57 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-14 11:57 DEBUG  TaskList: # Cancelling tasklist
03-14 11:57 DEBUG  TaskList: # Finished tasklist
```

---

### Post by failmerc on 2010-03-14
I read that it might be a CD problem. I'm trying another now, I'll keep you informed.

---

### Post by failmerc on 2010-03-14
Alright I have reinstalled Ubuntu 9.10. Figured it would be much faster. Thanks for the help.

---

### Post by failmerc on 2010-03-14
The only problem I have now is that it didn't restore my space back... it says 34.10gb is used from the total 38.34gb... while before I had 5gb on both Windows and Linux left to make sure there would be enough... now there's just 4.24gb left in total. Any idea how to fix that? :?

---

### Post by failmerc on 2010-03-14
I think I'll just uninstall Ubuntu for now... tried to upgrade to 10.04 and now I can't get into Ubuntu again because the installer was stuck on halfways the entire day. I'll try again in April when 10.04 releases and hope I have more luck. :(

---

