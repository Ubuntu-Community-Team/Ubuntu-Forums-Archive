---
title: "Install asked for root password now can't sudo"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by kenironside on 2005-04-10
I installed Hoary final today and during the install I received an error indicating that the install couldn't complete the step of copying all the packages from the CD to the disk, probably because there wasn't enough space in /var. (It's a 120Gb disk, so that's unlikely)

I resumed the process at the next step, thinking that it wasn't  a train smash that the packages weren't copied. I then got asked for a root password, which I gave and then asked if I wanted to add a user name and password, which I did.

The rest of the install seemed uneventful, but now, when I want to run any app from the desktop that requires a sudo password, I get one or other of the following error messages:

Failed to run /usr/sbin/synaptic:
 Wrong password.

Failed to run /usr/bin/update-manager:
 Child terminated with 1 status

I can open a terminal (but not a root terminal) and su. In this case I can 'become'; root, but none of the Ubuntu sudo techniques work.

I searched the archive and my problem seems similar to the thread by plzdontspamme - "Can't run synaptic etc". He got some help but it didn't seem to resolve his problem. I didn't do what was suggested because it didn't resolve his issues.

I'd appreciate any assistance. My other Hoary pc installed fine and the sudo stuff works great.

Thanks, Ken

---

### Post by reid on 2005-04-10
Just a guess, but on my installation, when I sudo, the password I have to enter is the regular user PW, not my superuser PW.  I figured that something was set up wrong on my machine, but I odn't know what.  It is not that I have the same PW for root and my other account.

Hope this is your problem also, good luck!

---

### Post by chronos on 2005-04-10
[QUOTE=reid]Just a guess, but on my installation, when I sudo, the password I have to enter is the regular user PW, not my superuser PW.  I figured that something was set up wrong on my machine, but I odn't know what.  It is not that I have the same PW for root and my other account.[/QUOTE]
I think that is the way it is supposed to be :-)

---

### Post by reid on 2005-04-10
[QUOTE=chronos]I think that is the way it is supposed to be :-)[/QUOTE]
 Interesting.  I would imagine that you would need the superuser password to do superuser tasks.
Thanks for the info.

---

### Post by matthieufecteau on 2005-05-03
I had the same problem (synaptic not starting) and I think that is was about the loopback interface not starting at boot.

Look further into the second post of this thread : [http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback](http://www.ubuntuforums.org/showthread.php?t=29637&highlight=loopback)

---

