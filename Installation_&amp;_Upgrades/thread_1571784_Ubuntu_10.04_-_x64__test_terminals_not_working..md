---
title: "Ubuntu 10.04 - x64:  test terminals not working."
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by KingGuru on 2010-09-10
I just made a fresh install of 10.04 x64, but none of the text terminals are functional. (ctrl + alt + F1 - F6). It's a fresh install, and right now I'm dooing an update. But last try that didn't help either. 
Am I missing something?

---

### Post by lechien73 on 2010-09-10
Does anything happen at all when you press Ctrl+Alt+F1-F6, or do you just get a black screen?

---

### Post by KingGuru on 2010-09-10
Well.. nothing happens..  except the cusor disappears :(

---

### Post by efflandt on 2010-09-10
Maybe your video chip/driver does not like the new default kernel mode setting (kms).  Try adding **nomodeset** as a kernel boot parameter.  From the grub2 menu I believe you press "**e**" to edit or add something temporarily to selected grub menu entry.

---

### Post by KingGuru on 2010-09-12
Ok..
I'll look into that. Though I'm using Nvidia GTX280 cards (2 of them in a SLI setup) and I thing that Nvidia is ok with lnx kernels

---

### Post by lechien73 on 2010-09-13
If you're getting a black screen with no cursor, then it could be a resolution issue.

[This article]("http://uri.tl/16") discusses how to fix the problem. It's primarily directed at Debian users, but seems to work for other Debian-based distributions as well.

---

