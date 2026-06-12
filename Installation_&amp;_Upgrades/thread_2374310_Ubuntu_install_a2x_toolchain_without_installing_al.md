---
title: "Ubuntu: install a2x toolchain without installing all asciidoc"
date: 2017-10-14
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2017-10-14
Hi,
I wonder to know if it is possible to install [a2x toolchain]("http://manpages.ubuntu.com/manpages/precise/man1/a2x.1.html") without installing all asciidoc (about 800 MB).
Thank you

---

### Post by erotavlas on 2017-10-14
After a very long search, I found the solution:
```
apt-get --no-install-recommends install asciidoc -y
```

---

