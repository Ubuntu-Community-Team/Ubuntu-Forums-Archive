---
title: "GRUB troubles"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by SigmaX on 2007-01-27
Hey; I'm trying to get Ubuntu 6.10 installed on my MacBook Core Duo *without* using rEFIt.  I already had Fedora working on it fine with Grub.  However, Fedora is no Ubuntu, even if they do have Compiz working out of the box -- so I whiped the Fedora partition this afternoon ;-).

I've installed Ubuntu already, but, as expected, it failed at the very end installing Grub on (hd0).  That's fine, I didn't want it on hd0 anyway, since I'm using Boot Camp.  I rebooted on the hopes that the Fedora GRUB was still intact (It wasn't), and now I'm back on the Edgy LiveCD.

So, here's the scoop:

```
$ sudo mount /dev/sda2 /mnt/root/
$ sudo mv /mnt/root/dev /mnt/root/dev2
$ sudo mount -o bind /dev /mnt/root/dev
$ sudo chroot /mnt/root /bin/bash
# grub-install hd0,1
The file /boot/grub/stage1 not read correctly.
```

Googling around I found Gentoo stuff.  Apparently they patch grub "0.97-r2" or use "0.97-r3" to get around a similar error.  Is the r2/r3 thing a Gentoo-specific release/patch indicator?  Ubuntu uses 0.97 straight.

Anyway, I just wanted to see if anyone had some tips before I take the time to try and patch Grub.

SigmaX

---

### Post by SigmaX on 2007-01-27
Ha!  I found a pre-patched Ubuntu package and tarball [here]("http://www.scl.ameslab.gov/Projects/mini-xen/index.html").

But still no luck.  Even after manually replacing the stage2 tarball, wherein the problem lies, I still get the same error.

Trying grub instead of grub-install:
```

grub> root (hd0,1)

Error 22: No such partition

grub> root (hd0,0)

grub> quit
```

Grub can't even read my second partition!  Now that's bogus :-(.  But, strangely enough, neither can fdisk:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7296    58605119+  ee  EFI GPT
/dev/sda2               1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
```

The table displays fine in parted, though:
```

Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  210MB   210MB   fat32        primary  boot 
 2      210MB   21.2GB  21.0GB  ext3         primary  boot 
 3      21.2GB  46.3GB  25.2GB  ext3         primary       
 5      46.3GB  48.7GB  2315MB  linux-swap   primary       
 6      48.7GB  60.0GB  11.3GB  ntfs         primary
```

ARG!

SigmaX

---

### Post by geek_Man on 2007-01-27
Can you access these other drives?

---

### Post by SigmaX on 2007-01-28
Just (hd0,0).  I can mount everything fine, however.

SigmaX

---

### Post by geek_Man on 2007-01-28
Like in Nautilus (or Konquerer). Can you open up that partition and look at the files and stuff?

---

### Post by SigmaX on 2007-01-29
Yes.  I can mount and use all the partitions normally.  I've been using the livecd to take notes in class and save them to /dev/sda3, in lack of a working installation.  (the livecd sure works great!  Scanner, camera, wireless -- everything works out of the box :-D).

SigmaX

---

