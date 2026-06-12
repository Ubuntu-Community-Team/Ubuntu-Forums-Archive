---
title: "install from iso, howto won't do"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by timcriger on 2007-04-22
I've followed the instructions on how to install Feisty from the .iso file [here ]("https://help.ubuntu.com/community/Installation/FromLinux").
However, i'm getting this error when the ubuntu cd tries to boot from grub:

"I/O error: dev/fd0"  or something like that.
Am i right in thinking it's trying to access a (non-existent) floppy drive?

I have extracted the contents of the feisty cd to /dev/hda4/Ubuntu704CD/
My GRUB menu.lst appears as below:

> title Ubuntu 7.04CD
        root (hd0,3)
        kernel /Ubuntu704CD/casper/vmlinuz boot=casper root=/dev/ram0 ramdisk_size=1048576 rw
        initrd /Ubuntu704CD/casper/initrd.gz

I've heard talk of needing an alternate vmlinuz and initrd.gz for this kind of install... is this correct? Or are those in the /casper/ folder in the Feisty cd made for this install?

Thanks for your help in advance,

Tim

---

### Post by timcriger on 2007-04-22
(see above)

---

### Post by timcriger on 2007-04-26
help please...

---

