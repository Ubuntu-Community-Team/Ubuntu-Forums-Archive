---
title: "Dual booting Windows (Vista or Win7) &amp; Ubuntu 9.10 from same SATA drive?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Nightstrike2009 on 2010-03-02
Hello everyone,

I can dual-boot on my PC by using my SATA drive for Windows & a second IDE (PATA) one for Ubuntu.

However when I try to install both OS's on the Primary SATA drive side by side only one is detected (and I have no option to boot the other).

I have a friend with the same problem who is trying to boot Win7 and Ubuntu off the same SATA drive and the same issue occurs on his (He doesn't have the second drive as an option as I do).

Does anyone know a way to get side by side installation to work on one (SATA) drive? Failing this is it possible to boot Ubuntu off and External hard drive and still be able to dual boot Windows & Ubuntu?

---

### Post by darkod on 2010-03-02
I hate blaming you (or your friend) but there must be a reason for this. I am dual booting on single SATA disk win7 and karmic with no issues at all ever since karmic was released.

This information is not nearly enough to try to figure it out. Did you run the boot info script to try and make your dual boot work from the same disk? Can your friend run the script and provide the results?

It also depends how you are trying the side-by-side install. Using the ubuntu installer option is nice and easy, but it needs to shrink the windows partition and install ubuntu in one single step. In that case windows doesn't have chance to reboot few times after the shrink and it can be problematic because of that.

So, the best way is to use Disk Management in vista/7 and shrink the windows partition, boot windows few times, and then install ubuntu into the unallocated space on the hdd created by the shrinking.

PS. One more note. Ubuntu will work just fine dual booting, either on the same disk or on multiple disks. Of course, as with any technology, any hardware, any OS, there might be situations where things don't work out at first and need some tweaking, or don't work out at all even with tweaking. I hope your cases are not one of those. :)

---

### Post by ubunterooster on 2010-03-02
Did you install ubuntu second, allowing it to overwrite the MBR?

---

### Post by Nightstrike2009 on 2010-03-02
Thanks Darkod,

I have tried this: > **By Darkod**It also depends how you are trying the side-by-side install. Using the ubuntu installer option is nice and easy, but it needs to shrink the windows partition and install ubuntu in one single step. In that case windows doesn't have chance to reboot few times after the shrink and it can be problematic because of that.

So, the best way is to use Disk Management in vista/7 and shrink the windows partition, boot windows few times, and then install ubuntu into the unallocated space on the hdd created by the shrinking.

But I/We end up with either Windows or Ubuntu taking over with no option to boot the other.

> **By Darkod:**This information is not nearly enough to try to figure it out. Did you run the boot info script to try and make your dual boot work from the same disk? Can your friend run the script and provide the results?

I have no idea what the boot info script is, I can get around the issue by using my second hard disk, but my friend doesn't have that luxury (& I would like to use them on same SATA drive too).

I have posted because my Ubuntu know how is probably higher, but I too am newish to Ubuntu (If you call Ubuntu 7.04 new)

> **By Ubunterooster:** Did you install ubuntu second, allowing it to overwrite the MBR?

The answer to that is yes my friend, we tend to install windows first, then ubuntu as this allows grub to load rather than being wiped out by the windows MBR. The way we install is via Ubuntu Live Cd and "Install side by side" on the partitioner menu. (Well my friend does anyhow)

Thanks for trying to help out though, any help on this matter is gratefully recieved. :-)

---

### Post by darkod on 2010-03-02
> **Nightstrike2009 said:**
> Thanks Darkrod,

I have tried this: 

But I/We end up with either Windows or Ubuntu taking over with no option to boot the other.


If windows bootloader is on the MBR then you can't expect to see an option for ubuntu, you are probably aware of that. There are ways to chainload but even for that you need to have grub2 installed on the ubuntu partition itself. I don't like and don't recommend this approach personally.

If grub/grub2 is on the MBR. For grub1 the adding to the menu.lst is not automatic I believe. Especially if windows was installed/upgraded after ubuntu. For grub2 also you need to run update-grub.

The boot info script can be downloaded from the link in my signature. You can run it if interested, it will show quite useful information. You don't have to post the results file.
And simple instructions are here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Your friend could run it either from the hdd ubuntu (if he can boot it) or from the live desktop. Just make sure the live desktop gives internet connection. For wired connections in most cases it would.
And it's best to run the script after the ubuntu install so we can see the situation with ubuntu also on the hdd, not just windows. It's rather pointless with only windows.

---

### Post by Nightstrike2009 on 2010-03-02
My Ubuntu is 9.10 so I have Grub2, I have modem connection issues (Vodafone modem on 9.10 requires "Wvdial" or manual network-manager settings) so I have to patch after installation and is not available straight after install for this reason, it does work on Live CD though (9.04 had no such issues but kernel upgrade in 9.10 borked it).

I personally have followed advice on how to chain load but with no success (Probably down to my lack of technical boot experience with Ubuntu) 

> **By Myself:**Failing this is it possible to boot Ubuntu off and External hard drive and still be able to dual boot Windows & Ubuntu? if this is possible could this be an easier option? (I run Ubuntu from 2nd internal hard disk, could my friend not do the same with a 2nd External one?).

Failing this could I not display my grub2 configuration file, make adjustments (drive locations) to it then overwrite the standard one with it after installation? Does anyone know where the grub2 configuration file is located? 

PS: My friend is new to Ubuntu (9.04/9.10), I have have used (7.04 briefly, mainly used 8.10,9.04 & 9.10)

---

### Post by presence1960 on 2010-03-02
You can install as many OSs on a disk that your disk can have space for. I have Vista (with wubi), karmic, mint 8, sabayon & lucid all on the same SATA disk. And I installed Vista last. After the Vista install all I needed to do was restore GRUB to MBR which takes all of 30 seconds with an Ubuntu Live CD.

Nightstrike2009 just so you can see here is the reults of my boot info script. It is a very useful tool to troubleshoot setup & boot problems:

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

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
   2.3GB: vmlinuz.old

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

### Post by Nightstrike2009 on 2010-03-02
Thanks presence1960,

That info probably will help out, I noticed you have LILO and GRUB on two different partitions, is that a default (Live cd setup) or a manual addition?

Where is the Grub2 configuration file located on ubuntu? (I know how to access it from experimenting before but I was using 9.04 then so I had grub legacy)

PS: I am asking on behalf of a friend, I fully intend to boot Ubuntu ONLY once I have alternatives to my windows utilities and have tested them fully.

---

### Post by ubunterooster on 2010-03-02
lilo is added via a special [not ubuntu] live cd. Do you have SystemRescueCD? it's a special livecd that has many utilities, including one for installing grub easily.

---

### Post by darkod on 2010-03-02
The grub2 main config file is /boot/grub/grub.cfg but there was a command you need to run before you can write in it. Can't remember it right now.
And any changes will be lost after you run update-grub. That's why it's better to do the changes through /etc/grub.d and /etc/default/grub files.
But if you wanna play with it... just google around what you needed to run to edit it.

---

### Post by presence1960 on 2010-03-02
> **Nightstrike2009 said:**
> Thanks presence1960,

That info probably will help out, I noticed you have LILO and GRUB on two different partitions, is that a default (Live cd setup) or a manual addition?

Where is the Grub2 configuration file located on ubuntu? (I know how to access it from experimenting before but I was using 9.04 then so I had grub legacy)

PS: I am asking on behalf of a friend, I fully intend to boot Ubuntu ONLY once I have alternatives to my windows utilities and have tested them fully.

I have lilo on MBR because I used lilo to repair the MBR back to a windows MBR at one time. If you ever need to fix an MBR to boot windows you can install lilo by opening a terminal and running ```
sudo apt-get install lilo
``` either from ubuntu or a live cd. Then ignore the warning and run in terminal ```
sudo lilo -M /dev/sdX mbr
```where X = device. I.e. sda, sdb,sdc. This will fix your MBR to boot windows without running the windows install CD/DVD and the accompanying commands necessary to fix the MBR from the windows CD/DVD.

For GRUB2 config see here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by presence1960 on 2010-03-02
Hey Darko... I am broadcasting from the Dark Side...:p

---

### Post by darkod on 2010-03-02
> **presence1960 said:**
> hey darko... I am broadcasting from the dark side...:p

:lolflag:

---

### Post by Dr Droid on 2010-03-02
If my memory serves me correctly. After I installed windows 7 on a SATA drive I had many options... One was to edit the windows boot.ini to point to grub. This works when the windows bootloader is on the MBR. Or boot from the live cd and install grub/grub2/lilo. Recently I needed to use grub2 and at first was extremely angry, but now after having toyed with it I like it much much more that menu.lst. There are a few useful tips in my last thread about moving an existing install of Karmic onto a new partition. [http://ubuntuforums.org/showthread.php?t=1420135](http://ubuntuforums.org/showthread.php?t=1420135)

---

### Post by presence1960 on 2010-03-02
> **Dr Droid said:**
> If my memory serves me correctly. After I installed windows 7 on a SATA drive I had many options... One was to edit the windows boot.ini to point to grub. This works when the windows bootloader is on the MBR. Or boot from the live cd and install grub/grub2/lilo. Recently I needed to use grub2 and at first was extremely angry, but now after having toyed with it I like it much much more that menu.lst. There are a few useful tips in my last thread about moving an existing install of Karmic onto a new partition. [http://ubuntuforums.org/showthread.php?t=1420135](http://ubuntuforums.org/showthread.php?t=1420135)

windows 7 does not use boot.ini. Unless you installed windows 7 after XP and did not change the boot flag on the XP partition to the windows 7 partition prior to installing windows 7. Failure to do this will result in the boot files of XP & 7 being combined. That is the only way boot.ini can be involved in a windows 7 boot process. Windows 7 does not use boot.ini, XP does.

---

### Post by Dr Droid on 2010-03-03
Ah, I stand corrected- That does make sense considering I had XP on the partition originally and had installed vista and 7 for testing. 

To anyone looking for the grub2 way of fixing the MBR is by running (be sure to make sure 30_os-prober is executable before proceeding - ls -l /etc/grub.d/)
```

update-grub
grub-install /dev/xxx (device)

```

---

### Post by rwin on 2010-03-03
> **presence1960 said:**
> windows 7 does not use boot.ini. Unless you installed windows 7 after XP and did not change the boot flag on the XP partition to the windows 7 partition prior to installing windows 7. Failure to do this will result in the boot files of XP & 7 being combined. That is the only way boot.ini can be involved in a windows 7 boot process. Windows 7 does not use boot.ini, XP does.

And this does result in getting the Windows boot menu, regardless of which Windows version you chose before. How would you fix this combined usage (so that you will only have grub2 to choose between the two Windows systems)?

---

### Post by presence1960 on 2010-03-03
> **rwin said:**
> And this does result in getting the Windows boot menu, regardless of which Windows version you chose before. How would you fix this combined usage (so that you will only have grub2 to choose between the two Windows systems)?

You should arrange that prior to install by taking the boot flag off the already installed windows partition and placing the boot flag on the as yet uninstalled windows version partition. If this is not done it is a windows OS default procedure for the two OS boot files to be combined into one. At that point GRUB needs to point to the windows OS that has the combined boot files. When you choose windows from the GRUB menu you will then get the choice of which version of windows to boot.

I am sure there is a way to restore the boot files to each version of windows so GRUB can detect both versions and boot both directly from GRUB. maybe meierfra or someone well versed in windows can explain that.

---

### Post by oldfred on 2010-03-03
I certainly do not know as much as meierfra. And usually look to you guys for better info.

This site has a good explanation of how windows multi-boots:
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I would move the boot flag to the other version of windows and then run fixboot from the CD with the correct version of windows. That should install the necessary boot files.

---

### Post by presence1960 on 2010-03-03
> **oldfred said:**
> I certainly do not know as much as meierfra. And usually look to you guys for better info.

This site has a good explanation of how windows multi-boots:
 Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I would move the boot flag to the other version of windows and then run fixboot from the CD with the correct version of windows. That should install the necessary boot files.

Thanks for the link oldfred. When I get home from Tae Kwon Do tonight I will give that a read. being away from windows for a while now, I am not as knowledgeable about some windows areas as I would like to be. I only boot into windows a few times a month & the rest of the time I use linux.

Everyone knows something that somebody else does not know. So your input here is appreciated as always- 2 sets of eyes are better than one set. The combined experience & knowledge of all in this community is it's biggest strength.

---

### Post by oldfred on 2010-03-03
Thinking some more. Fix boot only repairs the boot sector. You will still have to add the files it copies to the other partition. 

XP needs  /boot.ini /ntldr /NTDETECT.COM

Vista or Win7 need /bootmgr /Boot/BCD /Windows/System32/winload.exe

I do not know if you can just copy them back from the other partition or reinstall from the repair CD. from repair cd for XP:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

I do not have Vista/Win7 but think the repair CD should also work.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

