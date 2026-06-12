---
title: "Why does the update manager wants to remove metacity?"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-09
i have downloaded updates got a message about partial update didn't go this way instead i checked in synaptic and saw that it suppose to remove metacity now i don't really use metacity i use compiz so what should i do now?

thanks in advance.

---

### Post by theanswriz42 on 2010-04-09
[http://ubuntuforums.org/showthread.php?t=1450282](http://ubuntuforums.org/showthread.php?t=1450282)

---

### Post by aviramof on 2010-04-09
i saw this thread but it's not exceclly  the same it ask you to remove only metacity and updgrade metacity common if you do that then compiz and etc are still fine only if you want to install the new metacity version then it asks you to remove compiz, compiz gnome and fusion-icon.

---

### Post by psyke83 on 2010-04-09
> **aviramof said:**
> i saw this thread but it's not exceclly  the same it ask you to remove only metacity and updgrade metacity common if you do that then compiz and etc are still fine only if you want to install the new metacity version then it asks you to remove compiz, compiz gnome and fusion-icon.

It's most likely a packaging error in metacity which is causing it to remove the compiz packages by accident. The "compiz-gnome" package is listed in metacity's "reverse provides", and is probably shouldn't be there. It will most likely be fixed in the next update to the metacity packages.

In the meantime, the Partial Upgrade thread (and advice contained within) is *exactly* what you need to read and follow - i.e., be patient - and don't force the partial upgrade.

---

### Post by jppr on 2010-04-09
> **aviramof said:**
> i have downloaded updates got a message about partial update didn't go this way instead i checked in synaptic and saw that it suppose to remove metacity now i don't really use metacity i use compiz so what should i do now?

thanks in advance.

sometimes i wonder people who use the development version without the basic system are controlled

---

### Post by jppr on 2010-04-09
> **aviramof said:**
> i have downloaded updates got a message about partial update didn't go this way instead i checked in synaptic and saw that it suppose to remove metacity now i don't really use metacity i use compiz so what should i do now?

thanks in advance.

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by aviramof on 2010-04-09
> **jppr said:**
> sometimes i wonder people who use the development version without the basic system are controlled

what do you mean without the basic system are controlled i have plenty of knowledge about ubuntu and beside it's not my fault that versions 9.04 and 9.10 didn't want to work so well with my isp i was ubable to connect to my isp via pppoeconf and my isp instructed me to do.

and as i said i knew well enaf not to use partial updates and beside i really don't see a reason to keep metacity at all since i only use compiz so unless 
someone here think otherwise i don't see any reason to even keep metacity-common and libmetacity-private0 pacages.

---

