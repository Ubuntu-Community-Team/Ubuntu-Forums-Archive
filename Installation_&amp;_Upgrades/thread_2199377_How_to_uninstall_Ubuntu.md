---
title: "How to uninstall Ubuntu"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by martomanoloff on 2014-01-13
Hi, there. Quick question, whose answer I didn't find on the net.
I have installed Ubuntu through Wubi on the Partition D and later on I reinstalled the Windows formatting the whole C:. Now I can't seem to be able to uninstall Ubuntu, since Wubi doesn't recognise it. Also the same thing with the installation CD. Anyone knows a way around without formatting the D: since it has to many important things. Also a way to return ubuntu to the basics, I mean the same state as a fresh installed copy, would work.
Thanks in advance,
Regards, Maritn.

---

### Post by ppjdee on 2014-01-13
So your wanting to "restore" ubuntu to a fresh state on D drive, with out formatting and losing the data?

---

### Post by martomanoloff on 2014-01-13
The data on the D is needed, but the data that is in the Ubuntu is not important.

---

### Post by hakuna_matata on 2014-01-13
An uninstaller should be in ubuntu folder:
[B]
D:\ubuntu\uninstall-wubi.exe[/B]

Note: this deletes all data within ubuntu folder.

---

### Post by martomanoloff on 2014-01-14
Yes I also thought of that, tried it, doesn't seem to do anything. I guess the registry it is supposed to use is gone with the whole C. 
Other Suggestions?

---

### Post by mastablasta on 2014-01-14
but uninstaller might not work if the system drive was reformatted and system reinstalled.

is wubi still in the boot manager? if so you could delete it from windows boot manager and then just delete the [B]D:\ubuntu forlder.

[/B]also wubi is not supported anymore.

you can also just replace the windows boot manager with a fresh one from the windows install disk. it's just a command or two in recovery console (see microsoft help articles dependign on which windows you use).

---

### Post by hakuna_matata on 2014-01-14
> **martomanoloff said:**
> Yes I also thought of that, tried it, doesn't seem to do anything.
Then try this from mastablasta:
> just delete the **D:\ubuntu forlder.**

---

