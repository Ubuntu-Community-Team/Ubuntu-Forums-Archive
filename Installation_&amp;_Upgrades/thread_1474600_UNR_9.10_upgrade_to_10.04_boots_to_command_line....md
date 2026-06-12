---
title: "UNR 9.10 upgrade to 10.04 boots to command line...help"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by dmgrays on 2010-05-06
I clicked on the upgrade to LTS 10.04 option on my Asus 901 EEE PC and after completion it will only boot straight to command line...any help or ideas on what went wrong...I would like to get back to the UNR Gui. Thanks in advance for the help!

---

### Post by tom4everitt on 2010-05-06
Try logging in to the shell (if you're not automaticaly logged in), by typing your username. Then run:

sudo startx

or 

sudo start gdm 

and see if you get any error messages or something (these commands should should normally start your graphical desktop).

---

### Post by roosh on 2010-06-09
I have the same problem, except Ubuntu boots normally some of the time.

"startx" does give me back my regular desktop.

Any ideas on what the problem is?

---

