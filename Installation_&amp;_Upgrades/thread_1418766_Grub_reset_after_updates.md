---
title: "Grub reset after updates?"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by jesseafrantz on 2010-03-01
I recently installed Ubuntu 9.10 through "Wubi" I installed all it's updates. Now when I go to boot it up GRUB is completely reset? it says something about bash-line or something, something not regarding Linux or Ubuntu. Anyone else get this problem or know any fixes?

---

### Post by meierfra. on 2010-03-01
Sounds like you got hit by this bug:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by michaelhoward78 on 2010-03-01
Thanks for the tip, going into windows to try this. will post results in a few.

---

### Post by jesseafrantz on 2010-03-01
> **meierfra. said:**
> Sounds like you got hit by this bug:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


 Thanks for the link, it's very clear on the problem and how to fix it. Basically you need to go in and replace a file called "wubildr" in your C:\ Drive on your NTFS partition.

---

### Post by michaelhoward78 on 2010-03-01
YES. Thank you. This worked. I used the live cd to download and copy the file due to the fact that windows cant get online(no drivers for wireless).

Will this bug be fixed soon or should I not update again til 10.04?

---

### Post by michaelhoward78 on 2010-03-01
Hey jesseafrantz if this worked for you, you might want to mark this thread as solved so others can use it.

---

### Post by meierfra. on 2010-03-01
> Basically you need to go in and replace a file called "wubildr" in your C:\ Drive on your NTFS partition. 

Exactly.

> Will this bug be fixed soon 
By replacing the wubildr you fixed the problem. So   updates should no longer  cause problems.

---

