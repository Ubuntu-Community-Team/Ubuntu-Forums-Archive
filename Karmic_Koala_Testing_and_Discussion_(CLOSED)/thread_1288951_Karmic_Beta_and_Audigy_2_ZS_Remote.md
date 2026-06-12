---
title: "Karmic Beta and Audigy 2 ZS Remote"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by josefcub on 2009-10-12
I long ago successfully had my Audigy 2 ZS remote control (RM 1500) working with Hardy, Intrepid, and Jaunty.   Well, I installed the Karmic Koala beta release, and it worked fine at first.  

A few days ago, after the kernel updated in Karmic, the remote stopped working.   My configuration didn't change, none of the daemons report anything wrong, yet irw no longer shows me that I'm pressing buttons on the remote.

I know it's just a beta release and unfinished, but does anyone else with an Audigy 2 ZS and remote have this problem with an updated Karmic beta?  
I used partimage to move back from the updated Karmic beta to Intrepid Ibex, otherwise I'd have more specifics posted.  Again, the same lirc configuration works between Hardy, Intrepid, and Jaunty.  I did read the forum posts about the broken lirc package (that's since been updated), but I still can't isolate the real reason it isn't working. 

I figure it may be fixed by the time the release happens, but if nobody else is having the problem is it even worth reporting more formally?

---

### Post by pezlin on 2009-10-21
I have the same problem as you although I have a different remote.

---

### Post by josefcub on 2009-10-21
> **pezlin said:**
> I have the same problem as you although I have a different remote.

I have a feeling about this...   Did you perchance perform a 'Partial Upgrade'?

I reinstalled Karmic beta, and applied all updates except the "partial upgrade" updates.   And my remote still works.

There's a thread here on the forums about the dangers of partial upgrades, come to think of it.

---

### Post by pezlin on 2009-10-22
> **josefcub said:**
> I have a feeling about this...   Did you perchance perform a 'Partial Upgrade'?

I reinstalled Karmic beta, and applied all updates except the "partial upgrade" updates.   And my remote still works.

There's a thread here on the forums about the dangers of partial upgrades, come to think of it.

I did the same, reinstall Karmic Beta, started Update Manager skipped the partial update and installed all the updates but no luck.

---

### Post by josefcub on 2009-10-27
I found out what was causing it on my system. 

Using [http://www.aaronetc.com/mediawiki/index.php/Soundblaster_Audigy](http://www.aaronetc.com/mediawiki/index.php/Soundblaster_Audigy), the first line is an addition to /etc/modprobe.d/alsa-base.conf to add options to the snd-emu10k1 module to enable the remote.  Well, after these updates (which included an alsa update if I'm not mistaken), that change disappeared.   Putting the line:

```

options snd-emu10k1 index=0 extin=0x3fcf extout=0x1fcf enable_ir=1

```

into /etc/modprobe.d/alsa-base.conf re-enabled my remote in Karmic.  Perhaps a dedicated /etc/modprobe.d/ .conf file is called for here?

---

