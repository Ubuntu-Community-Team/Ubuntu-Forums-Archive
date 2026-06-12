---
title: "Recover HFS+ Data After Ext3 Format??"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by jmcbri on 2010-02-06
I was interested in setting up my Mac G5 as dual boot and used the PowerPC distro to begin that process.  Apparently I'm more newbie than I thought, because I managed to repartition the disk, not just resize and setup for dual boot.  

I think I have most of the data from the partition backed up, but I'd still very much like to see what I can recover from the disk that is now not partitioned as HFS+ (or at least it fails to mount in OS X, but the structure isn't what I'd expect for a Linux box, so apparently I caught it before it went too far).

Ideally, I'd like to do something with free (cost) tools.  I already tried the OS X Disk Utilities and it doesn't even want to look at the disk.

---

### Post by jmcbri on 2010-02-06
Problem not solved yet, but I'll tell you, this looks like a very powerful set of tools:

(Testdisk and photorec)

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Let's see how it works.

---

### Post by jmcbri on 2010-02-09
So how's it going you ask?

Well, it's taken this long just to get the image pulled off the drive so that I felt that I could work on it. 

Lesson - If you use ddrescue and you rescue to a NTFS partition, ddrescue begins to slow dramatically until it's doing almost nothing.  Rescue the image file to a ext2 or ext3 partition.  Goes MUCH faster.  Why?  Don't know.  It just did.

Maybe tomorrow I'll see what I can do to restore the partition.  More then.

---

### Post by jmcbri on 2010-02-20
I was able to recover a bunch of files using PhotoRec, but not suprisingly, there neither named nor in folders and so the value is limited for my  "use case" (love the new and still worthless buzz words).  

I downloaded r-studio for mac cd-bootable.  It's scanning the disk now.  Maybe worthwhile maybe not.  After all, I think I have most of the files backed up, but you never know.

More later.

---

