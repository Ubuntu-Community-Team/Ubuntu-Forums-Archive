---
title: "accidently removed synaptic manager..."
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by gauthaman on 2008-03-21
hi...
        I accidentally removed the synaptic manager from synaptic manager itself...
        how to get it back? please help me out, new to ubuntu, actually new to linux itself...
        i don have a net connection also...:(

---

### Post by Barrucadu on 2008-03-21
You'll need a net connection to fix this - can't you temporarilly spare a network cable or something? If you do get it connected, open a terminal and type
```
sudo apt-get install synaptic
```

---

### Post by forestpixie on 2008-03-21
might be on the livecd, that's where it's installed from in the first place - in which case make sure that the cdrom is enabled as a source in software sources and try the line barracadu gave

---

### Post by Mustard on 2008-03-21
I would imagine it could install from the install CD if it was listed in the sources.lst.  Would that work?

---

### Post by forestpixie on 2008-03-21
that's what I was getting at - gonna be easier to do the software sources though rather than editing sources.list - he/she can learn that later :)

---

