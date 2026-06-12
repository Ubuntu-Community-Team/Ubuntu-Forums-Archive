---
title: "Ubuntu rights (files and directories) problem"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by lipstick31 on 2010-12-22
Hello , I am an ubuntu dammie user. I'm building something in ubuntu and i have the following problems
 
I create some directories (with mkdir command) and some files (copy paste). After these operation i set chmod 755 to the files and chown username to the directories. All work ok .
But after editing of these files , the files turn again to locked mode and i cannot edit them . So i must chmod 755 to the files or chown srv to the files
 
Is there any way to solve this problem . Probably i must not understand right these 2 commands
 
chown
chmod
 
Thanks in advance

---

### Post by sikander3786 on 2010-12-22
Try the recursive chown by placing -R switch when you chmod or chown.

---

### Post by lipstick31 on 2010-12-22
Thank you my friend.I will try it

---

