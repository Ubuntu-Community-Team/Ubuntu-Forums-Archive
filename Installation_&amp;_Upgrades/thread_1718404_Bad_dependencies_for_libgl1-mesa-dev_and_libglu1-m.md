---
title: "Bad dependencies for libgl1-mesa-dev and libglu1-mesa-dev"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by dewdrop_world on 2011-03-31
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```-->

```
 Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa-glx (= 7.7.1-1ubuntu2) but 7.7.1-1ubuntu3 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.7.1-1ubuntu2) but 7.7.1-1ubuntu3 is to be installed
E: Broken packages
```How do I get around this?

PS I saw this thread* but the solution follows an upgrade to 10.10. I'm on 10.04.

* [http://ubuntuforums.org/showthread.php?t=989075&highlight=libgl1-mesa-dev](http://ubuntuforums.org/showthread.php?t=989075&highlight=libgl1-mesa-dev)

Thanks.

---

### Post by zvacet on 2011-04-02
```
sudo apt-get -f install
```

---

### Post by dewdrop_world on 2011-04-04
Unfortunately, no, that doesn't help.

```
**sudo apt-get -f install libgl1-mesa-dev libglu1-mesa-dev**
[sudo] password for dlm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: libgl1-mesa-glx (= 7.7.1-1ubuntu2) but 7.7.1-1ubuntu3 is to be installed
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.7.1-1ubuntu2) but 7.7.1-1ubuntu3 is to be installed
E: Broken packages
```

I've also tried

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
```

... and then rerunning the *sudo apt-get -f install* command, with no change in the result.

Other ideas?
James

---

### Post by Dutch70 on 2011-04-04
This may not be worth the ink I'm using to type it, but try going to synaptic, click "edit" and then select "fix broken packages". It may do the same thing as apt-get -f install. I'm not sure, but maybe it's worth a shot.

---

### Post by dewdrop_world on 2011-04-04
Nope, it just says immediately (fraction of a second) "fixed broken packages" and then I'm still not able to mark libgl1-mesa-dev for installation. Same dependency error.

Bug report time?

---

### Post by Dutch70 on 2011-04-04
I definitely would. You may get lucky and be lead to a bug report that helps you find an answer too.

---

