---
title: "libc6 broken packages"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by Zarate on 2007-03-26
Hi guys,

I was trying to install some stuff when I have accidentaly broken some libc6 packages:

libc6-dbg
libc6-dev
libc6-i686
libc6-pic
libc6-prof

If i try to reinstall them via Synaptic, it says it's going to remove a HUGE amount of other packages that are using libc6. Can't i just update those packages without removing anything else? Should i do it by hand?

I think i really screwed it up here : |

---

### Post by zvacet on 2007-03-26
**synaptic>edit>fix broken packages  **    or


```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by Zarate on 2007-03-27
Hi thanks for replying,

If i do it via Synaptic, i get the message that 96 other packages are going to be removed. I guess those packages depend on libc6. Would they be automatically reinstalled after fixing libc6?

Then, via console, i get this error:

```
The following packages have unmet dependencies:
libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is installed.
libc6-prof: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is installed.
libc6-dbg: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is installed.  
libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is installed.  
libc6-pic: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-13 is installed.
```

Is it a different problem and can i safely try to fix it? I've been reading lots of posts about libc6 and dependencies, but i don't want to get wild and do something even worst.

I don't even want to reboot :S

Thanks again

---

### Post by zvacet on 2007-03-27
It loks lik you need to upgrade that packages.Go to synaptic and find package and mark it for upgrades.

---

### Post by szxuzhou on 2007-03-27
Hi Zarate,
I have same experience with you. I destroyed my system after removing a bunch of application software depend on libc6. I should spend three nights on reinstalling my entire Ubuntu syste.
I have no idea how to upgrade libc6 so far. I also want to get answers from Ubuntu guru.

Good luck!

---

### Post by Zarate on 2007-03-27
> **zvacet said:**
> It loks lik you need to upgrade that packages.Go to synaptic and find package and mark it for upgrades.

Apparently Synaptic doesn't let you update a broken package...

So does this mean that i have to reinstall the system? I think that reinstalling libc6 and removing the dependat packages means reinstalling the system, because Synaptic is saying that is going to remove:

build-essential
g++
g++4.0
gnome-common
kdelib
libgtk
libgpg
ubuntu-base
ubuntu-minimal
...

Just to name a few...

Would be great if someone figures out how to fix it.

Thanks

---

