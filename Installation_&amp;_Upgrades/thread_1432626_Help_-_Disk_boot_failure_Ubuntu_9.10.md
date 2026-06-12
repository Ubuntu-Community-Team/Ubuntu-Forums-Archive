---
title: "Help - Disk boot failure Ubuntu 9.10"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by nemesis688 on 2010-03-18
Hello, I am new here and to Ubuntu/Linux operating systems. It installs just fine but after it reboots I get a "disk boot failure, insert system disk". I have searched around but I can't seem to find anything that works.

There is only one hard drive in my computer and no other operating systems on it.

---

### Post by Herman on 2010-03-18
```
disk boot failure, insert system disk
```:D Is this boot error coming from your computer's BIOS?
If so, (and I will take a guess that it probably is from the BIOS), then it usually indicates that the BIOS has not been able to find a bootable MBR in your computer after looking at each of the drives in your BIOS boot sequence.

Since your post is fairly brief and doesn't give very much background information, I'm not sure if this is a new computer you have assembled yourself and this is the first time an operating system has ever been installed in it or if you replaced an operating system in a computer which has been booting okay until now.

The first thing to check is that your hard disk is properly set up and detected in the BIOS and it's listed in CMOS as one of the disks in the BIOS boot sequence.
Also check to make sure there's no BIOS MBR lock on, or 'boot sector antivirus' or the like, which may be preventing any software from writing any changes to your MBR.

You can check to see what your MBR looks like with a dd command,
```
sudo dd if=/dev/sda count=1 | hexdump -C
```Mine looks like this,
```
]1+0 records in
1+0 records out
00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
512 bytes (512 B) copied00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
, 3.6386e-05 s, 14.1 MB/s
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......**GRUB** .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  8f e7 9f 38 00 00 00 00  |...<.u.....8....|
000001c0  01 01 83 fe ff ff 00 04  00 00 a7 d9 73 07 00 00  |............s...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 **55 aa**  |..............U.|
00000200




```Notice the 55aa bootable disk symbol in the bottom right-hand corner.
If the BIOS doesn't find the 55aa bootable disc signature in any of your disks it gives you the error message you quoted.

Also look for the word GRUB in the right-hand column, that tells you that your installation has successfully written GRUB to your MBR, at least at some time in the past.  :D

---

