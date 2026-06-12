---
title: "compilation process freezes"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by bernat_f on 2007-01-29
Hi,

I'm using ubuntu edgy and recently while I was trying to compile the package of 'gutenprint 5' my whole system freezes, I have restarted it and prove several times but it always ends at the same point.

I don't know if its a problem of the package or of the gcc compiler, what should I do?

Can anyone help me, please?

---

### Post by taurus on 2007-01-29
What's the output before it freezes?

---

### Post by bernat_f on 2007-01-29
the last line break starts like that =

gcc -shared ... (5 lines of code)

I'm going to do a photo

---

### Post by taurus on 2007-01-29
Since there is not much to go on here, just want to see if you have installed build-essential package on your machine!

```
sudo aptitude update
sudo aptitude install build-essential
```

---

