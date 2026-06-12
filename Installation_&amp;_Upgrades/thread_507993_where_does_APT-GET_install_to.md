---
title: "where does APT-GET install to?"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by czJake on 2007-07-23
I need to run the ./config file for squid after installing it with apt-get so I can change the configuration options.
However, :confused: I don't know where it is located.

---

### Post by ddrichardson on 2007-07-23
I'm sure you can do this from apt-get but synaptic will tell you if you select the package and click properties/installed files.

---

### Post by czJake on 2007-07-23
I'm actually running Ubuntu server 7.04 with no GUI.

---

### Post by ddrichardson on 2007-07-23
sudo dpkg -L packagename

---

### Post by czJake on 2007-07-24
Thanks, I'll try that this evening.

---

### Post by czJake on 2007-07-24
I ran that command, as far as I can tell ./configure for squid is nowhere to be found. :(
Any ideas?

---

### Post by ddrichardson on 2007-07-24
Sorry I'm not familiar with squid, but if its not listed by dpkg then it wasn't installed - is it created by something another executable in the package?

---

