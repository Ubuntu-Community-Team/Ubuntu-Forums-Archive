---
title: "patch files"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by ashokmani on 2005-05-06
i am a newbie. 
how do i update a patch file provided in the ubuntu site.

the files are all .diff , wat i have to do to install these? 

Thanks

---

### Post by Professor X on 2005-05-06
Use that patch command to apply a diff file to something:

```
patch -p1 -i file.diff
```

Read the man page for patch for more info.

---

