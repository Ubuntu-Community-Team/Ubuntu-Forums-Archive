---
title: "How to create extended partitions?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by FastMady123 on 2008-01-06
I need to have three partitions for Ubuntu. I have 2 Windows XP partitions. I don't want to nuke those because I want to keep Windows XP, but not destroy Windows. C drive is for Windows and files. D drive is for my computer and it need this partition. I need to create 3 partitions for Ubuntu. One is 5GB ex3, another one is 1GB linux-swap, and this last is the rest ex3. I want to keep Windows XP. What should I do?

Note: This is the second time I ask this question because there was a typo in the question's title.

---

### Post by logos34 on 2008-01-06
> **FastMady123 said:**
> I need to have three partitions for Ubuntu. I have 2 Windows XP partitions. I don't want to nuke those because I want to keep Windows XP, but not destroy Windows. C drive is for Windows and files. D drive is for my computer and it need this partition. I need to create 3 partitions for Ubuntu. One is 5GB ex3, another one is 1GB linux-swap, and this last is the rest ex3. I want to keep Windows XP. What should I do?

Note: This is the second time I ask this question because there was a typo in the question's title.

During install choose 'manual' option to partition disk.  Create one big extended partition in free space and then put /, /swap and the other inside as logical partitions.  (might want to consider making the last one a separate /home)

---

