---
title: "Evolution gone after update March 17"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Flag on 2009-03-17
After the latest update / upgrade evolution is gone.
Am I the only one ?:-#

---

### Post by taavikko on 2009-03-17
> **Flag said:**
> After the latest update / upgrade evolution is gone.
Am I the only one ?:-#

All of those who did partial upgrade are affected.

Just install 
```
sudo apt-get -f install ubuntu-desktop
```
And you're good to go...

---

### Post by Flag on 2009-03-17
Thanks, but tried that already.

ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 51 not upgraded.

So, maybe something else ? Thought it was worth a try after the positive posts.

---

### Post by dBuster on 2009-03-17
> **taavikko said:**
> All of those who did partial upgrade are affected.

Just install 
```
sudo apt-get -f install ubuntu-desktop
```
And you're good to go...

Does this fix the missing desktop??  I get the the gui screen and it is just my wallpaper, clearcalendar and then my windows drive...

---

### Post by taavikko on 2009-03-17
> **dBuster said:**
> Does this fix the missing desktop??  I get the the gui screen and it is just my wallpaper, clearcalendar and then my windows drive...

It should fix missing dependencies that is part of default install, not those extra packages affected.

ubuntu-desktop is meta-package that includes ubuntu's view what is gnu/linux.

---

### Post by dBuster on 2009-03-17
> **taavikko said:**
> It should fix missing dependencies that is part of default install, not those extra packages affected.

ubuntu-desktop is meta-package that includes ubuntu's view what is gnu/linux.

Thanks, actually it was the panels that are missing.  I just had a brain blank when I last posted...  There are other posts that mention this issue also.  Will keep an eye on them all...

---

### Post by philinux on 2009-03-17
Never do partial upgrades.

---

### Post by Flag on 2009-03-17
Why not, it's not my operational OS.

Anyhow, all thanks I did the upgrade a couple of hours ago and was not able to re install evolution, I was now, so it's all OK.:D

---

### Post by dBuster on 2009-03-17
Wow, after cruising the forums from work I came home after the hosed update this morning and did the following:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Followed up with:

```
sudo apt-get -f install ubuntu-desktop
```

And I am up and running now.  Latest releases including the latest kernel for Jaunty and I even have my panels back!!  

Evolution is even working for me!  Wahoo!!!

---

