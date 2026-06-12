---
title: "Grub."
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by FahadMKS on 2010-08-19
I had the  Rad hat enterprise installed on to the computer which already had XP using a dual boot system.
When I saw that red hat needs an activation, I had to remove it from the computer, but was not aware of how to uninstall and OS.

So, I went to the XP OS  and selected the hard disk space where Red hat was installed and once after that deleted it.

The problem now is that, when I restarted the computer, I get only a black window with a message as Grub in it,

Now I am not even able to get to my Windows OS also.

Please Help!!!!!!!!!!!!!!!!


Note: while installation, one of the option as Kdump boot failure recovery was checked as I remember.

---

### Post by presence1960 on 2010-08-19
**_Do this if you ONLY have xp installed right now._** If you have multiple OSs installed skip to my next suggestion.

Boot from your windows xp install disk. Let it load up, may take a while depending on your hardware. At the screen which asks to install or repair choose repair. Select your windows xp install when given the option. When the command prompt appears first run ```
fixboot
```

Next run ```
fixmbr
```

Next run ```
exit
```

Reboot without the CD.

When you installed redhat you installed GRUB to the MBR of your hard disk. The windows boot loader now needs to be reinstalled to the MBR. That should do the trick!

If you have multiple OSs installed after you removed redhat **_don't do the above._**

Do this first:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

If you have more than one OS installed still I need to see what you have before giving any suggestions so as to make sure all your OSs will boot.

---

### Post by Dylnuge on 2010-08-20
I'm using Ubuntu, but I have a similar problem. When I install, everything seems to work fine. I can boot into Ubuntu, reboot, etc, without any problems. I can even boot into Windows 7--runs completely fine.

If I reboot after loading Windows, though, GRUB goes away entirely. I'm left with a damaged boot sector and my only choices are to either fixmbr with the Windows Install CD or reload GRUB manually from the Ubuntu Live CD.

I've tried reloading GRUB a couple of times--each time the same results occur.

EDIT:
This might explain some stuff: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

Unfortunately for me I have neither of the services available. I'm going to assume it is Dell's recovery partition, in which case I would like to know if it is possible for me to install GRUB to a Linux partition and have the Windows Boot Manager offer Ubuntu and load GRUB as an option; if so, how do I go about that, if not, are there any other solutions?

---

### Post by FahadMKS on 2010-08-21
To get rid of the issue I had installed the Ubuntu along with the windows using the option Install Side by Side

Now the issue has been solved upto a limit, but can I get a better screen on boot as I got with Red hat window to select the OS.

I havnt tried the steps that you said because it is said not to be done if there are multiple OS currently running.

---

### Post by presence1960 on 2010-08-22
> **FahadMKS said:**
> To get rid of the issue I had installed the Ubuntu along with the windows using the option Install Side by Side

Now the issue has been solved upto a limit, but can I get a better screen on boot as I got with Red hat window to select the OS.

I havnt tried the steps that you said because it is said not to be done if there are multiple OS currently running.

> If you have multiple OSs installed after you removed redhat don't do the above.

Do this first:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

See here for more info on the boot info script.

If you have more than one OS installed still I need to see what you have before giving any suggestions so as to make sure all your OSs will boot.
Do this please as I requested above.
__________________

---

### Post by FahadMKS on 2010-08-22
```

```  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 HPFS/NTFS
/dev/sda2          61,432,560   312,560,639   251,128,080   f W95 Ext d (LBA)
/dev/sda5          61,432,623   163,830,869   102,398,247   7 HPFS/NTFS
/dev/sda6         163,830,933   312,560,639   148,729,707   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   384,100,542   384,100,480   7 HPFS/NTFS
/dev/sdb2         384,102,398   488,396,799   104,294,402   5 Extended
/dev/sdb5         384,102,400   484,040,703    99,938,304  83 Linux
/dev/sdb6         484,042,752   488,396,799     4,354,048  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        1074CF2F74CF167E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        2EE49B26E49AEF79                       ntfs                                     
/dev/sda6        F83816243815E284                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb1        46D038E6D038DE3D                       ntfs       EHD-Seagate                   
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55   ext4                                     
/dev/sdb6        82d11b9a-a888-446f-a820-027d12a05854   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1074cf2f74cf167e
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5dfdd0f5-d280-4d38-ae69-ae6f23d1fb55 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=82d11b9a-a888-446f-a820-027d12a05854 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 226.8GB: boot/grub/core.img
 201.3GB: boot/grub/grub.cfg
 226.9GB: boot/initrd.img-2.6.32-21-generic
 227.0GB: boot/initrd.img-2.6.32-24-generic
 226.8GB: boot/vmlinuz-2.6.32-21-generic
 227.0GB: boot/vmlinuz-2.6.32-24-generic
 227.0GB: initrd.img
 226.9GB: initrd.img.old
 227.0GB: vmlinuz
 226.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  7b 3b bb 86 27 b6 47 fc  31 b7 9f 03 1e 75 bc 39  |{;..'.G.1....u.9|
00000010  de fa e1 8f d3 76 06 39  7d f8 41 df 37 e1 8d bc  |.....v.9}.A.7...|
00000020  fc 03 39 28 eb b2 6f 2d  f4 07 bf 0e 6e 87 b3 98  |..9(..o-....n...|
00000030  06 6b 6c c2 a7 ad 98 b3  97 eb b0 c1 6c e6 79 f8  |.kl.........l.y.|
00000040  62 6f dd 9a 04 5c 10 d2  f3 f1 88 86 03 41 60 71  |bo...\.......A`q|
00000050  c4 18 33 0c c0 2d c1 4a  3d 77 de 19 bd cc 20 77  |..3..-.J=w.... w|
00000060  b8 86 c0 4b 7b 66 79 23  81 a8 1c fb c1 98 68 e6  |...K{fy#......h.|
00000070  d7 88 d2 fe 70 5f 5f c9  2a ba 06 47 88 87 9b 98  |....p__.*..G....|
00000080  97 4e d7 bc c5 76 4e ba  bb fa dd 4d 8e 06 31 33  |.N...vN....M..13|
00000090  9e 3c fb fc 30 e3 3c 49  ef 92 e8 65 ed 90 e2 50  |.<..0.<I...e...P|
000000a0  44 74 fb fc e0 14 60 60  a7 99 7b dc 6c 01 60 93  |Dt....``..{.l.`.|
000000b0  c9 8c 18 e8 66 3e 3f f7  01 b1 08 0a de 01 04 01  |....f>?.........|
000000c0  82 cb 2c e5 97 9d 5e 1c  0e e3 84 8f 81 4e 61 62  |..,...^......Nab|
000000d0  13 12 2f ff f7 eb 48 d5  65 ef fc aa 5b 98 4c 19  |../...H.e...[.L.|
000000e0  bd c0 86 30 63 33 68 2d  f5 ef e2 9a 98 c3 c0 a6  |...0c3h-........|
000000f0  56 d9 9b ec b2 93 84 25  5e bb f5 7a 3b fc f4 cb  |V......%^..z;...|
00000100  77 d2 46 3d 18 db da f8  0c 7b fe f7 da d7 97 9c  |w.F=.....{......|
00000110  f6 bc 0a 6f 62 1f 67 94  b1 31 9a 60 bc e8 fe b6  |...ob.g..1.`....|
00000120  a2 d3 40 16 19 86 40 c2  c4 9e f7 bc 23 1d 75 91  |..@...@.....#.u.|
00000130  49 1a c2 db 85 79 bc f3  dc 02 ac 6d ef 7b 9c 1c  |I....y.....m.{..|
00000140  2c 33 e7 a7 2d 8b 6e 01  48 bf 53 1d 3b f7 06 37  |,3..-.n.H.S.;..7|
00000150  eb 55 0e 26 fd dd c3 1b  fb f8 63 6d eb 86 36 fe  |.U.&......cm..6.|
00000160  f0 c6 f3 af 0c 37 4e 6f  c3 1e 7b 5c 31 ed f7 86  |.....7No..{\1...|
00000170  3f 4d f8 41 db 3f d0 83  1c b7 c0 83 9c ec ac 01  |?M.A.?..........|
00000180  d4 8e 3f 4e 1f d9 1c 0c  7b 67 70 c7 f6 d7 00 91  |..?N....{gp.....|
00000190  38 43 b0 8a ee 68 08 dd  bc ce 09 30 0b 78 66 f4  |8C...h.....0.xf.|
000001a0  e1 83 37 bc 33 07 36 18  bd 5f be aa d9 66 59 ca  |..7.3.6.._...fY.|
000001b0  e7 a9 1f 97 79 4f fe ae  fb aa 7f 55 dd 97 00 fe  |....yO.....U....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 f4 05 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f0  f4 05 00 78 42 00 00 00  |...........xB...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2010-08-22
I do not see anything wrong in the boot info script. You should be able to boot Ubuntu or windows from the grub menu that comes up. Where are you at now?

---

### Post by FahadMKS on 2010-08-23
I am able to boot to OS by selection, but there does not seems to have a selection window such as the one I had with the Red Hat.

That is the only problem.

I am at India.

---

### Post by presence1960 on 2010-08-24
> **FahadMKS said:**
> I am able to boot to OS by selection, but there does not seems to have a selection window such as the one I had with the Red Hat.

That is the only problem.

I am at India.

I am not familiar with red hat. maybe the interface is different. As long as you can choose which OS to boot you really should not worry about it. if you want that pretty window reinstall red hat.

---

