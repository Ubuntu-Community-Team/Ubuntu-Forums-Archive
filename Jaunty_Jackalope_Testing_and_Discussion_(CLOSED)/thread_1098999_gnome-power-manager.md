---
title: "gnome-power-manager"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosmonaut on 2009-03-17
Hi there!

Were do i find the settings -in *gconf-edidor*- for gnome-power-manager: So that I can set the cpufrequency behavior. AFAIK in 8.04/10 it was apps -> gnome-power-manager -> cpufreq -> policy_ac...In jaunty I can't find it.

K.

PS: Using a ibmt61; centrino/pro

---

### Post by smbm on 2009-03-17
There seems to be a number of things about CPU freq stuff that have changed, I don't know if they're all related.

See also:

[http://ubuntuforums.org/showthread.php?t=1098459](http://ubuntuforums.org/showthread.php?t=1098459)

---

### Post by chrisccoulson on 2009-03-17
All of the cpufreq code was removed from gnome-power-manager in the 2.23/2.24 cycle. gnome-power-manager has nothing to do with CPU frequency scaling anymore.

---

### Post by Kosmonaut on 2009-03-17
Thanks for your turbo fast answers!

So if cpufreq was removed, where I can I define the behavior of my CPU in Gnome then? Like if connected to power = ondemand, or if on Battery = powersave? It seems like the gnome.power.manager doesn't provide this feature, right?

Yours
K.

---

### Post by RAOF on 2009-03-17
> **Kosmonaut said:**
> ...
So if cpufreq was removed, where I can I define the behavior of my CPU in Gnome then? Like if connected to power = ondemand, or if on Battery = powersave? It seems like the gnome.power.manager doesn't provide this feature, right?
...

Right, it doesn't.  And this is at least partially because all governors other than **ondemand** will actually [*increase* power consumption on almost all workloads](http://www.codon.org.uk/~mjg59/power/good_practices.html).  Moral of the story: use ondemand.

---

### Post by Kosmonaut on 2009-03-18
Hm...I don´t really understand this whole issue -all in all it is rather confusing me (...powersave consumes more power then ondemand??? No more cpu control for user via Gnome???) but let´s pretend I did understand it... Still the whole explanation doesn´t really solve my problem. I *WANT* to select the cpufrequencies, because I want to control them. Yeah! I am kind of resistant to logical thinking ;-). 
I guess that my real problem that I am having, is also reported here [http://ubuntuforums.org/showthread.php?t=1099394&highlight=ondemand+default]("http://ubuntuforums.org/showthread.php?t=1099394&highlight=ondemand+default"). Meaning that performance is the default cpufreq. and not let´s say ondemand....
Well as it is a bug...it will be solved soon...

Cheers
K

---

