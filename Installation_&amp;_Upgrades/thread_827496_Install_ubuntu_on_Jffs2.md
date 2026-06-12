---
title: "Install ubuntu on Jffs2"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by lfaraone on 2008-06-12
Can Ubuntu be installed on a jffs2 partition? (spesifcally the OLPC XO, but that's another ??)

---

### Post by dstew on 2008-06-13
Good question. I know that you can get Ubuntu to mount a jffs2 file system after installing some kernel modules (see [this thread]("http://ubuntuforums.org/showthread.php?t=432481")). However, I do not know if you can actually install the system to this file system type. I know that Ubuntu can read FAT32 file systems, but because of the permissions structure, I don't think you can install Ubuntu to a FAT32 file system.

---

### Post by lfaraone on 2008-06-13
> **dstew said:**
> Good question. I know that you can get Ubuntu to mount a jffs2 file system after installing some kernel modules (see [this thread]("http://ubuntuforums.org/showthread.php?t=432481")). However, I do not know if you can actually install the system to this file system type. 

Well,
I'm using a BIOS that can load a kernel from such a partition, and I'm not using ubuntu's kernel (as it does not load on the XO's custom hardware), I am instead using a kernel which should, in theory, support jffs2. Can I just 
```
cp /media/ubuntu /media/jffs2
```
where /media/ubuntu is mounted my ubuntu partition?

Thanks.

---

### Post by dstew on 2008-06-13
I do not doubt that the files can be copied. I just don't know if jffs2 will support the permissions and file-name properties that Ubuntu expects to see when it runs. I don't have any hands-on experience with jffs2. I could not find an posts where someone had Ubuntu up and running on jffs2. Maybe some Linux distributions that are made for imbedded systems would work, I just don't know.

But, you could try it and see what happens, and report back...

---

### Post by Habbit on 2008-06-13
> **ffm said:**
> Can I just 
```
cp /media/ubuntu /media/jffs2
```
where /media/ubuntu is mounted my ubuntu partition?
That would not work even with a normal FS, since you are not preserving permissions and/or special attributes. The best maneuver for this kind of ordeals is usually piping two instances of tar which are using the -p flag to preserve permissions. I remember there was also a cp flag for it, but I no longer remember it.

Usually, if a filesystem can support the POSIX permission architecture (or even better features, like ACLs), it should be possible to run use it as a root fs. This said, I haven't yet seen a Linux installation using NTFS as its root filesystem (Wubi doesn't cound since its root is a normal Linux fs, not matter it's a file on a NTFS partition).

---

