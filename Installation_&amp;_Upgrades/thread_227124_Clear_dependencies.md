---
title: "Clear dependencies"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by aweller on 2006-08-01
Dear all,

I am relatively new to Ubuntu and am enjoying the experience thus far. I have however, clicked on Add/Remove programs once too many times and my dependencies are all over the place.

What I would like to do is check to make sure that everything is in order and remove all the 'dependencies' that really aren't needed anymore to remove them. How do I do this? It doesn't appear that Synaptic has this option...

Cheers, Andy

---

### Post by Ziox on 2006-08-01
> **aweller said:**
> Dear all,

I am relatively new to Ubuntu and am enjoying the experience thus far. I have however, clicked on Add/Remove programs once too many times and my dependencies are all over the place.

What I would like to do is check to make sure that everything is in order and remove all the 'dependencies' that really aren't needed anymore to remove them. How do I do this? It doesn't appear that Synaptic has this option...

Cheers, Andy

that is the downside of the great too apt and its gui's.  When installing using apt or synaptic (add/remove), they would resolve dependencies for you.  However, upon uninstall, they only remove the apps you tell them to remove, no dependencies whatsoever.  There is a way to get around this. Instead of using GUI's or "sudo apt-get install..." use the command "aptitude"

sudo aptitude install gaim-themes for example would resolve all the dependency problems (say other necessary plugins)

after you've used gaim-themes for a bit, and you decide to remove them:

sudo aptitude remove gaim-themes would remove the package "gaim-themes" and any other apps/packages that's related to it.  However it removes other related packages only if there are no conflicts with it and other apps.

So my suggestion: find the "name" of the package you want to install in synaptic/adept.  Then copy the name to terminal and do:

sudo aptitude install programname

this would make cleaning up a breeze.

Hope this helps.

p.s. Check my link "General Help" in my signature to read more about aptitude and apt-get. (it is along the left side of the page)

---

### Post by aweller on 2006-08-01
Thanks Ziox,

I did read in the forums stuff related to aptitude, but was a little lost - perhaps because it's so simple and was waiting for the complex part ;)

If aptitude is so much better, why doesn't Ubuntu replace apt-get with it for the Add/Remove programs component?

Now, if I have installed packages with Synaptic (apt-get) and use aptitude for their removal, will it remove the dependencies too?

Andy

---

### Post by Ziox on 2006-08-01
> **aweller said:**
> Thanks Ziox,

I did read in the forums stuff related to aptitude, but was a little lost - perhaps because it's so simple and was waiting for the complex part ;)

If aptitude is so much better, why doesn't Ubuntu replace apt-get with it for the Add/Remove programs component?

Now, if I have installed packages with Synaptic (apt-get) and use aptitude for their removal, will it remove the dependencies too?

Andy

I really can't understand why Ubuntu still uses apt-get, i think it's probably because Debian uses apt-get, and there are something about them...

anyhoo...as for removing dependcencies with apt-get - no. and if you mean to use aptitude to remove dependcenies -no.

only apps/dependencies that have been installed by aptitude can be cleanly removed by aptitude...

also another thing that i have to mention, automatix uses apt-get which i don't like and don't want, so i edit their script manually so that it would use aptitude...wish everything is that easy. :rolleyes:

---

