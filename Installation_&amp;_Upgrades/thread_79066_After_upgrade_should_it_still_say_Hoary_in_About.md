---
title: "After upgrade should it still say Hoary in About?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by Louisvdw on 2005-10-19
I had Hoary installed from a CD. 
ANd I upgraded to Breezy by changing my sources.list to say Breezy in stead of Hoary and used apt-get dist-upgrade.

Now if I boot up and go to about, it still opens the browser and tells me it Hoary with all the nice thing. Should it not say Breezy? How can I tell if I really have Breezy now? 

Thanks

---

### Post by invalid on 2005-10-19
[QUOTE=Louisvdw]How can I tell if I really have Breezy now? [/QUOTE]

In a terminal, type:
```
cat /etc/*-release
```

Cheers,
Cb

---

### Post by Louisvdw on 2005-10-19
Great! It says Breezy.

Thanks

---

