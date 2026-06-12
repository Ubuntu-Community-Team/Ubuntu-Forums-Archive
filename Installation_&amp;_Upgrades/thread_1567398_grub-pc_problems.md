---
title: "grub-pc problems"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Shpadoinkle on 2010-09-03
When trying to install grub-pc on ubuntu 10.04, i get a pop-up window that i have included a screenshot of. Any help would be appreciated.

---

### Post by drs305 on 2010-09-03
That is a normal step in the Grub2 install. It is asking if you need any special options during boot, such as "noapic", etc. Chances are good that you don't need any, or if you do you already know what to type there.

If you don't need any special kernel instructions, just TAB to the "OK" prompt and press ENTER to continue with the install.

---

### Post by Shpadoinkle on 2010-09-03
well, when i do that i get this...

---

### Post by Shpadoinkle on 2010-09-03
and heres the output...

---

### Post by drs305 on 2010-09-03
Grub 2 failed to install correctly for some reason, but it isn't related to the first post.

You can try a reinstall to see if that corrects the problem:
```
sudo apt-get install --reinstall grub-pc
```

Before continuing, you might want to explain why you are installing Grub2. It should have already been on your machine when you installed 10.04 under normal circumstances. Reinstalling may not be what you need to do...

If you want to continue trying to fix things without further explanation, you could try purging it completely and reinstalling, although this may also be unsuccessful. If you choose this option, make sure you have a good Internet connection and power supply, as you will not have a bootloader on your machine for a very brief period.

Assuming you are currently in a normal Ubuntu installation (not a LiveCD or wubi), run these commands. The first removes grub-pc and grub-common, the second reinstalls them:
```
sudo apt-get purge grub-common
sudo apt-get install grub-pc
```
When you get to the partitioning section, choose the drive (sda, sdb) you want Grub2 installed on - do not include a partition number.

If you continue to have "postinst" errors, let us know.

---

### Post by Shpadoinkle on 2010-09-03
well, none of the above seemed to have fixed the problem. When i updated ubuntu after installing from the cd is when i first had this problem. everything worked fine until I updated. this is the output from the first code given...

Setting up grub-pc (1.98-1ubuntu7) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2010-09-03
I sort of expected that result but was hopeful...

The reason is that the next thing I'll recommend 'bypasses' APT by removing access to the post-install script. It's not as clean a solution, but it will most likely work. 

We will rename the script which is generating the error. Renaming it will allow us to restore it to the original name if this attempt doesn't work, making it better than deleting the file completely.

```
sudo mv /var/lib/dpkg/info/grub-pc.postinst /var/lib/dpkg/info/grub-pc.postinst.bad
```

Then try reinstalling grub-pc.

---

### Post by Shpadoinkle on 2010-09-03
well, i did everything above, reinstalled grub-pc and rebooted. No linux kernals are showing up now, only memtest86.

---

### Post by drs305 on 2010-09-03
> **Shpadoinkle said:**
> well, i did everything above, reinstalled grub-pc and rebooted. No linux kernals are showing up now, only memtest86.

Time to run *meierfra's* boot info script. Go to the link, download the script, run it according to the instructions on the site, and then post the contents here.

When you post the contents of RESULTS.txt, please copy them into the post, highlight them, and then press the # icon in the post's menubar to enclose the results within "code" tags.

The information will allow us to see the status of your Ubuntu system. If you can't get into your normal install, run the script from the LiveCD/install CD and it will give us the same information.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Shpadoinkle on 2010-09-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f0c7842f-14ba-4592-96c5-b2c6a4be0d45   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        059a9b72-bed5-47e5-8b2b-d968f949f341   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0c7842f-14ba-4592-96c5-b2c6a4be0d45
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0c7842f-14ba-4592-96c5-b2c6a4be0d45
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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
UUID=f0c7842f-14ba-4592-96c5-b2c6a4be0d45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=059a9b72-bed5-47e5-8b2b-d968f949f341 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  77.4GB: boot/grub/core.img
  95.0GB: boot/grub/grub.cfg
  77.4GB: boot/initrd.img-2.6.32-21-generic
  77.5GB: boot/initrd.img-2.6.32-24-generic
  77.5GB: boot/initrd.img-2.6.32-25-generic
  77.4GB: boot/vmlinuz-2.6.32-21-generic
  77.4GB: boot/vmlinuz-2.6.32-24-generic
  77.5GB: boot/vmlinuz-2.6.32-25-generic
  77.5GB: initrd.img
  77.5GB: initrd.img.old
  77.5GB: vmlinuz
  77.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  53 29 0b e9 c1 d1 eb 0c  e8 83 90 94 ab 56 53 8c  |S)...........VS.|
00000010  5d 77 a4 26 04 75 1a e9  ce ac d2 de 9b ca e4 80  |]w.&.u..........|
00000020  94 cf ab 19 91 99 fb d8  4d 5a ff fd 95 93 9c 71  |........MZ.....q|
00000030  12 84 a5 be b2 8d 42 88  c5 4a d4 8f 99 1b c0 78  |......B..J.....x|
00000040  7b 34 d9 99 81 19 c3 a9  8f 90 cf 8f 86 14 58 e1  |{4............X.|
00000050  55 42 86 12 9e a8 58 d9  3a 2a 37 f3 33 28 68 4c  |UB....X.:*7.3(hL|
00000060  ae 37 2b e1 21 21 24 01  c9 09 47 c2 f1 74 e5 46  |.7+.!!$...G..t.F|
00000070  27 2d 99 be 90 f3 a8 dc  7b 44 c7 67 f8 d9 51 56  |'-......{D.g..QV|
00000080  6b f7 85 a0 bb 3f c0 83  1c 5c 00 9d bb 76 1e 5f  |k....?...\...v._|
00000090  e1 a4 0c 19 4b d7 6a 71  bc 5e 93 c3 4c fd 4e ab  |....K.jq.^..L.N.|
000000a0  90 c1 ca 0e 62 16 a3 4b  bb 2b 06 59 8e 95 5c a9  |....b..K.+.Y..\.|
000000b0  d0 6e 4f 04 2d f0 3e 24  2f 37 7f 87 83 01 46 e1  |.nO.-.>$/7....F.|
000000c0  cc c4 4c 38 63 ce 23 82  aa 90 51 a0 ac 25 32 ea  |..L8c.#...Q..%2.|
000000d0  d9 48 cc 31 d4 fa 17 cb  85 b2 d5 1e 7d e9 64 92  |.H.1........}.d.|
000000e0  1a ae f8 9f b4 73 a4 6d  ab cf 45 04 4f 36 7d 16  |.....s.m..E.O6}.|
000000f0  b8 da 6d 62 27 4f 18 f4  4e c7 5f 32 4d 04 54 7a  |..mb'O..N._2M.Tz|
00000100  96 7a 66 05 3c eb 70 1e  de ef c4 5f a2 d8 91 55  |.zf.<.p...._...U|
00000110  76 a4 4f 8b ed 3a fe da  67 a1 c4 38 9a 1d e3 5c  |v.O..:..g..8...\|
00000120  5c 04 d5 98 10 4c 13 14  cb a7 69 95 ca e5 e5 8a  |\....L....i.....|
00000130  d2 06 d5 9f a1 1d 32 7c  ee 30 fb 15 a2 f2 bc 76  |......2|.0.....v|
00000140  08 02 94 04 14 e6 d6 c3  f0 ea 1e 29 23 78 79 a8  |...........)#xy.|
00000150  92 4a 83 f8 e4 60 1a 02  1c 55 60 d9 2c 62 e4 e6  |.J...`...U`.,b..|
00000160  02 39 e0 20 b0 9e 41 58  a0 6b 0a 6c 48 26 2e 6c  |.9. ..AX.k.lH&.l|
00000170  22 44 60 34 1e b1 13 42  2c a3 29 0e a3 c2 66 96  |"D`4...B,.)...f.|
00000180  0e 06 8e b8 47 3a 31 8d  4c 5d c2 73 b8 86 5b 50  |....G:1.L].s..[P|
00000190  70 3d b6 5d 8f 4b c6 a1  e8 3e 5a 40 5a 5f 5e 27  |p=.].K...>Z@Z_^'|
000001a0  28 fb 19 45 3b 33 38 a6  67 61 6b 58 ab 4b 1c 42  |(..E;38.gakX.K.B|
000001b0  12 0b 0b 14 e2 61 21 15  a0 61 89 83 e6 65 00 fe  |.....a!..a...e..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 92 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

