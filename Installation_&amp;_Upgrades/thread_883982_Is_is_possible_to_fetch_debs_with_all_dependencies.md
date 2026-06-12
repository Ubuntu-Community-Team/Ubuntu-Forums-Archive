---
title: "Is is possible to fetch debs with all dependencies without installing them?"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by PryGuy on 2008-08-08
Hello all! Well, the subj... Thanks in advance!

---

### Post by Vorian Grey on 2008-08-08
Sure. I think there may be a setting in Synaptic's settings that allow you to download only (not sure about that, I really don't play with Synaptic much, it would be under file). However, I know you can do that with apt-get from the command line. Put -d on the end, like this...

```
apt-get install gimp -d
```

That only downloads the file and it's dependencies.

---

### Post by PryGuy on 2008-08-08
The man! [-o<

---

