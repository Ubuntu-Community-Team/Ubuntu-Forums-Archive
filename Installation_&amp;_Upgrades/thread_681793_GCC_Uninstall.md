---
title: "GCC Uninstall"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by BrainDedd on 2008-01-29
Help ... I asked Kubuntu to remove GCC 4.1 so it would use 4.2 by default and it started uninstalling just about everything and I couldn't cancel. I turned the machine off but I think it's a bit broken now...

---

### Post by PmDematagoda on 2008-01-29
You can install a majority of the lost packages by executing:-
```
sudo apt-get install kubuntu-desktop
```

---

### Post by BrainDedd on 2008-02-03
That seems to have done it thanks. :)
Is there any way to set the default gcc to 4.2?

---

### Post by PmDematagoda on 2008-02-03
Not sure if this will work, but try:-
```
sudo update-alternatives --config gcc
```

---

### Post by BrainDedd on 2008-02-08
No alternatives for gcc.

---

### Post by PmDematagoda on 2008-02-08
Could you please answer this question, why do you want to install GCC 4.2?

---

### Post by BrainDedd on 2008-02-08
I already have it installed, it just doesn't get used as default.
I want to use it because it has more recent cpu optimizations than the old gcc.

---

### Post by PmDematagoda on 2008-02-08
I believe you can create a symbolic link to the new gcc, but I am not too sure myself.

---

