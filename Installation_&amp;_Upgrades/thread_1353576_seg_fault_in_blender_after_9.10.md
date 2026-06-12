---
title: "seg fault in blender after 9.10"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-12-12
ok i used blender in 9.04 and then i clean installed 9.10. After installing it i clicked on tghe icon and nothing happend. I than ran it in terminal and got a segfault message, any clues.

---

### Post by buntubunny on 2009-12-26
Are you using an ATI Radeon graphics card?

If so, it seems to be a bug in the mesa package.

You may wish to refer to this bug report thread: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/446632](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/446632)

If you have an ATI Mobility Radeon 9000 graphics card, then perhaps the workaround on post #49 in that thread will work for you.

---

