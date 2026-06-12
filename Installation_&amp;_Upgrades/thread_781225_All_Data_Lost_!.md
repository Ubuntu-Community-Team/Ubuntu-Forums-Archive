---
title: "All Data Lost !"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by JayPidgee on 2008-05-04
Hi everybody,

I just install Ubuntu but I made a mistake so WIdnows XP and all HD data are lost, pictures, movies documents,etc

Is there any recovery software to recover most of them ?

Thanks for any advice

JP

---

### Post by ajmorris on 2008-05-05
hi there,
are you absolutely  positive all data is gone? what is the output of ```
sudo fdisk -l
```
But, if a partition has been written over the top of where the windows XP one was, then unfortunately, no, there is no way to get it back, if the blocks that XP was on, have not been touched, there is a slight chance we could get it back....


AJ

---

### Post by kellemes on 2008-05-05
[PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

Edit: Also see [TestDisk]("http://en.wikipedia.org/wiki/TestDisk").

---

### Post by logos34 on 2008-05-05
Yeah, TestDisk and Photorec.  Testdisk will dig down many layers if necessary to find the previous partition. Scans still turn up old buried ntfs layers I have overwritten with ext3 long ago. Getting all your data back is another issue. But hopefully you'll be able to recover most of it.

---

