---
title: "Kernel panic with Installation disk"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by alobo on 2005-02-22
Hi!

I'm trying to install Ubuntu 4.10 Warty Warthog from a CD that I've
burnt using the iso file warty-release-install-i386.iso

I have a working Mandrake 10.0, which I want to substitute by Ubuntu,
keeping my /home (which is in a different disk with reiserfs) intact.

First, I just wanted to check how the installation program sees
my partitions etc., but, once I start up with the CD, and
soon after I hit the first enter, I get:
(the screen cuts off the first character)

AMDDISK: Compressed image found at block 0
rc error
FS: Mounted root (ext2 filesystem).
ounted devfs on /dev
reeing unused kernel memory: 204k freed
XT2-fs error (device ram0): ext2_check_page:bad entry in direcory #287:rec_]
n is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
XT2-fs error (device ram0): ext2_check_page:bad entry in direcory #261:rec_]
n is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
ernel panic: No init found. Try passing init= option to kernel


My system has 1 Gb of RAM

Thanks for your help.

Agus

---

### Post by wallijonn on 2005-02-22
You may want to burn another copy from a different downloaded file, using Nero .iso burn image option.

You may want to download & run memtest on your memory subsystem because of the RAM0 errors (although they seem to be pointing to the HD as being bad, in which case you'll want to run diags on the HD).

RAMDDISK: Compressed image found at block 0
crc error
freeing unused kernel memory: 204k freed
EXT2-fs error (device ram0): ext2_check_page:bad entry in [COLOR=Blue]directory #287[/COLOR](?):rec_]
nn is smaller than minimal - offset=0, [COLOR=Blue]inode=0, rec_len=0, name_len=0[/color] (Sounds like the MBR)
kernel panic: No init found. Try passing init= option to kernel

---

