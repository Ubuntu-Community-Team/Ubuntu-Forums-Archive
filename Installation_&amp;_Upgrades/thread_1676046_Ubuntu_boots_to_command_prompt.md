---
title: "Ubuntu boots to command prompt??"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by apanton06 on 2011-01-26
I just installed Ubuntu 10.10 and all went fine after install. 
It asked to install an Nvidia driver, so I went ahead and it asked to reboot. Upon doing so, now it only boots in to the terminal area.

Ideas how to fix it? W7 still boots fine

My graphics card is GForce 310M, 512 MB Vram

---

### Post by Rubi1200 on 2011-01-27
Hi and welcome to the forums :-)

I suggest the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

Thanks.

---

### Post by apanton06 on 2011-02-26
Late reply, I solved the problem temporarily. I just booted in to low res, on recovery mode and removed the Nvidia 3D driver. SO I can still boot up fine but unable to make the most out of games on Ubuntu, but I use windows for gaming anyway so it isn't a problem.

---

### Post by YesWeCan on 2011-02-26
Try adding 'nomodeset' to the grub kernel options. You can do this in /etc/default/grub and then run update-grub. Reinstall the correct nVidia drivers.

I read somewhere that there seems to be some problem when the kernel tries to set the graphics mode during boot. This issue has been around for years.

---

### Post by fewjr on 2011-03-12
Rubi1200,
     I'm having the same problem. I ran your script. I hope you can help. Here are the results:  

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   243,931,334   213,129,415   7 HPFS/NTFS
/dev/sda4         243,933,182   312,580,095    68,646,914   5 Extended
/dev/sda5         243,933,184   309,665,791    65,732,608  83 Linux
/dev/sda6         309,667,840   312,580,095     2,912,256  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            129     3,907,007     3,906,879   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        0AEE36F9EE36DC9F                       ntfs       RECOVERY                      
/dev/sda3        38E23AB1E23A736C                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        19b2bd05-fa10-428b-a365-27707b2546df   ext4                                     
/dev/sda6        7f7ed099-a249-4090-9da2-8c24355aefee   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1603-3B67                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
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
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=19b2bd05-fa10-428b-a365-27707b2546df ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
	echo	'Loading Linux 2.6.35-27-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-27-generic-pae root=UUID=19b2bd05-fa10-428b-a365-27707b2546df ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 19b2bd05-fa10-428b-a365-27707b2546df
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0aee36f9ee36dc9f
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
# / was on /dev/sda5 during installation
UUID=19b2bd05-fa10-428b-a365-27707b2546df /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7f7ed099-a249-4090-9da2-8c24355aefee none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 146.5GB: boot/grub/core.img
 138.0GB: boot/grub/grub.cfg
 125.8GB: boot/initrd.img-2.6.35-27-generic-pae
 146.5GB: boot/vmlinuz-2.6.35-27-generic-pae
 125.8GB: initrd.img
 146.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 81 00 00 00  |........?.......|
00000020  3f 9d 3b 00 b1 1d 00 00  00 00 00 00 02 00 00 00  |?.;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 67 3b 03 16 4e  4f 20 4e 41 4d 45 20 20  |..)g;..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 86  3b 00 00 66 ba 00 00 00  |..E}.f..;..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by fewjr on 2011-03-12
To continue,
     The computer I am working with is a new Alienware laptop I just recieved today from Dell. I had no problem installing Ubuntu 10.10 as a duel boot system until I rebooted after installing the restricted Broadcom and Nvidia drivers. Actually, before that after I first installed ubuntu and rebooted the first time, I booted into Windows to see if it was okay. It had to run a boot repair but then it was fine. So then I booted into Ubuntu and thats when I installed the restricted drivers.
      So I am at a standstill until you can tell me what is wrong. I would appreciate your help. Your script works very well. I am new to this, so...thanks.

fewjr

---

### Post by fewjr on 2011-03-13
Okay, I went into recovery mode and selected "failsafeX", and reonfigured graphics to default. So Ubuntu 10.10 runs fine again. I was hoping to learn something from the script you suggested Rubi1200. I have seen in a couple of post where your script was suggested, but I haven't seen anyone post the results. If you would care to show me what would be done with my results I would love to see it. I'm sure alot of folks could benefit.

Thanks,
fewjr

---

### Post by Rubi1200 on 2011-03-13
Sorry for the delayed response fewjr.

Actually, the script results suggest that everything is okay with your boot configuration. At least, there is nothing obviously wrong with the results.

As you discovered, and solved, it was actually a graphics issue.

In any event, should you ever have booting problems, you know that the first place to turn is the script.

---

### Post by fewjr on 2011-03-13
Thanks for popping in. Okay...well I guess I will have to study the results.txt a bit. If its good, then it would be good to know why. Yes I did relize that it was the Nvidia driver that I downloaded from restricted. A little reading is all it took. 

Thanks,
fewjr

---

### Post by Rubi1200 on 2011-03-14
Just to get you going, these are some of the important things to look for:

1. where is GRUB installed
> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.


2. are there any errors reported with the partitions
> Boot sector info:  No errors found in the Boot Parameter Block.

3. if you have other operating systems, is GRUB picking them up

> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0aee36f9ee36dc9f
	chainloader +1
4. are all the GRUB files there
> 146.5GB: boot/grub/core.img
 138.0GB: boot/grub/grub.cfg
 125.8GB: boot/initrd.img-2.6.35-27-generic-pae
 146.5GB: boot/vmlinuz-2.6.35-27-generic-pae
 125.8GB: initrd.img
 146.5GB: vmlinuz

Hope this helps as a starting point. The script is very useful for troubleshooting booting issues and keeping a record of the layout of your partitions amongst other things.

---

### Post by Farstanley on 2011-03-14
Me too
I just tried to put 10.10 on an Acer Aspire 4738z and I can only get the interface through recovery console > low resolution mode and no sound At All
Works fine on my other machines, which are older, so it could be Ubuntu developers are just a little behind Intel ( Who, like Acer, do not do drivers for Linux ) HD Audio & HD Graphics ( No disrespect intended here ) and the IntelHD Audio shows a Realtek vendor id but the device id is unknown and it's only two months before 11.4 becomes available but..
Anyone know what the current work arounds are for Intel Hd Audio, Display Audio & HD Graphics?
Didn't we used to have to provide a *.inf file or something?
Any help would be appreciated

---

### Post by fewjr on 2011-03-14
Thank you very much Rubi1200. That is very informative and I will keep it in mind for now on. I also hope it can help someone else later down the road.

fewjr

---

