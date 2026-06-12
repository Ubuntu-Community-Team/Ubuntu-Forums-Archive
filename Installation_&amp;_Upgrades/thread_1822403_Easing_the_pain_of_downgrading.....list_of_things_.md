---
title: "Easing the pain of downgrading.....list of things I installed?"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by thegoonden on 2011-08-10
I have to get rid of Natty, it's broken video system (no vsync on desktop or more importantly mplayer) and no sign that anyone gives a crap, are giving me headaches and ulcers ;)


Now, I already have a way to make a list of every installed package so that when I install 10.10 again....but it's messy as many of the things listed in it are dependencies that were never installed manually.....the process takes hours and from the terminal output, it appears to go over and over the same packages.

Is there a file somewhere that contains a list of just the software that I requested via synaptic/software centre/apt-get?

Then I can use that to bring my new 10.10 back up to standard.


Thanks in advance.

---

### Post by matt_symes on 2011-08-10
Hi

For apt-get look in

```
cat /var/log/apt/history.log
```

and the other history logs.

For aptitude look at 

```
cat /var/log/aptitude
```

For every package installed

```
dpkg -l
```

That is a small L above

Kind regards

---

### Post by thegoonden on 2011-08-10
Thank you kindly :D

---

### Post by drs305 on 2011-08-10
With Synaptic, you can create the lists via the Synaptic menu:
File, Save Markings, *make sure you tick the 'Save full state'*, and then choose a folder and name. The file is a simple text file that you can review (and even edit) if you wish.

To restore, File, Read Markings.

---

