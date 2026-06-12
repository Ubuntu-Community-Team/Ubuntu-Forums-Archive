---
title: "cannot mount cryptoloop encrypted cdrom in feisty"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by charly4711 on 2007-06-26
Hi there,
have a bunch of cdroms with iso9660 file systems on them with content encrypted with cryptoloop on my machine before I upgraded from edgy to feisty. I can no longer mount them on feisty. Before I am even asked for the encryption key, the mount command returns "No medium found",

I created them like this:
```
dd if=/dev/zero of=/bla/neues-iso.iso bs=1000 count=xyz
losetup -e aes /dev/loop0 /bla/neues-iso.iso
cat altes-iso.iso > /dev/loop0
losetup -d /dev/loop0
mount -o loop,encryption=aes /bla/neues-iso.iso
```
wrote the iso to cdrom and always use to be able to mount it.

Ah, and of course I did modprobe for aes_i586, loop, and cryptoloop.

Any ideas?

---

### Post by hes on 2007-07-27
> **charly4711 said:**
> Hi there,
have a bunch of cdroms with iso9660 file systems on them with content encrypted with cryptoloop on my machine before I upgraded from edgy to feisty. I can no longer mount them on feisty. Before I am even asked for the encryption key, the mount command returns "No medium found",

I created them like this:
```
dd if=/dev/zero of=/bla/neues-iso.iso bs=1000 count=xyz
losetup -e aes /dev/loop0 /bla/neues-iso.iso
cat altes-iso.iso > /dev/loop0
losetup -d /dev/loop0
mount -o loop,encryption=aes /bla/neues-iso.iso
```
wrote the iso to cdrom and always use to be able to mount it.

Ah, and of course I did modprobe for aes_i586, loop, and cryptoloop.

Any ideas?

Maybe You should specify additional option (-N) in losetup. I had similar problem with disks transfered from FC6

---

