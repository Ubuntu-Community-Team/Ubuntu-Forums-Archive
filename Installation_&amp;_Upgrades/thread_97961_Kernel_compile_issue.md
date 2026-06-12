---
title: "Kernel compile issue"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by serzz on 2005-12-02
I'm trying to compile my own kernel to improve performance. But I've stucked at the begining.
```

serzz@ubuntu-linux:~/Desktop$ sudo tar -xvvzf linux-2.6.14.3.tar.gz /usr/src
tar: /usr/src: Not found in archive
tar: Error exit delayed from previous errors

```
What this error actually mean? How can get it worked?

---

### Post by serzz on 2005-12-02
Solved by adding --directory parameter  before /usr/src

---

