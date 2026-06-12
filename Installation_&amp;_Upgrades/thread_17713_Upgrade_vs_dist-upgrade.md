---
title: "Upgrade vs dist-upgrade"
date: 2005-03-02
forum: Installation &amp; Upgrades
---

### Post by Joeb on 2005-03-02
I was lurking on a board of another distro (kind of rhymes with the name of a certain city in Tennessee) and there was a discussion of using apt-get upgrade vs apt-get dist-upgrade (which would also apply to the regular and smart-upgrades in synaptic).

Anyway, to make a long story short, although dist-upgrade worked for many people, the developer didn't recommend it because it could a) break things and b) made the distro more debian like instead of the distro itself.

Now to be honest, I've only done the dist-upgrade when going from Warty to Hoary, but in Synaptic, I do the smart-upgrade all the time.

So, I guess, the question is "What is the preferred upgrade method for Ubuntu?"


Joeb

---

### Post by Marauder1 on 2005-03-02
i think, but i can be wrong, that upgrade or dist-upgrade
are not the point here. MIxing all kinds of repositorie and
using the 2 to make an upgrade could lead to problems.
I use only warty's repos and run both commands and i don't
have any problems.And when i want a certain new software
which is not in warty, i just enable the repo, install it and then
disable it.
This way when i make an upgrade this new software wont
be included.

Works for me !!!

Ciao.

---

### Post by Joeb on 2005-03-02
Actually, that is pretty similar to what I do, but they were pretty adamant about not using dist-upgrade/smart upgrade because it could/would potentially break things. 

I realize that if one had their repositories pointed to the generic debian ones (or a lot of other non-Ubuntu repositories) that it could quite definately cause problems, but I would think that would be the case regardless of upgrade vs dist-upgrade.  

Again, they seemed to be concerned only with dist-upgrade (and smart upgrade in synaptic), which is why I ask the question here.


For the record, I haven't had any problems with the smart upgrade in Synaptic.  Although, I did notice that doing a dist-upgrade from Warty to Hoary loaded a lot more stuff than doing a clean install of Hoary Array 5 followed by an upgrade.  But that could just be related to what were the dependencies of the packages at the time the upgrade or install was done.


Joeb

---

### Post by Marauder1 on 2005-03-02
agree !!! :-D

---

