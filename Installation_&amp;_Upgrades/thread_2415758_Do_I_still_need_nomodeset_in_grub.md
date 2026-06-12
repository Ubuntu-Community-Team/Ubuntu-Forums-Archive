---
title: "Do I still need nomodeset in grub?"
date: 2019-03-31
forum: Installation &amp; Upgrades
---

### Post by headlessspider on 2019-03-31
Hi folks,

I've been running 18.04 since they released it. Since that version does not have the intel video drivers anymore, the only way I can run is when nomodeset was added to the command line:

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

I read somewhere that nomodeset is a temporary fix but I don't have proprietary video drivers running. I just have the llvmpipe (LLVM 7.0, 256 bits).

Can I just edit out the nomodeset?

Thanks folks!

---

### Post by Bashing-om on 2019-03-31
headlessspider; Yuk -

I can not imagine that Intel graphics are not supported.
Show us the hardware:
```

lspci -vnn | grep VGA -A 12

```
See then what we can do.

[INDENT][INDENT]gotta be a way - it's 'buntu
[/INDENT][/INDENT]

---

