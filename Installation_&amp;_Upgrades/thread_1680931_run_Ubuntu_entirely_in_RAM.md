---
title: "run Ubuntu entirely in RAM"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-02-03
Has anyone built this, or is anyone working a such a project?

The goal is to structure an Ubuntu system (either desktop or server), staged on one (maybe virtual) machine, with added packages, upgrades, and local modifications as desired, and build it into an image that can be written to a DVD or USB memory stick, that when booted, loads everything (e.g. /usr and such) into RAM, and runs it from RAM.  Netbooting into this would also be nice.  Configuration changes (like what goes in /etc) would be done by changing that staging system and rebuilding the image to boot.  Persistent live data (e.g. log files in /var) might either be kept in RAM (and thus lost when shutting down), via NFS, or on a real disk as usual.

It looks like I'd eat up about 4GB of RAM for this for my typical configurations.  I can add 4GB or more to the target machines.

One goal is to have a hardened system that can't be modified (e.g. use DVD+R), and thus will always come up.  Another goal is to be able to update complex configurations on remote machines by just shipping a DVD or transferring an image for someone there to burn onto a DVD.

---

### Post by psusi on 2011-02-03
Add the toram boot parameter.

---

### Post by Skaperen on 2011-02-03
> **psusi said:**
> Add the toram boot parameter.
And how does this get onto the boot media?

---

### Post by psusi on 2011-02-03
If you want it to be the default then you will need to build your own custom image and add that argument to the syslinux default argument list.  There was a wiki entry on how to build a custom image, but the search seems to be broken again.

---

### Post by Skaperen on 2011-02-03
Where does "toram" put /var ?

---

### Post by psusi on 2011-02-03
> **Skaperen said:**
> Where does "toram" put /var ?

Nowhere?

It just copies the cramfs image from the cd to /tmp.

---

### Post by C.S.Cameron on 2011-02-03
Following is a discussion on the subject of Ubuntu in Ram including a script to do so.

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

### Post by Skaperen on 2011-02-03
> **psusi said:**
> Nowhere?

It just copies the cramfs image from the cd to /tmp.
Ah, so this is part of the distributed ISO setup.  How well does that work rebuilding it from a hard drive based system used to stage in the added packages, configuration, and local modifications (for example lots of static IP addresses).

These machines WILL have a hard drive or two or twenty or so.  I just want to move the OS itself so it is not running from the hard disk, and probably not even loaded from the hard disk.  This isn't for administrative rescue purposes ... it's to be run as live production this way.

How fast is total extraction from cramfs, as compared to something like extracting from cpio.gz?  If cramfs is slower, it might be better to hack this to store all that in a cpio.gz file instead.

I assume you mean tmpfs or ramfs when you said /tmp.  I want to have /tmp itself be on the hard drive, along with /home.  That tmpfs or ramfs should then be the / mount point.

---

### Post by psusi on 2011-02-03
I have never built a custom image so I'm not sure about the details.  Yes, it probably uses some other tmpfs rather than /tmp.  It is actually a squashfs which is not extracted, but mounted directly and the files are decompressed on the fly when accessed.  The toram argument just copies the file to a tmpfs and mounts it there instead of from the cd.

---

### Post by Skaperen on 2011-02-03
> **psusi said:**
> I have never built a custom image so I'm not sure about the details.  Yes, it probably uses some other tmpfs rather than /tmp.  It is actually a squashfs which is not extracted, but mounted directly and the files are decompressed on the fly when accessed.  The toram argument just copies the file to a tmpfs and mounts it there instead of from the cd.
I found reference to "toram" in the live-build package from the Debian project.  I installed it from the Ubuntu repo to check it out.  Is that what you were referring to?

So far it looks like it tries to build a system by actually installing packages at the time you build it.  That alone won't work for me, as I need to tweak a LOT of things after that.  But there might be other hooks to do that through, and other "less common" options to take a system from an existing file tree instead of building one.  If I go with this, I'd expect to be building these live images VERY frequently, and I sure would not want to be pulling them from the network every time, or having a package version just change on me some day.  So I might need my own unsynced repository.  But it would be a lot better if it can build from a given root tree (like a package I made many years ago did ... it took 2 root trees, one for i386 and one for sparc, and made a single dual-arch ISO).

---

### Post by uyuy on 2011-04-05
I am trying something based on similar idea and test with some difficulties, just share here in this discussion. I mount ramfs & copy vmware.com virtual machines inside and tried. There is a difficulty however that vmware says "no more space left in..." 
I checked with df -ha command and discovered that df reported all the mounted ramfs as ZERO size regardless of how many GB I had defined in my mount statement.
This I suspect is a df issue or ramfs issue.

vmware's vmdk virtual disks are file or files emulated as disks. entire image of OS; settings; data etc are inside. As long as we can solve the ZERO size issue, we can have vmdk virtual disks in ram, to run them fast.

Does any one know the ramfs df issue?

---

### Post by Skaperen on 2011-04-20
> **uyuy said:**
> I am trying something based on similar idea and test with some difficulties, just share here in this discussion. I mount ramfs & copy vmware.com virtual machines inside and tried. There is a difficulty however that vmware says "no more space left in..." 
I checked with df -ha command and discovered that df reported all the mounted ramfs as ZERO size regardless of how many GB I had defined in my mount statement.
This I suspect is a df issue or ramfs issue.

vmware's vmdk virtual disks are file or files emulated as disks. entire image of OS; settings; data etc are inside. As long as we can solve the ZERO size issue, we can have vmdk virtual disks in ram, to run them fast.

Does any one know the ramfs df issue?
The ramfs design is based on extreme simplicity.  There is no backing store.  Essentially, the pages stored in ramfs are waiting to be moved out to backing store ... but it is never available so they just wait forever.  You get zero because that actually is the size of the backing store.  Maybe a feature, enabled via something in /proc, could map the amount of space queued to fake the backing store information safely to user space without confusing the kernel.  It should be /proc enabled because it might confuse some user space programs that expect these zeros.  Based on reading a post about it that Linus wrote, ramfs is basically half a filesystem.

You could use tmpfs.  It seems to work.  It does use swap as backing store, so if swap is enabled, it can use it.  But, if you have no swap, tmpfs should be effectively the same as ramfs, but I think it will show the numbers.

---

