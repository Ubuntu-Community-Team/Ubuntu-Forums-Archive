---
title: "PDF printer in 10.10"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by dmtparker on 2010-10-29
I recently upgraded to 10.10 (and am regretting it!). Now my PDF printer doesn't work. First it appeared I had two installed (I
 had not done anything) so I deleted the one that was not working, but now the other one doesn't work either. Files just pile up in the que.
This is a major issue for me as I only have internet when I make a 20 minute boat trip to town (Bocas del Toro, Panama) so I routinely PDF Print anything I want to read offline when I return home.
Any help is appreciated.

---

### Post by lechien73 on 2010-10-29
Have you tried removing and re-installing the cups-pdf package?

```
sudo apt-get install --reinstall cups-pdf
```

Also, does the folder named PDF exist under your user folder?

---

### Post by dmtparker on 2010-10-29
That worked. Well, actually it worked after I deleted the remaining pdf printer and then ran the script. Thanks for the help!
It just seems that these sort of thing should be worked out BEFORE the release of a major upgrade. Not having to use the command line is one reason a lot of people choose Ubuntu.

---

