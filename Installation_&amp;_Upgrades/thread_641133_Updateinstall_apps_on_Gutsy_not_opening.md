---
title: "Update/install apps on Gutsy not opening"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Halfling Rogue on 2007-12-15
Hey all, I'm a Dapper user who just upgraded to Gutsy a few weeks ago, and I'm already running into problems with the Synaptic Package Manager/Add-Remove Programs menu/System Updates applications. Basically, they won't open. The SPM seemed to work fine when I first installed, but when I tried to use the System Updates app after that, it wouldn't work, and the Add/Remove Programs app in the Applications menu will open but won't actually upgrade anything. If I try to run SPM, it shows up in the System Monitor as gksu, and then goes to sleep.

Apt-get seems to work fine in terminal, but I'm not all that comfortable with it and it's harder to see what's available, plus I'm worried as to what might be causing this glitch. Help?

---

### Post by Partyboi2 on 2007-12-15
Have you tried to open Synaptic Package Manager via terminal? 
```
sudo synaptic
```
Is there any errors displayed in terminal after trying to run synaptic?

---

### Post by Halfling Rogue on 2007-12-15
Yeah, running it via terminal works fine. It seems to be spreading to the rest of the apps now too; I tried opening gedit using the icon on the taskbar, and it wouldn't open at all until I used terminal.

---

