---
title: "Lots of Filesystem Checks?"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Fred2a on 2010-03-26
Lucid Beta1 Fully updated Mar 26th.

Is anyone else getting disk checks on startup, I've been getting them almost every time I restart recently.

The latest one didn't even do anything, the HDD light was off, it just hung the system - had to Alt+PrtScr REISUB out of it.

I'm beginning to wonder if my drives are being unmounted cleanly on shutdown...

Any idea which logs I should look at?

---

### Post by kansasnoob on 2010-03-26
I've also thought that was the case. I brought that up here:

[http://ubuntuforums.org/showpost.php?p=9014661&postcount=456](http://ubuntuforums.org/showpost.php?p=9014661&postcount=456)

Full thread:

[http://ubuntuforums.org/showthread.php?t=1416872](http://ubuntuforums.org/showthread.php?t=1416872)

Some of the stuff about ureadahead may even be helpful:

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by Didius Falco on 2010-03-26
I'm at the opposite end of that scale - I'm not getting ANY file system checks.

It makes me wonder if the two things are related by a common bug...

---

### Post by VMC on 2010-03-26
> **Fred2a said:**
> Lucid Beta1 Fully updated Mar 26th.

Is anyone else getting disk checks on startup, I've been getting them almost every time I restart recently.

The latest one didn't even do anything, the HDD light was off, it just hung the system - had to Alt+PrtScr REISUB out of it.

I'm beginning to wonder if my drives are being unmounted cleanly on shutdown...

Any idea which logs I should look at?

If you mean the *fsck* on boot , that's normal. Its checking your file system. Later they will turn that off, once plymouth is final.

---

