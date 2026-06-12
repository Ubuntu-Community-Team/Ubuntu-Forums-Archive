---
title: "Change path"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by davholla on 2007-02-24
I want to add some directories to my path permantely.  Should this be done in .profile ?

---

### Post by taurus on 2007-02-24
Should be in ~/.bashrc

```
PATH=$PATH:new_path:even_newer_path
export PATH
```

---

### Post by highneko on 2007-02-24
```
[COLOR="DimGray"]# Will work after a restart:[/COLOR]
printf '\nif [ -d ~/bin ]; then\n    PATH=~/bin:"${PATH}"\nfi\n' >> .bashrc
[COLOR="DimGray"]# To get it working now you could:[/COLOR]
PATH=~/bin:"${PATH}

```

---

