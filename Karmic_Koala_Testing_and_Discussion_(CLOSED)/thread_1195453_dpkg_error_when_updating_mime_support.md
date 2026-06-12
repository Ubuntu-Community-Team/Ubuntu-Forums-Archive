---
title: "dpkg error when updating: mime support"
date: 2009-06-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2009-06-23
Not a biggie, but I got this earlier on my main karmic install:

```
aptitude update/safe-upgrade

blah blah...

Errors were encountered while processing:
 mime-support
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mime-support (3.46-1) ...
update-alternatives: unable to make /usr/share/man/it/man1/view.1.gz.dpkg-tmp a symlink to /etc/alternatives/view.it.1.gz: No such file or directory
dpkg: error processing mime-support (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mime-support
```

---

### Post by jfernyhough on 2009-06-25
I'm getting the same thing. It's a little annoying as it's now affecting a LyX update.

I worked around this by manually creating some extra /usr/share/man/ directories (pl.UTF-8, fr.UTF-8, it.UTF-8 etc) but that really shouldn't be necessary.

---

### Post by paul_in_london on 2009-06-29
To eliminate this error, I had to create the following directories:

/usr/share/man/it/man1
/usr/share/man/pl/man1
/usr/share/man/it.ISO8859-1/man1/
/usr/share/man/fr.ISO8859-1/man1/
/usr/share/man/it.UTF-8/man1/
/usr/share/man/pl.ISO8859-2/man1/
/usr/share/man/pl.UTF-8/man1/

---

