---
title: "can't install simple-ccsm"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2011-05-05
When trying to install simple-ccsm using synaptic, I get the following:

[IMG]http://farm6.static.flickr.com/5145/5691190367_b2d91c4f59.jpg[/IMG]

But when I check those dependencies, they are installed. I tried reinstall on both, but didn't help.

---

### Post by Dutch70 on 2011-05-05
What do you get when you run this command...
```
sudo apt-get install simple-ccsm
```

---

### Post by aeronutt on 2011-05-05
By the way, this is a fresh install of 11.04, I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages

---

### Post by Dutch70 on 2011-05-05
Run these commands & try again

```
sudo apt-get install -f
```
and 
```
sudo dpkg --configure -a
```

---

### Post by aeronutt on 2011-05-05
Ran those, then, got the same results:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages

---

### Post by Kaparen on 2011-05-06
I have/had the same problem as you. I settled with compizconfig-settings-manager and the fusion plugin instead.

---

### Post by aeronutt on 2011-05-06
I'd be happy with that, but UCC (Ubuntu Control Center) which I'm trying to load, has a dependency on simple-ccsm!

---

### Post by aeronutt on 2011-05-08
Anyone else have any ideas?

---

### Post by heyandy889 on 2011-07-13
Hello, everyone. I was also wondering about this, and turned up this bug report, [Ubuntu >> “simple-ccsm” package >> Bugs >> Bug #738168]("https://bugs.launchpad.net/ubuntu/+source/simple-ccsm/+bug/738168"). Looks like it's an incompatibility with Compiz 9.0. Maybe there's some way to downgrade Compiz? Although, that might mean losing the sweet Unity fat toolbar.

Sorry for the necro, but I thought it might be better to add a little info here than reopening discussion in a new thread.

---

