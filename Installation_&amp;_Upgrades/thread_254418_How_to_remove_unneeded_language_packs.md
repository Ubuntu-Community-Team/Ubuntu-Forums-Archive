---
title: "How to remove unneeded language packs?"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by rscow on 2006-09-09
,

---

### Post by SkyNet2029 on 2006-09-10
You could use 'localepurge' to remove/set the languages your system uses.
Like this:

```
$sudo apt-get install localepurge
```

once installed, you should run this:

```
dpkg --configure localepurge
```

to ensure your language settings are set correctly.

to run it manually once installed (although you shouldn't really need to as it should run after every dpkg run automagically) you can just do:

```
$sudo localepurge
```

---

