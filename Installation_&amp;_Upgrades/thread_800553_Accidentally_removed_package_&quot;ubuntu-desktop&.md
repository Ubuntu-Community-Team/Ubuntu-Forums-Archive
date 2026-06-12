---
title: "Accidentally removed package &quot;ubuntu-desktop&quot;"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by jdholifield on 2008-05-19
Hi, one of my computers has Hardy and we've been having a problem getting the Sound to work.  Well I was trying something I read somewhere and I tried to install the package "esound", well when I installed it, it also removed the package "ubuntu-desktop" and now I cannot figure out how to get it back ?

Can you give me any advice ?  My Ubuntu lets me log in, but we can't get a terminal or run the Add-Remove programs thing.

Am I just screwed, or can this be fixed ?

---

### Post by iaculallad on 2008-05-19
Try this on your terminal:

sudo apt-get install ubuntu-desktop

---

### Post by Monicker on 2008-05-19
What do you see when the system boots up?

Try this to get to a terminal prompt:

```
CTRL + ALT + F3
```

---

### Post by renovate on 2008-05-19
you don't need to find the "terminal" application you would use with the desktop, you can just enter the code after you log in.

---

### Post by jdholifield on 2008-05-20
> **iaculallad said:**
> Try this on your terminal:

sudo apt-get install ubuntu-desktop

I would gladly do that, but as I was saying I don't have a terminal now and can't seem to figure out how to get one.

---

### Post by iaculallad on 2008-05-20
Try pressing Alt+F1 if it pops the Application Menu. If it pops, navigate through Accessories->Terminal and execute 
sudo apt-get install ubuntu-desktop

---

### Post by zvacet on 2008-05-20
If you can not find way to the terminal boot in recovery mode and type

```
aptitude install ubuntu-desktop
```

---

