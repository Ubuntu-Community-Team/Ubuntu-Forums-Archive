---
title: "unable to update ubuntu 10.10"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by cschamber on 2011-03-13
after initating the update and i enter my pass word, update stops and an error box comes up stating that it is unable to update because there is more than one synaptic manager running, i have restarted and get the same results, and to my knowledge there is nothing else running in the background. does anyone have any ides as to what i should do next.

---

### Post by Dutch70 on 2011-03-13
How are you attempting to do the update? 

Try running this code in terminal...
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cschamber on 2011-03-14
thank you, i was able to force it to update with the terminal line command you gave me. no more issues at the moment.

---

### Post by Dutch70 on 2011-03-14
Great, you shouldn't have any more problems with it then.

---

