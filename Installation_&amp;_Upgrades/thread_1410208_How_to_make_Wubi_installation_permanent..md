---
title: "How to make Wubi installation permanent."
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by stevh0 on 2010-02-18
I installed Ubuntu 904 through wubi a couple of months ago and everything is working sweet. Now, id like convert the whole setup to a local ext filesystem and keep my current ubuntu installion.

Basically I want to ditch vista and keep Ubuntu...

any ideas or will I have to start from scratch?

---

### Post by meierfra. on 2010-02-18
You can use lubi to  convert Wubi to a regular install:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

According to that link, lubi only has been tested for Wubi 8.04 and older. But from what I read in this [thread ]("http://ubuntuforums.org/showthread.php?t=438591") it also works for Wubi 9.04 except that you will have to manually edit "boot/grub/menu.lst" afterwards.

---

