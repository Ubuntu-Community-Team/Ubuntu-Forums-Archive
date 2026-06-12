---
title: "Updates won't install"
date: 2017-07-09
forum: Installation &amp; Upgrades
---

### Post by Deejay35 on 2017-07-09
Hi, running Ubuntu 16.10 Gnome, and now updates won't install for this reason.

dpkg: error processing package bsdutils (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 bsdutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

Haven't been able to rectify, could someone give me the method please, thanks.

---

### Post by Bashing-om on 2017-07-09
Deejay35;  Hey, hey

What results when taking the package manager's advise:
```

sudo apt update
sudo apt install --reinstall bsdutils

```

[INDENT][INDENT]could be a small thing
[/INDENT][/INDENT]

---

### Post by Deejay35 on 2017-07-09
Thanks friend, all OK now.

---

### Post by Bashing-om on 2017-07-09
Deejay35; Good deal :)

Glad it was an easy fix .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]weren't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2017-07-10
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

