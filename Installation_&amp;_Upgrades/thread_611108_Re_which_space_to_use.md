---
title: "Re: which space to use?"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by PinkyGifford on 2007-11-12
Hello,

I want to install Ubuntu 7.10 - Here is what my space looks like after un-insalling Kubuntu 7.10 :

Vista- C: 47.74 GB NTFS

25.64 GB - Unallocated

1.15 GB - Free Space

I have an  80 gig hard drive, Can I install Ubuntu 7.10 on the unallocated space if so how would I do this? Would i have to use _Manual_ when it comes to the partioning part of the CD to locate the unallocated space.

Easy instructions would be helpful  :)

Thanks

---

### Post by taurus on 2007-11-12
Use gparted from the LiveCD and format that unallocated space to ext3.  Then, tell the installer to use that space, NOT the whole harddrive or bye-bye Vista.

---

### Post by PmDematagoda on 2007-11-12
You can use the installer's partitioner itself to format the unallocated space to ext3 and use it the way you want without having to do it through Gparted.

---

