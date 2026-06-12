---
title: "grub error 25 in stage 1.5 (solved)"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by larschri on 2006-08-17
Just wanted to share my experience on this one, since I wasn't able to find the answer here.

Ubuntu installation succeeded, but grub was not able to find any partitions during boot. Debugging with a grub shell from a floppy told me that hd0 was found, but no partitions. In the grub shell:

```

> root (hd0, #pressing tab here listed nothing.
> root (hd1, #pressing tab here listed my windows partitions.
```

I think it was caused by some hardware conflict, because it worked just fine when I (more or less randomly) re-arranged my IDE-hardware. So my advice on similar problems would be to remove any extra hardware, check if it works, and put it back one by one.

---

