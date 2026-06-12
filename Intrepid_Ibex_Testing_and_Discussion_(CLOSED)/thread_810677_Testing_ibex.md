---
title: "Testing ibex?"
date: 2008-05-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Wicked411 on 2008-05-28
Whats the best way to try ibex out? Or should I wait till aplha 1?

---

### Post by 23meg on 2008-05-28
If you're asking, you're best off waiting at least until Alpha 1.

---

### Post by zorkerz on 2008-05-29
The above response is correct however I think it would be more helpful to provide the information asked for. Leaving others with the ability to choose. Nobody will ever be able to learn how to get into testing without some help.

It seems that most people are taking an ubunt 8.04 hardy install and editing the sources.lst (/etc/apt/sources.list) config file. If your replace every instance of hardy with intrepid. That will make your install look at the intrepid repositories instead of the hardy ones for package updates.

Im currently wondering if there is another way to do this?

Often times you can do upgrades by typing in a terminal sudo or gksu "update-manager -d". This does not seem to work for intrepid yet so the above edit of sources.list might be the only method.

Can anyone confirm this?

BE WARNED intrepid is pre-alpha it will break. Only use it under circumstances where your system becoming suddenly unusable is OK with you.

---

### Post by ronacc on 2008-05-29
> **zorkerz said:**
> 
Im currently wondering if there is another way to do this?

Often times you can do upgrades by typing in a terminal sudo or gksu "update-manager -d". This does not seem to work for intrepid yet so the above edit of sources.list might be the only method.

Can anyone confirm this?

BE WARNED intrepid is pre-alpha it will break. Only use it under circumstances where your system becoming suddenly unusable is OK with you.

Right now changing your sources list is the only way , when daily builds start showing up and / or alpha 1 is out you could download that . Until a new version is actualy released as final update manager (from an earlier version) won't "see" it .

---

### Post by 23meg on 2008-05-29
> **zorkerz]
The above response is correct however I think it would be more helpful to provide the information asked for.[/QUOTE]

"*The* best way to test" depends, so there wasn't any concrete answer I could provide said:**
> Often times you can do upgrades by typing in a terminal sudo or gksu "update-manager -d".

No need for sudo, just "update-manager -d". But that probably doesn't work yet.

[QUOTE=ronacc]Until a new version is actualy released as final update manager (from an earlier version) won't "see" it .[/QUOTE]

It should, if you run it with the -d option, but not at this point in the cycle.

---

### Post by ronacc on 2008-05-29
r> **23meg said:**
> "


It should, if you run it with the -d option, but not at this point in the cycle.

I stand corrected .:) I never use update-manager from terminal I use apt-get instead . I had just assumed from the way the gui version of update-manager works that it would only offer releases . I know better than to assume but I do it anyway:confused:

---

