---
title: "i need help to install aMSN"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by boboyo on 2008-01-06
i am using ubuntu gust 7.10

i have problems installing amsn.
when i go to add/remove programs and i click on amsn, this message appears :
Cannot install 'amsn'

This application conflicts with other installed software. To install 'amsn' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict. 
(same  thing happens when i try to install java runtime)

when i go to synaptics, and i try installing amsn, this message appears:
amsn:
 Depends: tk8.4  but it is not installable

when i look for tk8.4 in synaptics, its not there.

when i try installing amsn trough terminal, this is what happens

sudo apt-get install amsn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  amsn: Depends: tk8.4 but it is not installable
E: Broken packages


so plz someone help me!!!

---

### Post by rodo-&gt;dave on 2008-01-06
I am just guessing but it looks like the tk8.4 was just released a couple of days ago and may not be populated everywhere it needs to be.
Here is a link to tk8.4' webpage:
[http://www.tcl.tk/software/tcltk/8.4.html](http://www.tcl.tk/software/tcltk/8.4.html)

good luck.

---

### Post by boboyo on 2008-01-06
wich ones do i download and what do i do with them after?

---

### Post by boboyo on 2008-01-06
i fixed the prob

a guy on another post told me to change the repositories and i found tk8.4

---

