---
title: "Rhythmbox does not save added internet radio stations"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-01-15
If I add Internet radio station in Rhythmbox it is not saved on exit. Previous versions did that. I could not find a file where this information is stored, to try to manually add a station. OK, problem with notification and icon is solved, but, this is more annoying than the problem solved.

---

### Post by Gourgi on 2010-01-15
i cannot reproduce this bug but feel free to report it to launchpad using ```
ubuntu-bug rhythmbox
```

---

### Post by zika on 2010-01-15
> **Gourgi said:**
> i cannot reproduce this bug but feel free to report it to launchpad using ```
ubuntu-bug rhythmbox
```I did.

---

### Post by ranch hand on 2010-01-15
I have rhythmbox with 2 added radio stations that I added yesterday.   I have rebooted at least 5 times since then and they are still with me.

---

### Post by zika on 2010-01-15
> **ranch hand said:**
> I have rhythmbox with 2 added radio stations that I added yesterday.   I have rebooted at least 5 times since then and they are still with me.It is not reboot that messes with it. Just if I close RB the new station is gone. There was upgrade of RB, recently, that solved status icon problem. It is not a big deal, I'm more curious. Do You know where RB stores that info, so I could edit that myself...?

---

### Post by mc4man on 2010-01-15
> where RB stores that info

may not do you any good but..
~/.local/share/rhythmbox/rhythmdb.xml

---

### Post by ranch hand on 2010-01-15
/home/<user name>/.local/share/rhythmbox/rhythmdb.xml  way at the bottom of the list.

---

### Post by zika on 2010-01-15
Done! I've cleaned a hundreds of lines, added stations I want, and, now, I'm listening... Something is, still wrong with saving mechanisam, but, I do not complain. Thank You guys.

---

### Post by zika on 2010-01-20
It seems that upgrade of some other package solved the problem with RB... We'll see...

---

