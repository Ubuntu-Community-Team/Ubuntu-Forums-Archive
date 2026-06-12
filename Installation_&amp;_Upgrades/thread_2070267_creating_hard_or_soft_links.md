---
title: "creating hard or soft links"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-10-12
I have installed python 3.3 and am trying to create a link from /usr/bin  to where I have installed the new version. In the /usr/bin folder I  find

python   -> python2.7
python2 -> python2.7

Which  are links to enable python to be run. Now I want to leave python2.7  where it is and create another link called python3 and point it to the  location of the executable where my new install is. I have tried a few  things like

ln -i python3 /home/berny/python/Python-3.3.0/debug/python

this did not work. Lost my python file so had to re-install, also tried 

ln -s python3 /home/berny/python/Python-3.3.0/debug/python

but this did'nt work either

please advise. Thanks in advance

---

### Post by oldfred on 2012-10-12
I have the 3.2 version installed from the repositories and this is what I have. Did you change to make python executeable?

Whatever you do, do not modify any settings on python or python2.7 links. The Ubuntu system relies on those links and if you break them, you may have to reinstall.

---

### Post by spjackson on 2012-10-12
You have your arguments to ln the wrong way round.
```

sudo ln -s /home/berny/python/Python-3.3.0/debug/python /usr/bin/python3

```
However, if this is just for you to run, I would suggest putting it in your own bin directory instead, rather than /usr/bin.
```

ln -s /home/berny/python/Python-3.3.0/debug/python ~/bin/python3

```

---

### Post by bencouve on 2012-10-12
Thanks for your comments guys, and SPJACSON, I had suspected that but decided to ask the experts before proceeding. Will try now.

---

### Post by bencouve on 2012-10-12
That has worked. Thanks again for your help. I will mark it as solved.

---

