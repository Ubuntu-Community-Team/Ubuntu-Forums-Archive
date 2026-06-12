---
title: "Black screen from GRUB in 10.10"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by Roger49 on 2011-02-26
Hi All,
I have installed Maverick onto an INTENSO 320GB USB Hard Disk.
I can boot from GRUB, but only get a dark grey screen, with no cursor.
I have tried editing the boot script, removing "quiet & splash" and putting in "nomodeset". I have also tried "i915.modeset=1" and "i915.modeset=0".
Also "xforcevesa" and "nouveau.modeset=0".
 
None have worked. I have not been able to reach a console screen to log in.
Here are the specifications of the machine:
 
Monitor: CTX 1569SE
Machine: HP Compaq Pentium 4, 512MB RAM
Graphics: Intel 829158/GV/910GL Express 
ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
/dev/sda: 4GB Quantum Bigfoot, Slave drive, from old Win95 machine.
/dev/sdb: 80GB Maxtor 6V080E0 Win XP Pro, bootable
/dev/sdc: 320GB Intenso USB hard disk, with GRUB2 resident.
/dev/sdc1: 80GB partition with Ubuntu 10.10 installed, ext3.
/dev/sdc2: 4GB partition, Linux Swap.
 
Are the number of spaces between "ro" and "quiet and splash" essential?
There are three spaces on the boot script and I have left them there.
 
Please let me know what it is I'm doing wrong!
Ubuntu works fine as a live CD, and I experienced no problems with the installation.
Regards,
Roger49

---

### Post by sikander3786 on 2011-02-26
Please plug-in your USB drive and boot from an Ubuntu Live CD or another USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated ```
 tags for readability purposes.

In the mean time, you can try reconfiguring your graphics. Choose Recovery mode from Grub menu and then Drop to Root Shell Prompt. Follow the commands below.

[code]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

The command is case sensitive. Capital 'X' for X11. If it says file not found, no problem, proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

Let us know how that goes.

---

### Post by Roger49 on 2011-02-26
Thanks Sikander,
There may be a delay while I work out how to do that.
I'm in Windows at the moment...
Regards,
Roger49

---

### Post by Roger49 on 2011-02-26
Hi Sikander,
Back again.
Here are the bootinfoscript results.
```
[CODE]
```                        #toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Liberation Serif'; font-variant: normal; text-indent: 0in; widows: 2; font-style: normal; font-weight: normal; text-decoration: none; color: rgb(0, 0, 0); text-align: left; font-size: 12pt; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Liberation Serif'; font-size: 12pt; text-align: left; }         [LEFT]                Boot Info Script 0.55    dated February 15th, 2010                    [/LEFT]
        
[LEFT]============================= Boot Info Summary: ==============================[/LEFT]
        
[LEFT] => Windows is installed in the MBR of /dev/sda[/LEFT]
    [LEFT] => No boot loader is installed in the MBR of /dev/sdb[/LEFT]
    [LEFT] => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in [/LEFT]
    [LEFT]    partition #1 for (,msdos1)/boot/grub.[/LEFT]
    [LEFT] => No boot loader is installed in the MBR of /dev/sde[/LEFT]
        
[LEFT]sda1: _________________________________________________________________________[/LEFT]
        
[LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  MSWIN4.1: Fat 32[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows 95[/LEFT]
    [LEFT]    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM[/LEFT]
        
[LEFT]sdb1: _________________________________________________________________________[/LEFT]
        
[LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows XP[/LEFT]
    [LEFT]    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[/LEFT]
        
[LEFT]sdc1: _________________________________________________________________________[/LEFT]
        
[LEFT]    File system:       ext3[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    [LEFT]    Operating System:  Ubuntu 10.10[/LEFT]
    [LEFT]    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/LEFT]
        
[LEFT]sdc2: _________________________________________________________________________[/LEFT]
        
[LEFT]    File system:       swap[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
        
[LEFT]sde1: _________________________________________________________________________[/LEFT]
        
[LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  Unknown[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files/dirs:   [/LEFT]
        
[LEFT]=========================== Drive/Partition Info: =============================[/LEFT]
        
[LEFT]Drive: sda ___________________ _____________________________________________________[/LEFT]
        
[LEFT]Disk /dev/sda: 4335 MB, 4335206400 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 527 cylinders, total 8467200 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        
[LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
        
[LEFT]/dev/sda1    *             63     8,450,189     8,450,127   b W95 FAT32[/LEFT]
        
    
[LEFT]Drive: sdb ___________________ _____________________________________________________[/LEFT]
        
[LEFT]Disk /dev/sdb: 80.0 GB, 80026361856 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        
[LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
        
[LEFT]/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS[/LEFT]
        
    
[LEFT]Drive: sdc ___________________ _____________________________________________________[/LEFT]
        
[LEFT]Disk /dev/sdc: 320.1 GB, 320072933376 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        
[LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
        
[LEFT]/dev/sdc1    *          2,048   156,250,111   156,248,064  83 Linux[/LEFT]
    [LEFT]/dev/sdc2         156,250,112   164,062,611     7,812,500  82 Linux swap / Solaris[/LEFT]
        
    
[LEFT]Drive: sde ___________________ _____________________________________________________[/LEFT]
        
[LEFT]Disk /dev/sde: 1010 MB, 1010826752 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 122 cylinders, total 1974271 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
        
[LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
        
[LEFT]/dev/sde1                  63     1,974,270     1,974,208   6 FAT16[/LEFT]
        
    
[LEFT]blkid -c /dev/null: ____________________________________________________________[/LEFT]
        
[LEFT]Device           UUID                                   TYPE       LABEL                         [/LEFT]
        
[LEFT]/dev/loop0                                              squashfs                                 [/LEFT]
    [LEFT]/dev/ramzswap0                                          swap                                     [/LEFT]
    [LEFT]/dev/sda1        1033-1101                              vfat                                     [/LEFT]
    [LEFT]/dev/sda: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sdb1        0D722CC16758D0E8                       ntfs                                     [/LEFT]
    [LEFT]/dev/sdb: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sdc1        c01e751f-bfc1-45b5-b73b-53c3944ee7e3   ext3                                     [/LEFT]
    [LEFT]/dev/sdc2        68dc41c4-be9c-4ef4-8402-fa501f3f70e6   swap                                     [/LEFT]
    [LEFT]/dev/sdc: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sde1        1508-18D5                              vfat       STORE'N'GO                    [/LEFT]
    [LEFT]/dev/sde: PTTYPE="dos" [/LEFT]
    [LEFT]error: /dev/sdd: No medium found[/LEFT]
        
[LEFT]============================ "mount | grep ^/dev  output: ===========================[/LEFT]
        
[LEFT]Device           Mount_Point              Type       Options[/LEFT]
        
[LEFT]aufs             /                        aufs       (rw)[/LEFT]
    [LEFT]/dev/sr0         /cdrom                   iso9660    (ro,noatime)[/LEFT]
    [LEFT]/dev/loop0       /rofs                    squashfs   (ro,noatime)[/LEFT]
    [LEFT]/dev/sde1        /media/STORE'N'GO        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)[/LEFT]
    [LEFT]/dev/sdc1        /media/c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ext3       (rw,nosuid,nodev,uhelper=udisks)[/LEFT]
        
    
[LEFT]================================ sdb1/boot.ini: ================================[/LEFT]
        
[LEFT][boot loader][/LEFT]
    [LEFT]timeout=30[/LEFT]
    [LEFT]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/LEFT]
        
[LEFT][operating systems][/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/LEFT]
        
[LEFT][spybotsd][/LEFT]
    [LEFT]timeout.old=30[/LEFT]
        
    
[LEFT]=========================== sdc1/boot/grub/grub.cfg: ===========================[/LEFT]
        
#
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    #
    [LEFT]# It is automatically generated by grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    #
        
[LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s $prefix/grubenv ]; then[/LEFT]
    [LEFT]  set have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ "${prev_saved_entry}" ]; then[/LEFT]
    [LEFT]  set saved_entry="${prev_saved_entry}"[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  set prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]  set boot_once=true[/LEFT]
    [LEFT]fi[/LEFT]
        
[LEFT]function savedefault {[/LEFT]
    [LEFT]  if [ -z "${boot_once}" ]; then[/LEFT]
    [LEFT]    saved_entry="${chosen}"[/LEFT]
    [LEFT]    save_env saved_entry[/LEFT]
    [LEFT]  fi[/LEFT]
    }
        
[LEFT]function recordfail {[/LEFT]
    [LEFT]  set recordfail=1[/LEFT]
    [LEFT]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/LEFT]
    }
        
[LEFT]function load_video {[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  insmod vga[/LEFT]
    }
        
[LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd2,msdos1)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=640x480[/LEFT]
    [LEFT]  load_video[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]terminal_output gfxterm[/LEFT]
    [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd2,msdos1)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]set locale_dir=($root)/boot/grub/locale[/LEFT]
    [LEFT]set lang=en[/LEFT]
    [LEFT]insmod gettext[/LEFT]
    [LEFT]if [ "${recordfail}" = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/light-gray[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd2,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro   quiet splash[/LEFT]
    [LEFT]	initrd	/boot/initrd.img-2.6.35-22-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]	recordfail[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd2,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]	echo	'Loading Linux 2.6.35-22-generic ...'[/LEFT]
    [LEFT]	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro single [/LEFT]
    [LEFT]	echo	'Loading initial ramdisk ...'[/LEFT]
    [LEFT]	initrd	/boot/initrd.img-2.6.35-22-generic[/LEFT]
    }
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/20_linux_xen ###[/LEFT]
    [LEFT]### END /etc/grub.d/20_linux_xen ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd2,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin[/LEFT]
    }
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ext2[/LEFT]
    [LEFT]	set root='(hd2,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]	linux16	/boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    }
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]menuentry "Windows 95/98/Me (on /dev/sda1)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod fat[/LEFT]
    [LEFT]	set root='(hd0,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 1033-1101[/LEFT]
    [LEFT]	drivemap -s (hd0) ${root}[/LEFT]
    [LEFT]	chainloader +1[/LEFT]
    }
    [LEFT]menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {[/LEFT]
    [LEFT]	insmod part_msdos[/LEFT]
    [LEFT]	insmod ntfs[/LEFT]
    [LEFT]	set root='(hd1,msdos1)'[/LEFT]
    [LEFT]	search --no-floppy --fs-uuid --set 0d722cc16758d0e8[/LEFT]
    [LEFT]	drivemap -s (hd0) ${root}[/LEFT]
    [LEFT]	chainloader +1[/LEFT]
    }
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]
        
[LEFT]### BEGIN /etc/grub.d/41_custom ###[/LEFT]
    [LEFT]if [ -f  $prefix/custom.cfg ]; then[/LEFT]
    [LEFT]  source $prefix/custom.cfg;[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/41_custom ###[/LEFT]
        
[LEFT]=============================== sdc1/etc/fstab: ===============================[/LEFT]
        
[LEFT]# /etc/fstab: static file system information.[/LEFT]
    #
    [LEFT]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/LEFT]
    [LEFT]# for a device; this may be used with UUID= as a more robust way to name[/LEFT]
    [LEFT]# devices that works even if disks are added and removed. See fstab(5).[/LEFT]
    #
    [LEFT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/LEFT]
    [LEFT]proc            /proc           proc    nodev,noexec,nosuid 0       0[/LEFT]
    [LEFT]# / was on /dev/sdc1 during installation[/LEFT]
    [LEFT]UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 /               ext3    errors=remount-ro 0       1[/LEFT]
    [LEFT]# swap was on /dev/sdc2 during installation[/LEFT]
    [LEFT]UUID=68dc41c4-be9c-4ef4-8402-fa501f3f70e6 none            swap    sw              0       0[/LEFT]
    [LEFT]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/LEFT]
        
[LEFT]=================== sdc1: Location of files loaded by Grub: ===================[/LEFT]
        
    
[LEFT]  70.7GB: boot/grub/core.img[/LEFT]
    [LEFT]  70.8GB: boot/grub/grub.cfg[/LEFT]
    [LEFT]  70.7GB: boot/initrd.img-2.6.35-22-generic[/LEFT]
    [LEFT]  70.7GB: boot/vmlinuz-2.6.35-22-generic[/LEFT]
    [LEFT]  70.7GB: initrd.img[/LEFT]
    [LEFT]  70.7GB: vmlinuz[/LEFT]
    [LEFT]=========================== Unknown MBRs/Boot Sectors/etc =======================[/LEFT]
        
[LEFT]Unknown BootLoader  on sde1[/LEFT]
        
[LEFT]00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 1e 00  |.<.MSWIN4.1.. ..|[/LEFT]
    [LEFT]00000010  02 00 02 00 00 f8 f1 00  3f 00 ff 00 3f 00 00 00  |........?...?...|[/LEFT]
    [LEFT]00000020  c0 1f 1e 00 80 00 29 d5  18 08 15 4e 4f 20 4e 41  |......)....NO NA|[/LEFT]
    [LEFT]00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|[/LEFT]
    [LEFT]00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|[/LEFT]
    [LEFT]00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|[/LEFT]
    [LEFT]00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|[/LEFT]
    [LEFT]00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|[/LEFT]
    [LEFT]00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|[/LEFT]
    [LEFT]00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|[/LEFT]
    [LEFT]000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|[/LEFT]
    [LEFT]000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|[/LEFT]
    [LEFT]000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|[/LEFT]
    [LEFT]000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|[/LEFT]
    [LEFT]000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|[/LEFT]
    [LEFT]000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|[/LEFT]
    [LEFT]00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|[/LEFT]
    [LEFT]00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|[/LEFT]
    [LEFT]00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|[/LEFT]
    [LEFT]00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|[/LEFT]
    [LEFT]00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|[/LEFT]
    [LEFT]00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|[/LEFT]
    [LEFT]00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|[/LEFT]
    [LEFT]00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|[/LEFT]
    [LEFT]00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|[/LEFT]
    [LEFT]00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |[/LEFT]
    [LEFT]000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|[/LEFT]
    [LEFT]000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|[/LEFT]
    [LEFT]000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|[/LEFT]
    [LEFT]000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |[/LEFT]
    [LEFT]000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|[/LEFT]
    [LEFT]000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|[/LEFT]
    00000200
        
    
[LEFT]=======Devices which don't seem to have a corresponding hard drive==============[/LEFT]
        
[LEFT]sdd [/LEFT]

[/CODE]

I hope I've done this correctly - haven't had to do it before.

I think that all Ubuntu options on the GRUB screen are inaccessible.
I can only boot to Windows from GRUB.
Regards,
Roger.

---

### Post by sikander3786 on 2011-02-26
Thanks for the output. It seems pretty good to me. No problems at all.

What happens if you choose the Recovery mode? Can you quote any error messages?

---

### Post by Roger49 on 2011-02-26
Hi Sikander,
I've just tried again - recovery mode goes to the same grey screen as Ubuntu.
No messages displayed.
 
I'll be offline now until tomorrow afternoon at the earliest.
Will be back in touch then.
Regards,
Roger49

---

### Post by Roger49 on 2011-03-01
Hi Sikander,
I've been looking at some other forums, and rtfm.
Am I correct in thinking that the problem may be with the X windows config?
Would it be possible to create a new one from a Live CD session? This being the only way I can currently run Ubuntu?
 
I have disks for a couple of the older versions, Dapper and Hardy.
If I install one of those, would it be feasible to use the x-org.config file from an earlier version in Maverick?
 
Looking forward to a reply,
Regards,
Roger49

---

### Post by sikander3786 on 2011-03-02
If there is a problem with xorg.conf, at least putting in 'nomodeset' should have worked.

And the modern 'X' doesn't need an xorg.conf. It does all that configuration stuff on the fly.

You can try with some other xorg.conf and later can remove it as mentioned in the above command if it doesn't work.

---

### Post by Roger49 on 2011-03-03
Hi Sikander,
I ran the Memory Test yesterday, and noticed that it mentioned I had an "i915 chipset"
This seems to be somewat notorious. Looking at the GRUB Command Line options last night, I saw "i915resolution" among the list of commands.
I will try running this tonight, followed by "startx" and see what happens.
Regards,
Roger49

---

### Post by Roger49 on 2011-03-03
Hi Sikander,
Nothing is what happened. Back to the black screen again.
Thats it for this week.
Will try to create new config file from live CD at w/end.
Regards,
Roger49

---

### Post by Roger49 on 2011-03-04
Hi Sikander,
I decided to have another go with the boot script edited and "i915.modeset=1" added. 
The screen was black. All of a sudden a lot of listing appeared, followed by a login.
I think it's finally working! 
Many thanks for your assistance.
Regards,
Roger49

---

### Post by sikander3786 on 2011-03-05
You are Welcome and glad that finally things are sorted for you :-)

Hope you enjoy your stay with Ubuntu!

---

### Post by zwei_zucker on 2011-03-06
Hi Everybody!

Had a similar problem today after restoring my Ubuntu Partition with dd=/ from my backup, all goes well  apart 
the booting ... now my system refuse to boot ! I have verified the boot flag on my sda3 partition ( in my case Ubuntu ext4) but nothing . Get a blank screen at boot up with "no operating systems" message !

Right now booting with Live CD :(

Thanks for some help !

p.s.: attached my boot info if it could help, thanks again everyone.

---

