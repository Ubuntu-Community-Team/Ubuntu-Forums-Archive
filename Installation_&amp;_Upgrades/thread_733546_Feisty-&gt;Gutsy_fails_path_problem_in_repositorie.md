---
title: "Feisty-&gt;Gutsy fails: path problem in repositories?"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by markiangooley on 2008-03-23
I get an error message when trying to upgrade from 7.04 Feisty to 7.10 Gutsy:

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-amd64/Packages.gz) 404 Not Found

No such directory as /apt exists there.  /ubuntu/dists does.

So, how do I get the thing to look there?  Similar message with sudo apt-get update.

Mark., I suppose I could install from a CD
gooley at gator dot net

---

### Post by marpstar on 2008-03-24
open a terminal and type:

```
sudo gedit /etc/apt/sources.list
```

you need to comment out any lines that are outside of the official ubuntu repos.  After this, everything should work great.  I think I had this same error because of the automatix repos, so if you've got them, make sure to comment them out.

---

### Post by markiangooley on 2008-03-24
1.  Thanks.  That solved the problem.
2. AAAAARGH!  Tripped up by the Automatix problem, and I didn't even recognize it!
3. Now there's another problem I'm going to try to puzzle out before making another post...

Mark., sigh
gooley at gator dot net

---

