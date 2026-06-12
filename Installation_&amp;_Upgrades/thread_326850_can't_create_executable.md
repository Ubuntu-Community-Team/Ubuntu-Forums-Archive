---
title: "can't create executable"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by dujlinvik on 2006-12-28
does anyone knows how can i configure the 'c-compiler' in Ubuntu?
i'm trying to install Apache but after the coomands :
```

./configure --prefix=/usr/local/apache2

```
in terminal i get this message :
```

checking for C compiler default output file name... configure: error: C compiler cannot create executables
```
everything else during the ".config" process seem to be OK.
i tried 'sudo aptitude update', but did not help....
](*,)

---

### Post by taurus on 2006-12-28
You probably need to build-essential package...

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by dujlinvik on 2006-12-28
that helped, thanks :D

---

