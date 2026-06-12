---
title: "WUBI - windows files on same disk not accessible"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by yosibeck on 2008-04-25
I have installed Hardy with WUBI in my Vista system.
I have a laptop with two 100GB disks.
The first hard disk is the Vista boot disk, on the second one I keep my most of my Vista docs, pictures etc and there I also installed the Hardy WUBI which I gave 30GB.
The Ubuntu system runs just fine, but I have one big problem:
The first hard disk is mounted and I can access all that's on it.
However, I cannot find the windows files and docs on the second disk where Hardy is installed with WUBI. that disk has 100GB, of which only 30GB is WUBI and as I mentioned above, the rest (70GB) is regular windows with all my documents, pictures and videos.
Under "filesystem" I only find my Ubuntu files, no sign of windows.
How do I access the window files on the disk where my WUBI Hardy is installed?
Thanks,
Yossi

---

### Post by tormod on 2008-04-25
If you are using another locale than C, it might be related to [https://bugs.launchpad.net/bugs/136682](https://bugs.launchpad.net/bugs/136682)

The disk where WUBI is installed is available under /host IIRC.

---

### Post by yosibeck on 2008-04-27
indeed under /host I found it all. No bugs. Just my ignorance...
Thanks.

---

