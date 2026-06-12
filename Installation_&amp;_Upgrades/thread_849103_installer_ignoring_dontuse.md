---
title: "installer ignoring dontuse?"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Hagalmir on 2008-07-04
Hi!

I recently installed the 32 bit version of Hardy on my second
partition on the first disk, to check the differences with the 64 bit
version on the other partition. I also have a second disk with a Luks
encrypted partition. While installing I took special care to mark all 
other partitions (including the luks partition on disk 2)
as "dontuse", but the installer seems to have corrupted it
anyway. The header look fine with cryptsetup luksDump, but the passphrase
is not accepted anymore. With hexdump -C /dev/sdb1 I found the following:

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  63 62 63 2d 65 73 73 69  |........cbc-essi|
00000030  76 3a 73 68 61 32 35 36  00 00 00 00 00 00 00 00  |v:sha256........|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 04 08 00 00 00 10  |................|

which looks nice, but then at 00000ff0

*
00000ff0  00 00 00 00 00 00 53 57  41 50 53 50 41 43 45 32  |......SWAPSPACE2|
00001000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|

Does this mean the partition has been marked as swap during the
install? Has anyone seen this problem? I guess the luks data
is lost, but maybe at least an installer bug has been found.

Regards
-Hagalmir

---

