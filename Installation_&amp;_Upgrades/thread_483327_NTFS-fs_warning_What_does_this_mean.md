---
title: "NTFS-fs warning: What does this mean?"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2007-06-24
Using dmesg, got a log file that had the following messages at the end:

```
[  194.210244] NTFS-fs warning (device sdf1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  195.245206] NTFS volume version 3.1.
[  195.809220] NTFS-fs warning (device sdg1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  196.344388] NTFS volume version 3.1.
[  196.417526] NTFS-fs warning (device sde1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  196.705126] NTFS volume version 3.0.
```

What am I supposed to do?
What does it mean to use "option nls=utf8".

All 3 drives are external USB drives, formatted as NTFS.

---

