---
title: "renaming bookmarks in nautilus bug"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-04-25
Seems to be some regression now in nautilus regarding renaming of bookmarks.

If i bookmark a remote sftp location and rename it the bookmark name does not change. In the past, once I restarted nautilus the bookmark name would change but now it seems to exhibit this behaviour temporarily and then it loses the renamed folder again.

---

### Post by dino99 on 2010-04-25
have just tried to see what happen: no trouble on my end. Try sudo dpkg-reconfigure nautilus

---

### Post by sonicb00m on 2010-04-25
[https://bugs.launchpad.net/nautilus/+bug/549707?comments=all](https://bugs.launchpad.net/nautilus/+bug/549707?comments=all)

looks like a confirmed bug. will try your tip.

---

### Post by sonicb00m on 2010-04-25
Didn't help. If you rename it in the bookmarks menu it works first time but if you hit F2 and rename it the problem still exists.

Did you test this with a remote sftp location?

---

