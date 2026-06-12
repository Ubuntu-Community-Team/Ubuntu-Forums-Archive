---
title: "After dots blank screen and hangs"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by pfcg on 2010-07-02
Hi 
 
First time with ubuntu envronment. I downloaded image and try to load on a laptop  with existing ubuntu 9x version. When I am booting from CD, it goes up to ...... dots and blank screen appears and nothing happens for hours. 
 
I don't know from where to start checking and what should I do.
 
Thanks in anticipation
 
pfcg

---

### Post by Rubi1200 on 2010-07-02
Ubuntu is already installed; 9.10?

What type of graphics card do you have?

---

### Post by pfcg on 2010-07-02
> **Rubi1200 said:**
> Ubuntu is already installed; 9.10?
 
What type of graphics card do you have?
 
 
Thks. I don't know. Can I check on OS level ? 
 
pfcg

---

### Post by pfcg on 2010-07-02
Sorry, I did not answer yr first question. Yes ubuntu was already instaleed and I was trying to download the new version and that is where it stopped working and getting blank screen.
 
I downloaded the new image and thought of loading by CD boot. 
 
thks
 
pfcg

---

### Post by Rubi1200 on 2010-07-02
You can still get into the existing install right?

If yes, then go to the terminal and post the output of this:

```
lspci -nn | grep VGA
```

---

