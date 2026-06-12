---
title: "kernel version - stored in which files?"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by melonenmelli on 2007-09-14
hello

im wondering in which files my kernel "ID" is stored in. e.g. "2.6.20.10-generic".

I would like to install a custom kernel (HDAPS-support) and give it a "official" ubuntu identification.

If it would be possible to install a custom kernel with a revisionsnr. like "2.6.20.11-generic", it would be a nice workaround for troubles with the restricted driver module.

Does anybody know what files i have to edit to get this ID-string?

thanks in advance!

---

### Post by splintercellguy on 2007-09-14
I would imagine that the information uname outputs is queried from the kernel.

---

### Post by melonenmelli on 2007-09-14
yes i know...
"uname -r" gives me this information, but i would like to know how to SET this information.

to generate deb-files from a compiled kernel i usually do:

```
sudo make-kpkg --initrd --revision="some string" binary
```

i could set the "revisio-parameter" to e.g. "2.6.20.11" but i dont think that would work properly.

i read in the make-kpkg-man-files about some other files that may have to be edited.

but im quite unsure about this....

---

### Post by melonenmelli on 2007-09-14
yes i know...
"uname -r" gives me this information, but i would like to know how to SET this information.

to generate deb-files from a compiled kernel i usually do:

```
sudo make-kpkg --initrd --revision="some string" binary
```

i could set the "revisio-parameter" to e.g. "2.6.20.11" but i dont think that would work properly.

i read in the make-kpkg-man-files about some other files that may have to be edited.

but im quite unsure about this....

---

