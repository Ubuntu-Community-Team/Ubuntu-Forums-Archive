---
title: "Recover Unity after Gnome3 PPA install?"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by seeyouza on 2011-04-29
So I glossed over the fact that installing Gnome3 from the PPA would break Unity for some reason, and now it's broken, and I can't even check it out. Is there a way to recover it and/or remove Gnome3, or is it a case of being out of luck unless I do a full reinstall?

---

### Post by seeyouza on 2011-04-29
Sorry to bump this - but I'd really like to know if this is possible please?

---

### Post by seeyouza on 2011-04-30
Well I guess not :(

---

### Post by gwoodruff on 2011-04-30
You can purge the ppa with 

```
ppa-purge ppa:gnome3-team/gnome3
``` but it will likely break something else.

---

### Post by mafitzpatrick on 2011-04-30
I successfully installed the Gnome3 PPA and then purged it with no ill effects whatsoever that I can see. ([Instructions here]("http://ubuntuforums.org/showthread.php?p=10687613&highlight=purge#post10687613")).

People seem to have mixed results though, so maybe I was lucky :)

---

