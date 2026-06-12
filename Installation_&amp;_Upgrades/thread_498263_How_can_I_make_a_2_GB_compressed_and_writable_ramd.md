---
title: "How can I make a 2 GB compressed and writable ramdisk?"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by Finch75 on 2007-07-11
Hi everybody,

apparently, making a ramdisk is pretty easy, but "configuring" it is pretty hard?
Can anybody help me?

#1) The default size is ridiculously small (just a couple of MB). How can I change that? I tried adding "ramdisk_size=4000000" to the grub menu entry but that doesn't work :-( (I cannot format and use the ramdisk afterwards) (yes I am using a 64 bit version and I do have enough RAM :-)). Is there a size limit on ramdisks?

#2) I guess using ramfs/tmpfs would be easier but I want to use a compressed filesystem. And it should be writable. How do I do that? I've discovered that there is a compressed version of ext3. Is it enabled by default? Or what do I have to do if I want to use it?

#3) To make things a little harder I want to do all those things during the early boot process (initrd-phase). Of course I'll try it in a shell first. Just thought I should mention it :-)

A very first step would be a 4 GB UNcompressed ramdisk. That shouldn't be tooo hard (?). What do I have to do?

Thanks for any help!

---

