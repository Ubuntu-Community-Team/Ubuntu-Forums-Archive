---
title: "kio_file slow copy speed."
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by siegi on 2009-10-05
I'm using kubuntu karmic 64 bit, with ext4 and a encrypted home. (ecryptfs)
When I copy, much files using dolphin (kio_file), the computer becomes (unusable) very slow.
When I copy, much files using command line (cp), i don't have any problem.

When i compare the copy speed between cp and kio_file, cp is much faster.
When I compare the cpu usage between cp and kio_file, kio_file uses much more cpu. (wa: 80% in top)

The only difference, i can think about is that, kio_file constantly updates the status of the copy proces.
I have tried this in ubuntu using nautilus (gvfs), and this works normally.

I've opened a bug report about it:
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/443122](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/443122)

---

