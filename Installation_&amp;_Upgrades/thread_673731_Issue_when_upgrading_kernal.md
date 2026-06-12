---
title: "Issue when upgrading kernal"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by gspat on 2008-01-20
I have a small issue whenever I upgrade my kernal...

after each update, I have to manually edit the grub list to reflect the actual locations for the kernal...

each time it changes the location to hd1,6 instead of what it should be - hd0,6 so that when grub loads it just shows grub error - partition not found

is there a setting somewhere that I can't find to stop it from doing this?

this has happened every time i've updated the kernal from feisty (when I started using linux) to now (testing hardy)

---

### Post by logos34 on 2008-01-21
what does **groot** (line 74) show?

---

### Post by gspat on 2008-01-21
it shows what it changes it to...

lol.. 

ok... do I change it from:

# groot=(hd1,6)

to 

# groot=(hd0,6)

or 

groot=(hd0,6) <-- take out the comment ??

---

### Post by logos34 on 2008-01-22
> **gspat said:**
> do I change it from:

# groot=(hd1,6)

to 

# groot=(hd0,6)

Yes.  

(grub reads those lines despite the single '#' hash--confusing, I know.)

---

