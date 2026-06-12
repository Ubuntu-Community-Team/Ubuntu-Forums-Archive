---
title: "what packages should i get,to start c codes"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by yhcheong on 2005-09-03
im a newbie in linux . i had installed ubuntu on my pc. here some of my questions
1. LINUX file system had evolved from Minix to EXT2 and then to the current Virtual File System.why there was a change from Minix to EXT2 and then to the current Virtual File System.

2. What packages should get and what are the setting needed to start C codes executions..


can anyone answer my quest ions? will appreaciate...

---

### Post by Leif on 2005-09-03
1. I think you're confusing VFS with actual filesystems, such as ext3 and reiserfs. The switch to these has been mainly due to the increased protection journalling systems allow.

2. If you mean how can I compile things, apt-get install build-essential

---

