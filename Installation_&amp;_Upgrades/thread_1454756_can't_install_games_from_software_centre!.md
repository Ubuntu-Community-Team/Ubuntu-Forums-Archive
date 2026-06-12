---
title: "can't install games from software centre!"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-04-15
hello all,

this should be a simple one for you people, however not so for me!

after having used 9.10 KK for quite some time now, i got curious about the games.

i notice that while i am trying to install some of them - Airstrike, ACM Serial Combat Simulator, 20.000 Light Years Into Space etc, i am not able to do so.

i a message box saying the following -

" Requires Installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

>Details "

and the only option listed here is OK.

can anyone please let me know who i can install such games ? and since there seems to be such a security threat how do i distinguish the 'bad' from the 'good' games :)

thanks!

---

### Post by tommcd on 2010-04-15
I am not getting that when I try to install those games. What happens if you try to install them from the terminal with apt-get:
```
sudo apt-get install airstrike
```
Post the output of that command here.

---

### Post by maybeway36 on 2010-04-15
If you click OK, will it install them? I've seen this in one of two situations: either the repository doesn't have signed packages, or you need to run "sudo apt-get update".

---

### Post by tamagoji on 2010-06-08
i am getting some similar problem with a number of other applications (GIMP and gpaint included).
is it possible that the software sources must be updated or changed?

---

### Post by AM_SOS on 2010-06-08
hey tamgoji,
no idea really !
actually games are not a priority with me and i had moved on to other issues with ubuntu.
wondering if anyone has a fix on this one ...

---

