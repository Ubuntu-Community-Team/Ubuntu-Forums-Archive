---
title: "Ubuntu DD 6.06 and gcc 4.0 base"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by dalia on 2006-07-07
I've recently installed the 6.06 by replacing the last ubuntu 5.10,in which I had installed gcc3.3-base(the c compiler)
I saw in synaptic of the 6.06 the 4.0 version was installed already but when I type "man gcc" or "gcc -g file.c" on terminal says command not found...Do I need any components to make it work?

---

### Post by Jagot on 2006-07-07
Try:

```
sudo aptitude update && sudo aptitude install build-essential
```

---

### Post by dalia on 2006-07-10
Do I need Internet connection to do that? cause I dont have in ubuntu...can I download anything instead?

---

### Post by dalia on 2006-07-11
Synaptic says I have 2 destroyed packages and I cannot fix them so I can fully remove gcc base...what else can I do to make the compiler work?Can I download sth and install it from the beginning?

---

