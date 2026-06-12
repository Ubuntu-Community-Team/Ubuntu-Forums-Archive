---
title: "How to downgrade a package?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by 123dfdfg43 on 2006-06-06
Hi,

I have some problems with the new mplayer, and I'd like to downgrade it, with sdl packages too...
How can I downgrade these packages to 5.05?

Andrea

---

### Post by rcarring on 2006-06-06
Do a complete removal in your distributions package manager of the programs you want to downgrade, then go get the debs for the earlier version and double click to install them, you can  figure out the order of installation by the dependency errors thrown up.

I managed to downgrade my copy of Open Office by hacking my sources.list, but I don't recommned doing thsi unless you have a) backed it up and b) know what you are doing.

---

### Post by Lux Perpetua on 2006-06-07
Could you also accomplish this in Synaptic by selecting "Force version" from the "Package" menu?

---

### Post by rcarring on 2006-06-07
I cannot answer that, I'll have to defer to the senior users on board. Sorry.

---

### Post by Ushi on 2008-05-17
Package -> Force Version in Synaptic is definitely the way to do this.

This fixed my entire apt system after I upgraded a little hastily with dpkg.

---

