---
title: "jack help"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by johnlee on 2007-08-06
im sure this is simple, however i am having trouble, jack control doesnt start, om synth asks if jack is running, i dont know how to conigure this
thanks
john

---

### Post by johnlee on 2007-08-06
ive tried re-installing through apt-get to no avail, i dont get this

heres what i get for typing jack into terminal
john@john-laptop:~$ jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *warning* Default CD device /dev/cdrom does not exist.
 *error* Device /dev/cdrom does not exist!
still, om synth doesnt see it as running, neither does ardour


on 7.04 feisty ubuntu


on trying to run om i get
john@john-laptop:~$ om
om: error while loading shared libraries: libjack-0.100.0.so.0: cannot open shared object file: No such file or directory

---

### Post by johnlee on 2007-08-06
for some reason reinstalling with synaptic worked for me
:S now how to use these programs becomes the interesting part
later!
john

---

