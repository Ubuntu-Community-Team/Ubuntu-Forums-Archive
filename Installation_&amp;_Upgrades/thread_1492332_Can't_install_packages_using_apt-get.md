---
title: "Can't install packages using apt-get"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Rocafort8 on 2010-05-24
Hi, I tried to install some packages using "apt-get" but every time I try to install one it throws "Aborted" message, I tried several packages and combination allways with the same result.

But If I install them with Synaptics I can do it without any problem, as I know Synaptics uses apt-get to install packages so all this is a bit confusing to me . What can be wrong ?

apt-get version:

apt 0.7.25.3ubuntu9 per a i386 compiled on May 14 2010 15:33:48
I'm using Ubuntu 10.04 Lucid Lynx

Should I report some more information ?

---

### Post by SlidingHorn on 2010-05-24
May be a silly question, but are you using 

```
**sudo** apt-get install <program>
```

also, make sure you're using the correct package name.  You can run 

```
apt-cache search <searchterm>
```

to find packages in the repos

---

### Post by v1ad on 2010-05-24
yea i was about to say did u put sudo in front of it.

---

### Post by Rocafort8 on 2010-05-24
Yes, I'm trying

```

sudo apt-get install <program>

```I have also tried (I want to compile some program)
```

sudo apt-get build-dep <package> 

```"The following packages are going to be installed: <list of  packages>
0 actualized, <number> packages to be installed, ...
It's going to use <number>Mb of memory
Continue [Y/N]"

Then I press yes and then I see "Aborted"

I have tried with several packages so the name can't be wrong.

---

### Post by SlidingHorn on 2010-05-24
All it says is "Aborted"?  Nothing else?

---

### Post by Rocafort8 on 2010-05-24
Yes, only "aborted".

---

### Post by v1ad on 2010-05-24
ah now i get it. sometimes it wont install because dependencies are needed and it does not do it itself. look closer and figure out the dependencies and then install the actual program. if you don't mind please tell us what you are trying to install.

---

### Post by Rocafort8 on 2010-05-25
Ok, I made some progress, trying
```
sudo apt-get autoremove
``` I noticed A package "libgdata6" was going to be removed (when I tryed again the "Abort" message). Then I uninstalled usign Synaptic and I typed ```
sudo apt-get build-dep tomboy
``` and surprisingly it worked and installed plenty of packages.

Then I tried with ```
sudo apt-get install pidgin
``` but the "Abort" message appeared again.

I also tried to fix broken packages in Synaptics but seems not to have fix anything.

I tryed installing aleatory packages from Synaptics (just to try out which worked an which not) and some of them worked an some of them not.

---

