---
title: "&quot;Unusable&quot; space"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by Rakanishu on 2008-08-13
I have a 250 GB HDD, on which I have three Windows partitions prior to installing Linux.

I am running Linux with LiveCD, and I am trying to format the partitions manually. When I create a Linux partition, it says that the rest of the space is unusable. Which I find strange, since there's at least 10 GB left.
So now I can't create a swap file. Why is this and what can I do about it?

---

### Post by Partyboi2 on 2008-08-13
Have you created an extended partition? You can only have 4 primary partitions. So if you have not already done so, make a extended partition then under that make the ubuntu partitions

---

### Post by Rakanishu on 2008-08-13
That was the cause of this.
Thanks for the help.

---

