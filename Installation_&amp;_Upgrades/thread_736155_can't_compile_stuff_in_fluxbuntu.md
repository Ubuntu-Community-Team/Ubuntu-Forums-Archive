---
title: "can't compile stuff in fluxbuntu"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by ptero on 2008-03-26
well, i have fluxbuntu and can't compile stuff. 'till now i wanted to compile wicd and rebuild fluxbox, both didn't work with same error message (error: C compiler cannot create executables). i'll attach the config.log from fluxbox.

---

### Post by waspbr on 2008-03-26
have you installed the buid essentials?

put your install CD on and at terminal type

```
sudo apt-get install build-essential
```

this should enable you to compile

---

### Post by Oldsoldier2003 on 2008-03-26
> **waspbr said:**
> have you installed the buid essentials?

put your install CD on and at terminal type

```
sudo apt-get install build-essential
```

this should enable you to compile

probably better to get thenm from the repos since there have been some updates...
```

 sudo apt-get update
``` to update the package lists then Install build essential. Let us know if you need more help.

---

### Post by eriqjaffe on 2008-03-26
Also,

```
sudo apt-get build-dep fluxbox
```

---

### Post by ptero on 2008-03-26
yeah, thanks that solved THAT problem ;)
however, i got a new one (configure: error: Fluxbox requires the X Window System libraries and headers.), for which i also found a solution myself [here]("http://ubuntuforums.org/showthread.php?t=240678").
but xlibs-dev seems err... missing in the repos...
```
$ sudo apt-get install xlibs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xlibs-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xlibs-dev has no installation candidate
```
EDIT: well, synaptic helped me ;) (do i see it right, that there are no real console-based search tools for apt?). i installed xlibs-static-dev, which had 12 other dependencies (i guess, x11-dev was the one, i needed ;)
so, at least i got  through the ./configure routine right now ;)

---

### Post by eriqjaffe on 2008-03-26
> **ptero said:**
> (do i see it right, that there are no real console-based search tools for apt?)Sure there is!
```
sudo apt-cache search <whatever you're looking for>
```To narrow it down even further:
```
sudo apt-cache search <whatever you're looking for> | grep <refining term>
```
You could also use aptitude, although I really don't like it.

---

### Post by ptero on 2008-03-26
thanks a lot!
aptitude (btw, i don't like it either) doesnt really support real search (at least, i din't find it). it only selects in the list packages, which begin with... err, whatever i enter.

> sudo apt-cache search <whatever you're looking for> | grep <refining term>
lol, that seems necessary... apt-cache doesn't really show me everything containing my search string, but lots more... i don't know, why, but... well, what would we do without grep? :D
anyway, the whole system of apt seems very strange (if not pretty poor) to me...like, for instance it gone broken yesterday, as i wanted to remove fluxbox before compiling it (more on this - [here]("http://ubuntuforums.org/showthread.php?t=734835&highlight=fluxbox+toolbar+icons+broken")).
or today i wanted to install a flash plugin, but didn't know, which one, i've chosen something wrong in synaptic, then found something else and unchosen the first thing... that thing told me, it wanted to remove half my system!!! the same thing happend after i've chosen an other thing later (after restarting synaptics). i was lucky that i was sober and paying attention :D (however, that problem may have something to do only with synaptics, not the apt system)

---

