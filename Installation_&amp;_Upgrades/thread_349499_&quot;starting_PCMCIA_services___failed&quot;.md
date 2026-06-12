---
title: "&quot;starting PCMCIA services   failed&quot;"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by xingerguan on 2007-01-30
I met "starting PCMCIA services   failed" when upgrading breezy to dapper. 
I found this question unanswered yet in the forum though someone did have the same situation before. Can experts help?

---

### Post by hal10000 on 2007-01-30
A silly question: Do you have any PCMCIA devices?
If not, then the error does'nt matter and you can remove the package pcmciautils to get rid of this message.

---

### Post by xingerguan on 2007-01-30
I have to continue asking silly questions :) 
Why did this message appear only after I upgraded the system? I didn't see it when using breezy. 
Thanks!

---

### Post by hal10000 on 2007-01-30
Maybe during the upgrade the pcmcia package was installed,  e.g. to fit other dependencies. This sometimes happens when metapackages are installed or if a dependency of a given package has changed in the new version.

If you have any pcmcia devices you should of course not remove the package. Then we must try to walk through the problem.

---

