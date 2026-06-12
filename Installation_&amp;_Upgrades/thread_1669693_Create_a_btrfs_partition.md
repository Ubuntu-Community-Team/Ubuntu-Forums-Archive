---
title: "Create a btrfs partition?"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by ario on 2011-01-18
Since gparted don't know how to create a btrfs partition on 10.10 live CD, I wonder how can I do it by hand. The question is with which commands and how I can create a new btrfs partition?
Thanks for your attention guys:)

---

### Post by dino99 on 2011-01-18
from synaptic, about btrfs-tools:

This package contains utilities (mkfs, fsck, btrfsctl) used to work with btrfs
and an utility (btrfs-convert) to make a btrfs filesystem from an ext3.

WARNING: Btrfs is under heavy development, and is not suitable for any uses
other than benchmarking and review.

PartedMagic can directly deal with btrfs:
[http://partedmagic.com/doku.php?id=programs](http://partedmagic.com/doku.php?id=programs)

---

### Post by srs5694 on 2011-01-18
The generic command for creating a filesystem is:

```

mkfs -t fscode /dev/whatever

```

Change "fscode" to a suitable filesystem code (ext2, reiserfs, btrfs, etc.) and "/dev/whatever" to your device filename (/dev/sda2, /dev/sdc7, etc.).

Thus, to create Btrfs on, say, /dev/sda2, you'd type:

```

sudo mkfs -t btrfs /dev/sda2

```

This assumes that you've got the appropriate helper programs installed (btrfs-tools, as dino99 mentioned). There are also various generic and filesystem-specific options you might want to use. Read the man pages for mkfs and the helper program (mkfs.btrfs, at least on my Gentoo system -- it may be different in Ubuntu) for details.

Btrfs is still considered experimental, as dino99 emphasizes. FWIW, I'm using it as my root filesystem on a laptop and it's seemed fine until recently, when I've started getting subjectively poor disk performance. I've not yet investigated to find out if this is real, though; it could be I'm imagining things.

---

### Post by ario on 2011-01-21
> **srs5694 said:**
> The generic command for creating a filesystem is:

```

mkfs -t fscode /dev/whatever

```

Change "fscode" to a suitable filesystem code (ext2, reiserfs, btrfs, etc.) and "/dev/whatever" to your device filename (/dev/sda2, /dev/sdc7, etc.).

Thus, to create Btrfs on, say, /dev/sda2, you'd type:

```

sudo mkfs -t btrfs /dev/sda2

```

This assumes that you've got the appropriate helper programs installed (btrfs-tools, as dino99 mentioned). There are also various generic and filesystem-specific options you might want to use. Read the man pages for mkfs and the helper program (mkfs.btrfs, at least on my Gentoo system -- it may be different in Ubuntu) for details.

Btrfs is still considered experimental, as dino99 emphasizes. FWIW, I'm using it as my root filesystem on a laptop and it's seemed fine until recently, when I've started getting subjectively poor disk performance. I've not yet investigated to find out if this is real, though; it could be I'm imagining things.
Thank you all guys.
Decided to not create btrfs partitions, cause many programs still not support it well (e.g. firefox, dpkg). The old fsync function which is widely used in linux applications have problems with btrfs which causes whole system hang after hang.
For now installed an Ubuntu 10.10 on my 16GB SD card using traditional ext2 format.

---

