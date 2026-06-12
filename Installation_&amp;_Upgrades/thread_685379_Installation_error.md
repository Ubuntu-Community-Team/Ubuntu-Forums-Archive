---
title: "Installation error"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Iron23 on 2008-02-02
Ok well today I bought a 250 gig ext HD and just installed linux ubuntu 7.10

and i tried booting from the EXT HD and i got an error, when i unplugged it and i tried booting from my normal HD i get this message

GRUB LOADING STAGE 1.5

GRUB LOADING, PLEASE WAIT ...
ERROR 21

Ok thats the mesage, i thought that nothing could go wrong with my other HD when i did this. so ???? What do i do now?

I have alot of work that i need to do pretty urgantly and I need my computer up and running


WHAT DO I DO?????????????????? ahh im going crazy here. im on a different computer here but i cant use it forever, its not mine, i need my PC up and running in a few hours max

---

### Post by cotcot on 2008-02-02
> **Iron23 said:**
> 


WHAT DO I DO?????????????????? ahh im going crazy here. im on a different computer here but i cant use it forever, its not mine, i need my PC up and running in a few hours max

First of all you could supply a little bit more info. 
Nevertheless here are some possibilities.

What do you have on the internal HD ?

You could chroot in the ubuntu of your external HD with a liveCD.

You could try to reinstall grub like [[COLOR="Red"]this[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively")

Or you could try the [[COLOR="Red"]super grub disk[/COLOR]]("http://supergrub.forjamari.linex.org/")

Further you could reinstall ubuntu on the external drive the you do as on a pendrive  : [[COLOR="Red"]look here[/COLOR]]("http://supergrub.forjamari.linex.org/")

Finally I would suggest to consider installing ubuntu on the internal disk and use the external for data (shared with wathever else you have on it.)

---

### Post by Iron23 on 2008-02-02
> **cotcot said:**
> First of all you could supply a little bit more info. 
Nevertheless here are some possibilities.

What do you have on the internal HD ?

You could chroot in the ubuntu of your external HD with a liveCD.

You could try to reinstall grub like [[COLOR="Red"]this[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively")

Or you could try the [[COLOR="Red"]super grub disk[/COLOR]]("http://supergrub.forjamari.linex.org/")

Further you could reinstall ubuntu on the external drive the you do as on a pendrive  : [[COLOR="Red"]look here[/COLOR]]("http://supergrub.forjamari.linex.org/")

Finally I would suggest to consider installing ubuntu on the internal disk and use the external for data (shared with wathever else you have on it.)



On the internal i have XP and i want to keep it thats the only reason i bought the ext HD

---

### Post by Pumalite on 2008-02-02
Restore your Windows MBR and next time install to the external drive, with the internal disconnected.

---

