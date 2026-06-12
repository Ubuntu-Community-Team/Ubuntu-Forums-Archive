---
title: "Mounting/editing initrd.img"
date: 2005-01-01
forum: Installation &amp; Upgrades
---

### Post by Random Juju on 2005-01-01
Hello.

I'm having the problem described in [https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496) and [https://bugzilla.ubuntu.com/show_bug.cgi?id=3363](https://bugzilla.ubuntu.com/show_bug.cgi?id=3363) (it's happening to my new installation).  It sounds like I can fix things by manually editing my initrd image, but I'm not sure how to mount it.  I'm trying things like `mount -o loop -t romfs initrd.img ./temp` but I get answers like:

"mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       or too many mounted file systems
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)"

File says this about the initrd.img file:  "initrd.img: Linux Compressed ROM File System data, big endian size 4329472 version #2 sorted_dirs CRC 0xf26018f8, edition 0, 2468 blocks, 236 files"

Any hints?  I have romfs support built into the kernel (on another box) that I'm trying to use to mount this.  Thanks!

---

### Post by Random Juju on 2005-01-02
So some further poking and lots of help from the wonderful #ubuntu people has turned up some new details:

# mount -o loop initrd.img initrd
ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type

Despite the error, /dev/loop0 is used:

# losetup /dev/loop0
/dev/loop0: [0304]:11313838 (initrd.img)

Attempting to mount the loopback device directly (either the one used by mount or one used by losetup) doesn't work:

# mount -t cramfs /dev/loop0 initrd
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       or too many mounted file systems

 # mount /dev/loop0 initrd
mount: you must specify the filesystem type

The cramfs module is loaded when I try all of this.

Any thoughts?

Thanks!

---

### Post by Random Juju on 2005-01-03
I guess this is semi-resolved -- tried doing exactly the same thing on another machine and it worked just fine.

---

