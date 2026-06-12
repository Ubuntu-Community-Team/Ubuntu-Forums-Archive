---
title: "kernel panic -- can't find root"
date: 2006-05-20
forum: Installation &amp; Upgrades
---

### Post by uh-huh on 2006-05-20
Hi forum,

I just did a default install on a PIII VIA chip box. And it boots into a kernel panic.

I'm using four partitions like this: /dev/hdc1, ext2 /boot, 50M; /dev/hdc2, swap 500M; /dev/hdc3, reiserfs, /; /dev/hdc4, reiserfs, /home.

I'm using a GRUB boot floppy until I get everything to work OK.

I note in /dev/hdc3 are sym-links to /boot for vmlinuz and initrd but when I try to use them: Error 15 file not found.

grub>root (hd1,2)
grub>kernel /vmlinuz initrd=/initrd.img root=/dev/hdc3
   Error 15: file not found.

so I try

grub>root (hd1,0) #OK, it sees the image
grub> kernel /vmlinuz-2.6.12-9-386 initrd=/initrd.img-2.6.12-9-386 root=/dev/hdc3 #OK it sees /

(not sure if I got those version numbers right, but you get the idea)

grub>boot
...booting the kernel...
Panic!

I've booted with the installCD to look at the kernel config to make sure there's a [*] instead of [M] next to reiserfs under filesystems but /usr/src is empty!

How do I fix this thing?

uh-huh

---

