---
title: "Test print uses too much ink?"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-12-21
What's happening about this? The bug is still unassigned: [bug 298935]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/298935"). I don't know if it got fixed as I'm still using Jaunty.

---

### Post by VMC on 2009-12-21
Thanks for pointing that bug out. From it I got the location of the file that does all that useless printing:
```
/usr/share/system-config-printer/testpage-a4.ps
/usr/share/system-config-printer/testpage-letter.ps
```
Now I can edit out what I want printed!

It came from  [this]("https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/298935/comments/3") reply.

---

### Post by 23meg on 2009-12-22
This is a typical "bitesize" bug that can be fixed by a non-programmer with basic design skills. Feel free to redesign the test page and attach the output to a comment on the bug; or even better, [submit a debdiff]("https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff") or a bzr branch of the package (let me know if you need help with that).

---

### Post by VMC on 2009-12-22
> **23meg said:**
> ...[submit a debdiff]("https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff") or a bzr branch of the package (let me know if you need help with that).

That link is an interesting read. The only problem is, if and when I ever have a need to fix, say spelling errors in a package, how would I ever remember that link. 

That's the first time I ever came across that wiki before. I see its need, but remembering its existence is the key here.

---

### Post by 23meg on 2009-12-22
> **VMC said:**
> That link is an interesting read. The only problem is, if and when I ever have a need to fix, say spelling errors in a package, how would I ever remember that link. 

That's the first time I ever came across that wiki before. I see its need, but remembering its existence is the key here.

It would be a good idea to bookmark the Packaging Guide, which it's part of.

---

