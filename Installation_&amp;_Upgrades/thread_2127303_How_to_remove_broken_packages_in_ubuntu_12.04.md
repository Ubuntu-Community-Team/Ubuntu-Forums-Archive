---
title: "How to remove broken packages in ubuntu 12.04"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by pandesm on 2013-03-19
Unable to open lock! Ubuntu sofware center does not work, nor does sudo apt get install -f. It got stuck up with java 7, probably

---

### Post by Bashing-om on 2013-03-19
pandesm; Hi !

The lock condition is indicative that you have more than one instance of a software manager running.
Make sure that the Soft ware Center is not open, nor is synaptic open, aptitude nor apt-get is not running in any terminal. When all this is true, then reboot the system. To see what condition your condition is in, post the output of terminal codes:
[code}sudo apt-get update
sudo apt-get upgrade[/code][INDENT=3]
here there is help

[/INDENT]

---

