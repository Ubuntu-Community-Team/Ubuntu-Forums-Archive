---
title: "Bluefish not found"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by prezbedard on 2007-08-06
I'm trying to install bluefish using aptitude however I'm getting the message back that the package can't be found.

Any idea where to start with this?

Thanks,

---

### Post by Seisen on 2007-08-06
You probably can't find it because its in the universe repositories. To use the universe repositories go to System>Administration>Software Sources and check the box that says Community Maintained Open Source Software. Once you have done that you need to a ```
sudo aptitude update
``` and then it should find it.

---

### Post by prezbedard on 2007-08-06
I went and tried that yet I'm still getting bluefish package not found. :confused:

---

### Post by merlinus on 2007-08-06
Try finding and installing via Synaptic.

System/Administration/Synaptic

-merlin

---

### Post by Seisen on 2007-08-06
Did you do the ```
sudo aptitude update
``` before you searched for bluefish again?

---

### Post by prezbedard on 2007-08-06
Yes and I already tried using synaptic.

---

### Post by Seisen on 2007-08-06
I don't understand why its coming up as not being found. Does it say anything about another package having bluefish in the name?

---

### Post by prezbedard on 2007-08-07
I did a search for blue* and it founds  5 or 6 packages but no bluefish. A search for bluefish turned up nothing.

---

### Post by merlinus on 2007-08-07
Even on bluefish website it says:

debian and ubuntu users, simply run:

sudo apt-get install bluefish

so clearly the problem lies in your repos.

Take a look at /etc/apt/sources.list

-merlin

---

