---
title: "Partitioning scheme for 400GB disk??"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by eentonig on 2007-06-07
Ok,

I want some advice from the community. I'm going to do a new install on a Desktop a acquired. And I'm going to install a 400GB HD in it (20GB just seems a bit too little).

Now I was trying to figure out a decent and flexible partitioning scheme.

- Primary 1 : ext3; 10GB,'/' # will contain my main ubuntu OS
- Primary 2 : ext3, 300GB, '/home' # no explanation needed.
- Primary 3 : ext3, 10GB, '/' # will be used to install the 'Development' Ubuntu. So Gutsy for now.
- Extended :
\\\\\ ext3 : 10GB, '/' # To have some room to try out other distro's.
\\\\\ ext3 : 50GB, '/var/ # I would like to run some 'servers'. Ie Apache and ftp. This way, I figure I can keep their data. 
\\\\\ 3GB : Swap # I'm going to put 2GB RAM


Do these numbers make sense? Why not? Better suggestions?

---

### Post by dabl on 2007-06-07
The numbers all make sense except 3 GB for swap.  I know, the rule of thumb is 1.5X RAM, but my experience (I think my hardware specs are in my signature - I have 4 GB RAM) is that swap usage simply doesn't happen.  I've watched it while encoding audio with both CPU cores approaching 100%, and still no swap usage at all.  So, set swap at 1.5 GB so you'll sleep at night, but don't waste any time looking for it to be used.

:D

Also, note that you will not actually set mount points for your non-Ubuntu root partitions (the other 10 GB roots) while you are installing Ubuntu.  You get one "'/" per Linux, AFAIK.  So they will appear as non-used partitions in the Ubuntu installation routine, but of course will be set up as "/" in the other OS filesystems.

HTH :)

---

### Post by eentonig on 2007-06-07
> **dabl said:**
> 

Also, note that you will not actually set mount points for your non-Ubuntu root partitions (the other 10 GB roots) while you are installing Ubuntu.  You get one "'/" per Linux, AFAIK.  So they will appear as non-used partitions in the Ubuntu installation routine, but of course will be set up as "/" in the other OS filesystems.

HTH :)

I know. I wasn' t going to set the mount points in the original install (I even doubt if you can create three mounts to '/'), but I didn't know how to call/addresse them otherwise.


Concerning the Swap. I agree, I've never seen it being used that much. But since I have ample diskspace and it allows me to hibernate. I don't care for those three 3GB.

---

### Post by eentonig on 2007-06-08
Installing as we speak. 

I always have to laugh when I'm installing Ubuntu. I remember the day my boss asked me to install quickly a linux box to try out some monitoring software. Ten minutes later he came in and saw I was surfing the net. "I need that box asap. Can you start installing please?"

"I'm doing it, It's installing right now. But while I wait, I might as well spent my time usefull. Not?"

Never forget the look on his face.

---

