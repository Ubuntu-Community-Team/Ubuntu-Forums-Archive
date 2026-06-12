---
title: "Ubuntu 10.10 - Fails to boot from disc"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Cheese Power on 2010-11-12
I have an ASUS G51J notebook with Windows 7 installed. I was following **_[This Guide]("https://help.ubuntu.com/community/WindowsDualBoot")_**. I set aside about 100GB for the Unallocated partition. When I started my laptop, I chose to boot from CD (which has an Ubuntu 10.10 ISO on it). I saw a purple background with two icons at the bottom of the screen, and eventually "Ubuntu" appeared in the center with a few dots underneath it. These dots would change color from left to right like a loading bar.

This is where my issue comes up. My friend was using this same CD on his Dell laptop and his desktop which has a XFX motherboard, Q6600 processor, and Invidia 470 graphics card. After this "loading bar" was done, he would be asked if he wanted to boot or install Ubuntu.

This didn't happen for me. What happened instead was that I saw what looked like my Windows desktop after having gone through a meat grinder. There were various icons randomly in pieces all over the place. The only icon that was in one piece (by chance) was my shortcut to Skype.

Has anyone seen this before? Am I doing something wrong? My friend was saying that maybe I should try with a fresh reinstall of Windows and try again. I wasn't even given the choice to just boot from disc. It got to the point where I expected it to give me the options to do so, but instead the Kansas version of my desktop shows up after being hit by an F5.

Edit:
My friend was watching it load, and he says it looks like it's trying to boot up (without asking me whether to boot or install). When he was loading it up from disc, there were 4 dots that made up the loading bar. For me there are 5 dots. There is also a little logo on the top right side of "Ubuntu". This time when it was "done" loading, the screen turned black and white. It looked like a blocky maze.

---

### Post by Rubi1200 on 2010-11-13
Hi and welcome to the forums :)

Take a look here and see if it helps:
[http://ubuntuforums.org/showpost.php?p=10089470&postcount=4](http://ubuntuforums.org/showpost.php?p=10089470&postcount=4)

---

### Post by Cheese Power on 2010-11-13
Thanks for responding. That post doesn't really help me since I cannot even boot. I would like to install Ubuntu eventually, but I can't get anything to happen.

---

### Post by Richard60 on 2010-12-09
I have exactly the same problem with my Asus G51Jx I use 10.04 now, but 10.10 won't install. I did not find the solution yet. So I am looking forward to it.

---

### Post by Quackers on 2010-12-09
When the purple screen shows up press any key and a different screen should appear. Press F6 and a few options will appear near the bottom right of the screen. Select the "nomodeset" option and continue. This should get you to the next screens ( I think )

---

### Post by Richard60 on 2010-12-10
This works, Now the installation completed. But a new problem now. After completing and rebooting a error occurded: the symbol 'grub_xputs' not found.
grub resque>
 
what now?

---

### Post by sikander3786 on 2010-12-10
> **Richard60 said:**
> This works, Now the installation completed. But a new problem now. After completing and rebooting a error occurded: the symbol 'grub_xputs' not found.
grub resque>
 
what now?
Are you sure you are booting from the proper HDD? Check in Bios menu.

If that is not causing problems, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Rubi1200 on 2010-12-10
Hi,
an xputs error usually means that GRUB is missing some files. To repair this you will need to purge and reinstall GRUB from the LiveCD.

First, however, we need you to boot the computer with the LiveCD and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we have a better overview of your system and to make sure there are no other issues that need to be dealt with.

Thanks.

---

### Post by Richard60 on 2010-12-10
Here is the results.txt file.

---

### Post by sikander3786 on 2010-12-10
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 17350784 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    34,828,919    34,828,857  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     34,828,920   279,022,199   244,193,280   7 HPFS/NTFS
/dev/sda3         279,023,616   976,771,071   697,747,456   5 Extended
/dev/sda5         279,025,664   976,771,071   697,745,408   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sdb2          39,065,598   976,771,071   937,705,474   5 Extended
/dev/sdb5          39,065,600    54,687,743    15,622,144  82 Linux swap / Solaris
/dev/sdb6          54,689,792   976,771,071   922,081,280  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        02FA-C75A                              vfat       RECOVERY                      
/dev/sda2        244AB52C4AB4FC1C                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        FEE4B766E4B71FB7                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3474d795-d719-46dd-a37b-3a658ca7aa10   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        0cd4f8e4-28ba-452e-85da-3c5c50229452   swap                                     
/dev/sdb6        38006fdf-a0c7-486d-8ee0-19ab0204ecf5   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
set locale_dir=($root)/boot/grub/locale
set lang=nl
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3474d795-d719-46dd-a37b-3a658ca7aa10 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3474d795-d719-46dd-a37b-3a658ca7aa10 ro single 
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
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set 3474d795-d719-46dd-a37b-3a658ca7aa10
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 02fa-c75a
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 244ab52c4ab4fc1c
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=3474d795-d719-46dd-a37b-3a658ca7aa10 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=38006fdf-a0c7-486d-8ee0-19ab0204ecf5 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=0cd4f8e4-28ba-452e-85da-3c5c50229452 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   8.8GB: boot/grub/core.img
    .6GB: boot/grub/grub.cfg
   1.4GB: boot/initrd.img-2.6.35-22-generic
   8.8GB: boot/vmlinuz-2.6.35-22-generic
   1.4GB: initrd.img
   8.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  e1 d9 83 c3 ed f5 8d 33  31 f8 30 18 2e b4 96 7e  |.......31.0....~|
00000010  a2 35 46 50 8b 16 8b 11  d7 a2 0f c7 bb 51 51 21  |.5FP.........QQ!|
00000020  86 c3 9d 83 05 33 c7 63  04 0f 93 98 03 e1 0d 4f  |.....3.c.......O|
00000030  63 ec 0a 04 14 04 1c 7c  58 90 6f a2 69 51 a7 a9  |c......|X.o.iQ..|
00000040  d2 fc a6 1c ec 09 70 2c  ca f4 b7 b2 73 f5 0c ae  |......p,....s...|
00000050  f6 7b 96 ad 9e 25 6c ec  24 35 a5 b0 fd 75 4b 96  |.{...%l.$5...uK.|
00000060  81 44 93 50 98 86 0a 33  65 aa ff 8d f9 e3 6e 41  |.D.P...3e.....nA|
00000070  c5 0b d5 07 49 7a 59 c6  70 05 4c ed 5e d5 6c 87  |....IzY.p.L.^.l.|
00000080  38 77 24 b3 63 e6 9a 9c  4b 1c 00 3e 1f b3 71 1a  |8w$.c...K..>..q.|
00000090  d4 72 22 d0 e6 13 9e e7  22 30 7a 30 d2 48 16 17  |.r"....."0z0.H..|
000000a0  1e 0b a3 0e 61 bf fa 60  75 3f 51 89 fb 54 f5 3c  |....a..`u?Q..T.<|
000000b0  e3 a5 25 03 8d 56 77 13  ee 92 55 db 38 da a7 f4  |..%..Vw...U.8...|
000000c0  a2 07 59 dc 3e 31 92 de  96 c4 c8 2c b5 d6 80 28  |..Y.>1.....,...(|
000000d0  88 59 43 53 37 c4 4f bb  65 ef 1b c1 e8 d5 1c 1a  |.YCS7.O.e.......|
000000e0  47 33 28 91 3a 7e 50 37  80 75 ad 6a 5a 4a 90 d3  |G3(.:~P7.u.jZJ..|
000000f0  bd 79 37 3b a6 1f be da  10 77 a4 1e c3 89 6e aa  |.y7;.....w....n.|
00000100  1d 2e 8c 6c 38 a1 d3 cb  02 31 72 4d 73 07 27 ed  |...l8....1rMs.'.|
00000110  08 68 85 a5 06 df 60 7c  8e f5 49 e4 ae 92 d3 e9  |.h....`|..I.....|
00000120  dc b0 98 23 3f 4c 25 50  e3 b3 ff 8b af 4b 96 5d  |...#?L%P.....K.]|
00000130  93 14 f7 91 96 96 f3 ad  d2 86 1f 1e 5d b0 d6 6e  |............]..n|
00000140  1e bc ce 33 eb 75 9e 5f  7a 66 cc 40 72 55 d7 97  |...3.u._zf.@rU..|
00000150  52 f0 ba 74 b8 a6 2c 21  29 bb e3 1f f2 be 04 00  |R..t..,!).......|
00000160  94 12 e1 12 8a 0c 0b 4f  b0 c0 5f 5c c3 75 e9 af  |.......O.._\.u..|
00000170  5c 35 b5 6d 4c 52 2f d7  dd e5 27 1f 4a c8 7b 95  |\5.mLR/...'.J.{.|
00000180  a3 3e 44 a4 c2 97 df 29  93 06 2b d6 74 6e 8d 6c  |.>D....)..+.tn.l|
00000190  8f ae 8e d6 a6 b8 f4 11  ce af ca be 82 bc 4a f2  |..............J.|
000001a0  41 df c0 1c dd 42 77 d1  51 75 11 c2 ec 4b 29 3d  |A....Bw.Qu...K)=|
000001b0  64 35 32 bf fe 1c da b5  8f 67 ce 1b 55 1a 00 fe  |d52......g..U...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 ee 00 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff 02 60  ee 00 00 e0 f5 36 00 00  |.......`.....6..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by sikander3786 on 2010-12-10
The problem seems to lie here.

```
sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [B]Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 17350784 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 2048.[/B]
    Operating System:  
    Boot files/dirs:   

```

In my opinion, you need to purge and re-install Grub as described here.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Richard60 on 2010-12-10
Grub 2 reinstalled. Ubuntu started. After the logo the screen booting failed again. The same problem as in the first post. The circle was closed again.

---

### Post by Quackers on 2010-12-10
Did you try the nomodeset option?

---

### Post by Richard60 on 2010-12-10
I reinstalled 10.10 on a external esata hdd. I used nomodeset. I installed Grub on the external hdd. After installing en rebooting I had to use safe mode. After sevaral updates and installed Nvidia driver Ubuntu started ok.
I had 1 error message: Intel ips 0000:00:1f.6: *failed to get i915* symbols, graphics turbo disabled.
So it has progress, but it is not easy. How to solve the error message.

---

### Post by Quackers on 2010-12-10
There are also i915.modeset=1 and i915.modeset=0 boot options, I believe. You could try those. However, there is another thread on here where he is using a new machine with a new type of Intel chipset graphics, for which there is no current driver and he cannot find a workaround. It may be that you have the same chipset?

---

### Post by Richard60 on 2010-12-10
I accept the missing of a recent driver. My notebook is recent indeed. Thanks for your help. I wait untill the new driver arrives.

---

### Post by sikander3786 on 2010-12-11
> **Richard60 said:**
> I accept the missing of a recent driver. My notebook is recent indeed. Thanks for your help. I wait untill the new driver arrives.
I would want to work a bit more on this one if you want to...

So it is an Nvidia GTX 260M graphics chip? That is supported under Ubuntu since Lucid. I've seen some people using it.

Proprietary drivers have not been installed already from the Live CD? A workaround might be to boot a Live CD/USB and install the graphics drivers in that environment. Where it asks for a reboot, don't reboot. Switch to tty1 by pressing Ctrl + Alt + F1 and restart gdm.

```
sudo service gdm stop
```

```
sudo service gdm start
```

If the drivers were installed correctly, install Ubuntu once more and they'll be included in the installation and might solve the issue for you.

Or, boot to recovery mode from your existing install > drop to root shell and try to reconfigure your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot:

```
sudo shutdown -r now
```

Don't put in any parameter like nomodeset or i915 etc. Just let it boot normally. What happens?

If that doesn't work, from the same root shell, try to install nvidia drivers. Plug in your ethernet cable,

```
dhclient eht0
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install nvidia-current nvidia-common nvidia-settings
```

Reboot once more, if still no response, try to configure it from the command line.

```
sudo nvidia-xconfig
```

Lets hope any of those fixes works for you.

---

### Post by Richard60 on 2010-12-12
The notebook has a nVidia Geforce GTS 360M. Does that make a difference?

---

### Post by sikander3786 on 2010-12-12
> **Richard60 said:**
> The notebook has a nVidia Geforce GTS 360M. Does that make a difference?
It shouldn't. Did you try the steps in above post?

---

