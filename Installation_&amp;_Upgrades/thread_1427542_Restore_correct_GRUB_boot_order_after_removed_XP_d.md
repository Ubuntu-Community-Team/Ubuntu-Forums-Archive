---
title: "Restore correct GRUB boot order after removed XP drive"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by glenncvance on 2010-03-11
Hi all - I'm having a terrible time with this. I could really use some help.

I have an old Dell Dimension 4500 that, until recently, had 2 hard drives. One drive is running Xubuntu Koala and the other was running XP. I had set up Xubuntu to run LVM. 

After needing XP again for a small project I tried reinstalling XP, got disk errors, took the drive out to just have Xubuntu, and now when I boot I get "Error loading operating system".

I have tried restoring GRUB from a Live CD with no help. Everyplace I look on the net talks about restoring GRUB after installing Windows on another drive. I'm trying to get GRUB working again after removing the XP drive. Any and all help would be greatly appreciated. Thank you.

- Glenn

---

### Post by akand074 on 2010-03-11
[https://wiki.ubuntu.com/Grub2#Recove...20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recove...20via%20LiveCD")

---

### Post by glenncvance on 2010-03-11
akand074 - Thanks for the info, but where would I reinstall GRUB? From the Live CD?

---

### Post by 2hot6ft2 on 2010-03-11
Using Ubuntu 9.10 livecd
Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd,open terminal
Applications > Accessories > Terminal
and run:
To find out what your disk is listed as (that's the info you will use in place of sda8/sda6/sda in the examples)
```
fdisk -l
```That's fdisk -(lower case L)
To reinstall grub2
```
sudo -i

```
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot removing the livecd in the process.

This is from the Grub 2 Guide in my sig. below.

---

### Post by presence1960 on 2010-03-11
Let's not guess here. before you run any commands let's see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by glenncvance on 2010-03-11
Thanks everybody. My problem now is this :

```
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b0c361d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38882   312319633+  8e  Linux LVM
/dev/sda2           38883       38913      249007+   5  Extended
/dev/sda5           38883       38913      248976   83  Linux

root@ubuntu:/home/ubuntu# sudo -i
root@ubuntu:~# mount /dev/sda1 /mnt
mount: unknown filesystem type 'LVM2_member'
```

So I'm stuck. This LVM is killing me. Thanks.

---

### Post by glenncvance on 2010-03-11
Much thanks, presence1960. Here's the output of the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b0c361d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   624,639,329   624,639,267  8e Linux LVM
/dev/sda2         624,639,330   625,137,344       498,015   5 Extended
/dev/sda5         624,639,393   625,137,344       497,952  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        O2WLp1-xs1W-WZRJ-fxgg-npdZ-8HJZ-7QrfK0 LVM2_member                               
/dev/sda5        ff0531d6-a841-4204-82a8-176bfb9869ee   ext2                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


============================= sda5/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root=(charles-nickel-root)
search --no-floppy --fs-uuid --set 2d349134-4ca0-4779-97a5-492b016b42ab
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-20-generic root=/dev/mapper/charles--nickel-root ro   quiet splash
	initrd	/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-20-generic root=/dev/mapper/charles--nickel-root ro single 
	initrd	/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-19-generic root=/dev/mapper/charles--nickel-root ro   quiet splash
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-19-generic root=/dev/mapper/charles--nickel-root ro single 
	initrd	/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/charles--nickel-root ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set ff0531d6-a841-4204-82a8-176bfb9869ee
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/charles--nickel-root ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 319.8GB: grub/core.img
 319.8GB: grub/grub.cfg
 319.8GB: initrd.img-2.6.31-14-generic
 319.8GB: initrd.img-2.6.31-19-generic
 319.8GB: initrd.img-2.6.31-20-generic
 319.8GB: vmlinuz-2.6.31-14-generic
 319.8GB: vmlinuz-2.6.31-19-generic
 319.8GB: vmlinuz-2.6.31-20-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  3e 90 ef 79 d2 ad 13 b2  3e 44 ed 78 7a 25 69 f5  |>..y....>D.xz%i.|
00000010  eb fc 24 57 4f b6 36 f7  36 aa 1a ee 89 cd 27 b0  |..$WO.6.6.....'.|
00000020  7c ec 3b 09 53 57 fd b6  98 19 51 99 a2 36 b3 3f  ||.;.SW....Q..6.?|
00000030  4c c6 ee 57 ab 51 a2 df  58 c6 99 10 eb 30 f4 f3  |L..W.Q..X....0..|
00000040  23 07 b8 28 bf fb e3 a3  81 98 f2 f8 99 ee 04 33  |#..(...........3|
00000050  db 32 ce 97 ca 49 07 99  65 19 d5 5b 3e 72 4e a6  |.2...I..e..[>rN.|
00000060  73 93 53 e3 ad 38 64 e9  18 70 d3 f1 20 48 ff 63  |s.S..8d..p.. H.c|
00000070  3a 7e d9 87 f7 a0 c7 46  a8 96 cd 44 78 ff da 1a  |:~.....F...Dx...|
00000080  2d 4f 6f 78 85 1f 74 64  2a 52 c2 01 83 d1 ef a2  |-Oox..td*R......|
00000090  c7 a2 cf bd cb 9d e7 db  3b d2 15 d3 e0 a4 7f af  |........;.......|
000000a0  7e 01 48 e4 79 ce 6c f4  f1 0f 45 a0 6a e8 19 51  |~.H.y.l...E.j..Q|
000000b0  c8 b8 8b ac 83 93 b0 32  b4 ea 3a 1a b9 c4 49 cd  |.......2..:...I.|
000000c0  c2 4f ee b5 cf 42 9b dc  59 e4 67 69 73 ee 32 a9  |.O...B..Y.gis.2.|
000000d0  a7 b9 b6 6f 49 6e d3 bd  1a a9 19 f3 c8 9d ef b3  |...oIn..........|
000000e0  69 a2 3e aa 98 17 e7 0b  48 6a 9e b5 9d bd 17 13  |i.>.....Hj......|
000000f0  14 fd 71 23 8f 14 fd 5b  86 a4 7a 5f 61 62 c2 c5  |..q#...[..z_ab..|
00000100  7f 11 b8 13 3b f3 ec 56  9a 3e 43 74 57 38 dc 18  |....;..V.>CtW8..|
00000110  ce 1b a9 cc 11 e6 7e f5  2d ca 62 29 f3 2f f4 57  |......~.-.b)./.W|
00000120  e4 e8 9c 0a 65 7a 3e 5c  a4 5f ad 5a c1 cf d9 13  |....ez>\._.Z....|
00000130  bf 92 b2 e7 11 ea bc e4  56 a0 fa be 19 f2 85 1f  |........V.......|
00000140  a4 a4 09 f9 ba a1 66 c8  6b 04 d6 01 9d 62 42 06  |......f.k....bB.|
00000150  89 c6 2e fa 1d 32 cf 4d  3d 1c 62 b7 0c d4 71 df  |.....2.M=.b...q.|
00000160  89 77 58 3a 42 e5 d0 d2  7b 4c 9e 6f 7a 8a f7 a1  |.wX:B...{L.oz...|
00000170  e7 0f bc 95 2a b3 df f9  b6 95 cf 20 53 f8 32 d7  |....*...... S.2.|
00000180  2b 16 9e 7b 92 3e bc 33  7a ed 1c a7 95 c0 2d e4  |+..{.>.3z.....-.|
00000190  3d 1b 37 9f f3 23 5a f3  ad 39 84 96 71 c4 ac 15  |=.7..#Z..9..q...|
000001a0  cf b5 9d 42 22 a9 8c 2b  c6 19 72 9f 34 a5 c2 f1  |...B"..+..r.4...|
000001b0  1f eb 38 6f d1 e7 0b 99  a4 ce 4a 99 01 83 e9 e9  |..8o......J.....|
000001c0  4c 4b d6 9c 37 e1 1b 6c  9b 47 ba 78 82 4f 92 a6  |LK..7..l.G.x.O..|
000001d0  e3 fd c9 65 69 08 d2 d4  63 28 ff 65 64 d8 29 be  |...ei...c(.ed.).|
000001e0  9d c6 4d 58 19 d8 b3 fe  32 78 53 6f fb 5f be f5  |..MX....2xSo._..|
000001f0  37 73 4c dc 8e 84 17 a4  e0 a5 fd 78 63 e6 6f 1b  |7sL........xc.o.|
00000200



```

---

### Post by presence1960 on 2010-03-11
I do not know too much about LVM, but what I can see from your boot info script sda5 is a /boot partition and sda1 is the OS. If this is indeed correct go [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") and follow method 3- Chroot

P.S. All the methods on that page may fail due to LVM- again I am not sure. I would consider starting a new thread if this fails with LVM in the thread title to attract attention of those versed in LVM

---

### Post by glenncvance on 2010-03-11
Thanks presence. I'll give it a try. Much appreciated.

---

### Post by presence1960 on 2010-03-11
> **glenncvance said:**
> Thanks presence. I'll give it a try. Much appreciated.

I wish I could be of more help, but I have never used LVM. If it doesn't work I would start a new thread with LVM and GRUB 2 in the title to attract attention from those who have experience in this matter.

---

### Post by poltr1 on 2010-03-11
Thanks for the instructions on how to reinstall grub.  I tried to install XP on a laptop that already had karmic, and Windows just doesn't play well with other OSes.  (Why did I do this?  Because I had it.)  These instructions helped me restore my system.  Thanks again.

---

