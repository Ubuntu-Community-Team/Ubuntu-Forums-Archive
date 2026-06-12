---
title: "GRUB error or Kernel Init..."
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by Lifyre on 2005-02-22
Take your pick.

I just installed a new motherboard into my box.  Was running an AOpen AX6LC with a Celeron 300A which I replaced with a Tekram P6PRO-A+ running a PIII 500.  The main reason I did this was the ram was PC133 and the AOpen only would run it 66MHz and the Tekram runs it at 133...

After the swap I tried to boot it.

The first error I got was

"GRUB Loading stage1.5



GRUB loading, please wait...
Error 18"

I tried fiddling with the BIOS to no avail and resorted to trying to install Ubuntu again.  I did this 3 times on the previous motherboard no problem.  This time I got error

"RAMDISK: Compressed image found at block 0
incomplete distance tree
invalid compressed format (err=1)
VFS: Mounted root (ext2 filesystem).
Mounted devfs on /dev
Freeing unused kernel memory: 204k freed
EXT2-fs error (device ram0): ext2_check_page: bad entry in directory #287: rec_l
en is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
EXT2-fs error (device ram0): ext2_check_page: bad entry in directory #261: rec_l
en is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
Kernel panic: No init found.  Try passing init= option to kernel."

I copied the spacing and line breaks as best I could.

I'm new to Ubuntu and Linux in general and have no idea what is wrong or how to fix it.  Any help you guys could give would be much appreciated.  (When I say new I've used UNIX before but a step by step would be the best way to help me out if possible)

Thanks,
Lifyre

[edit] I just found a related post searching.  Not sure why I couldn't find it before.  Hopefully it will resolve this problem [/edit]

[reedit]  The memory past ramtest in the past month and it does the same with a new install disk so the other posts didn't help me unfortunately.  Any ideas?[/reedit]

---

### Post by Lifyre on 2005-02-22
Setting the HDD mode to AUTO in BIOS fixed the GRUB error.  The default mode was LBA.

---

