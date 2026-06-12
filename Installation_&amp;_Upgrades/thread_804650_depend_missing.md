---
title: "depend missing"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by grizzlysmit on 2008-05-23
Hi I installed a program called chmsee from the repositories, it's supposed to read .chm files, when I run it it gives me an error that it cannot find libxul.so ](*,) I cannot find libxul.so in the repositories shouldn't it be there, and shouldn't it be a dependency of chmsee ??

---

### Post by bwhite82 on 2008-05-23
Install the package "libxul-dev" which with install a few others and you should be all set. I would also file a bug report on this as chmsee should have asked you to install these dependencies.

---

### Post by grizzlysmit on 2008-05-26
> **Soldierboy said:**
> Install the package "libxul-dev" which with install a few others and you should be all set. I would also file a bug report on this as chmsee should have asked you to install these dependencies.

OK I installed libxul-dev but it still doesn't work now I get the following error, chmsee: symbol lookup error: chmsee: undefined symbol: gtk_moz_embed_set_comp_path thats 2 bugs how do I report bugs 
mind you I have an alternative I found a program call xchm to read .chm files

---

