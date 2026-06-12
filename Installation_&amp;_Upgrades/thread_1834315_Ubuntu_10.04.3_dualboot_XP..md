---
title: "Ubuntu 10.04.3 dualboot XP."
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by Swedish Berserk on 2011-08-27
Hello! I have been trying to dualboot Ubuntu with XP. The problem is that i dont get the install side by side option. I have defraged the computer but no luck. How can i solve this problem?

---

### Post by dino99 on 2011-08-27
try to grab free room on xp, then:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by oldfred on 2011-08-27
Have you used all 4 primary partitions? Post this from liveCD, copy & paste:

```
sudo fdisk -lu
```

---

### Post by Swedish Berserk on 2011-08-27
Hi again! It worked! I shrinked the XP partition with third party application. XP cant do it native. Then i installed Ubuntu on the free space! Simple! Thanks for your help dino99 och oldfred!

---

