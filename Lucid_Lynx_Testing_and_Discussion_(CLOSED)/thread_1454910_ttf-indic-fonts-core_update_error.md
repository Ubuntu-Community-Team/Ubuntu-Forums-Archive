---
title: "ttf-indic-fonts-core update error"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Muflon on 2010-04-15
Is anyone getting the following error message when updating ttf-indic-fonts-core

```
E: /var/cache/apt/archives/ttf-indic-fonts-core_1%
3a0.5.8ubuntu1_all.deb: subprocess new pre-installation script returned 
error exit status 127
```

---

### Post by tokyobadger on 2010-04-15
exact same error here - I'm sure it'll be fixed in a while

---

### Post by phill on 2010-04-15
Same here, the problem seems to be with this line:
"/var/lib/dpkg/tmp.ci/preinst: 19: rm_conffile: not found"

I've just held the file and continued with the rest of the upgrade:

```
echo "ttf-indic-fonts-core hold" | sudo dpkg --set-selections -

```

---

### Post by JCoster on 2010-04-15
+1.

```
sudo dpkg --configure -a
```
..ran the rest of the upgrade for me.

---

### Post by aviramof on 2010-04-15
the new command i made today bypase this update and continue with the rest automaticly:

```
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade
```

---

### Post by jaco223 on 2010-04-15
I'm getting the same error message here.

---

### Post by vaibhav on 2010-04-15
Talking of Indic fonts, after recent updates I've found Devanagari rendering to be broken in Chromium. See attached picture. Things seem to be fine in Firefox. Anyone else here having this issue?

---

### Post by bornagainpenguin on 2010-04-15
> **aviramof said:**
> the new command i made today bypase this update and continue with the rest automaticly:

```
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade
```

This fixed the issue for me, so thanks!

--bornagainpenguin

---

