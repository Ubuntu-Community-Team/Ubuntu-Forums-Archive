---
title: "file system"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by dagerftw on 2008-08-31
i recently screwed up my windows by uninstalling IE7 which deleted an insane amount of very essential dll's that i cant fix. no xp cd anymore so no dual booting or anything. well anyway I am currently formatting it and will be putting ubuntu on it. since i only have access to her windows machines i dont know what file system is best for ubuntu. i can ony reformat to NTFS from a vista machine. sorry if this is posted somewhere else but im not good with forum search tools, but what file system is best for ubuntu and if its possible, how do i put that file system on the harddrive using vista. thanks

-dager

---

### Post by eyyou101 on 2008-08-31
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by mytwobears on 2008-08-31
You can use the ext3 file system.  The Ubuntu installation CD will format the drive for you during installation.  You cannot and should not try to do it from windows.  The Ubuntu installation CD will take you through the process and it's pretty straightforward.

Hope that helps.

---

### Post by manishtech on 2008-09-02
Use **ext3** for installing ubuntu, additionally you need one more partition for managing OS swap memory. This should be around 700MB-1GB and should be formatted with filesystem **linux-swap**

Apart from ext3 you can also try out **reiserfs** which is also very good. I use it on my system.

---

