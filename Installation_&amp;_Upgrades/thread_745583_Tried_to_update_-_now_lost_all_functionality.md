---
title: "Tried to update - now lost all functionality"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by DrFixxer on 2008-04-04
Hi Guys! 

I recently switched my desktop from Ubuntu to Xubuntu, and earlier I got around to applying some updates that required downloading and installing. 

I let the update manager do its thing then a few minutes in, it dissapeared and I assumed it had finished. 

I tried to reboot my machine but it said I didn't have sufficient rights to do so. 

Then I switched it off by holding the button down, loaded it up, and now a significant amount of my programs won't work anymore.The terminal wont load up, The network adapter isn't being recognised, firefox wont load up, the update manager wont work and on boot it says: 

Failed to Initialize HAL

The other thing is, it is no longer booting into the Xubuntu desktop, but the Ubuntu one - which I assumed had previously been overwritten by the Xubuntu files. 

Is there any way to recover my installation?  PLEASE! I'm desperate :) 
I do have an original 7.10 ubuntu live disk, and I can also boot into the recovery mode screen (Non GUI)
As you can tell I'm a bit of a noob at all this. 

Many thanks in advance, 

Alex

---

### Post by DrFixxer on 2008-04-04
Its fixed! 

Ok, I'll be honest, I'm not clever enough to work out HOW I fixed it, but I know it IS fixed and its working like a charm once more. 

I went through several forums and ran several commands in desperation, however only one had any effect at all, and took me from useless heap of junk to fully operational with all my files and progs: 


```

dpkg --configure -a

```

If that's any help to someone then good luck to you! 

Alex

---

