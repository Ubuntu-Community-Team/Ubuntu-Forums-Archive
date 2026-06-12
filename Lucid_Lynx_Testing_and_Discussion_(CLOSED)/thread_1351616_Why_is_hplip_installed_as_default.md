---
title: "Why is hplip installed as default?"
date: 2009-12-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-12-10
Takes room up on live cd and can be installed after if you have a hp printer.

??

---

### Post by mdurham on 2009-12-10
> **philinux said:**
> Takes room up on live cd and can be installed after if you have a hp printer.

??

I agree, it does seem strange.

---

### Post by nystire on 2009-12-11
Possibly because it it a "generic" driver for most of the HP printers out there (and there are many of those)? This way, new users will be able to have a working printer out-of-the-box, which is always a nice thing to see.

---

### Post by Psumi on 2009-12-11
hplip was installed by default on my 9.10 install. So?

---

### Post by jmmL on 2009-12-11
This seems to me to be a good candidate for removal.

There should be a list of questions asked after install: 
"Do you

[LIST]
[*]own a HP printer?
[*]own a Palm Pilot?
[*]want to do advanced image editing?"
[/LIST]
Checking boxes next to them would install the relevant packages. Automatic detection for deciding whether to install things like printer drivers could be risky, as many may not have them attached at the time of install.

---

### Post by steeleyuk on 2009-12-11
> **jmmL said:**
> Checking boxes next to them would install the relevant packages. Automatic detection for deciding whether to install things like printer drivers could be risky, as many may not have them attached at the time of install.

You could still check for drivers from the Internet upon plugging the printer in and ask the user to confirm installation.

Though removing something like this would have to make the replacement worthwhile. Nobody seems to have suggested something to replace hplip... just suggested for removal because its 'big'.

---

### Post by yelo3 on 2009-12-11
Oh, come on! there is plenty of packages installed by default to support hardware! Why are you complaining about it?

---

### Post by phenest on 2009-12-11
What about users that want to run the live cd and need access to their hp printer? No different to all the other hardware support on the disc.

---

### Post by philinux on 2009-12-11
> **phenest said:**
> What about users that want to run the live cd and need access to their hp printer? No different to all the other hardware support on the disc.

Cups+gutenprint and foomatic have available drivers or install hplip when using the livecd. Other printers/manufacturers would need drivers installing.

I'm not complaining, just asking a question?

---

