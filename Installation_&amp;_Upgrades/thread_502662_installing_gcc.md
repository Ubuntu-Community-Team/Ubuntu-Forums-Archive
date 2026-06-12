---
title: "installing gcc"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by matches on 2007-07-16
Hello all,

I am trying to get Beryl installed but it appears I need a compiler. I tried installing gcc but it is pretty complicated. Then in my research i noticed that gcc might come with Ubuntu. Maybe someone knows the easiest way to get gcc installed.

Thanks for

---

### Post by Pumalite on 2007-07-16
Synaptic>Search>gcc>Mark to install>Apply.

---

### Post by odiseo77 on 2007-07-16
Have you tried the following?:

```
sudo apt-get install gcc
```

And as for beryl, all you have to do is to [add extra repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") and execute:

```
sudo apt-get update
sudo apt-get install beryl emerald-themes beryl-manager
```

NOTE: You probably want to read [this]("http://easylinux.info/wiki/Ubuntu:Feisty#Eye_Candy") first.

---

### Post by matches on 2007-07-16
OK cool. That worked nicely, thanks. Honestly, I looked for a long time and found nothing like that. Of course I could do another search and find that same solution a thousand times now ;) I will research Beryl and I check back in with my results. Thanks for the info!

---

