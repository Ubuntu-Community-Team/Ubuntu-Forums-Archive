---
title: "Issue with update-manager"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by JasonGriffee on 2011-05-18
I received this:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/psyke83-ppa-natty.list'

Update Manager and Packet Manager do not work.

EDIT: Ubuntu Software Center is also affected.

---

### Post by coffeecat on 2011-05-18
You have a malformed line in the *.list file for the psyke83 ppa repository. This will affect the three apps you mention (I presume you mean Synaptic Package Manager for Packet Manager). There's an easy fix and slightly more complicated fix.

The easy fix. Open Synaptic > Settings menu > Repositories > Other Software tab. Untick any lines for the psyke83 ppa repository. This will cause the error to go away but you will have disabled the ppa repository.

If you want to use that repository, open a terminal, and:

```
cat /etc/apt/sources.list.d/psyke83-ppa-natty.list > Desktop/psyke83-ppa-natty.list
```Post the contents of the file psyke83-ppa-natty.list that appears on your desktop and we can take it from there. Alternatively, if you are comfortable editing system files, open /etc/apt/sources.list.d/psyke83-ppa-natty.list in gedit with administrative privileges and see what is wrong with line 3.

---

