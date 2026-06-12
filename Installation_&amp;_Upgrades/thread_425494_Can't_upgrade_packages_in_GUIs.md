---
title: "Can't upgrade packages in GUIs"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by steve0921 on 2007-04-27
In both the update manager and synaptic GUIs I can't seem to upgrade packages, though the symptoms are a bit different in each. I recently upgraded to feisty and I believe this has been happening since the upgrade.

In update manager I can press the "Check" button and it will find upgrades for me. When I press the "Install" button though, all it does is refresh the cache (like it does after updating the list, and used to do after an upgrade) and then does nothing. In synaptic, pressing the button to mark upgrades simply does nothing. However, synaptic still works to install and remove packages. 

Also, I just did an apt-get upgrade and it upgraded the packages that update manager told me I could upgrade. I have no idea how this could work, while somehow the graphical upgraders do not. Searching has only yielded a bug with the same update manager problem, but only for those using italian (I'm not).

Any ideas?

---

### Post by bapoumba on 2007-04-27
Try to launch synaptic from the terminal (>Accessories > Terminal) and see if you get any error.
```
gksudo /usr/sbin/synaptic
```

---

### Post by steve0921 on 2007-04-27
That's a good idea. Unfortunately I don't have any more upgrades, so I'll have to wait and try it in a day or so.

---

### Post by steve0921 on 2007-04-28
Synaptic does not give me any useful information when run from the terminal.

---

### Post by steve0921 on 2007-04-29
An interesting new development:
I recently downgraded some mesa packages to the edgy versions (the feisty ones made NWN very ugly) and synaptic CAN mark those upgrades. It still does nothing with the others available from feisty.

Does anybody know why this would be happening?

---

