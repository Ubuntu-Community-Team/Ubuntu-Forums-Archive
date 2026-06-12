---
title: "Evolution gone"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by dox_drum on 2011-05-21
Hi people:

Yesterday I installed a PPA repository ppa:danilo/evolution, and try to upgrade evolution from there. However, there was a dependency fail, and it did nothing. Thus, I remove the repository. Nonetheless, today I find out that my installed version of evolution is gone! and when I try to install it again, it says that danilo's repository has a dependency fail... and it does nothing.

```
$ sudo apt-get install evolution
[sudo] password for oscar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 2.32.1-0ubuntu1~ppa0) but 3.0.0-2~danilo0 is to be installed
             Depends: evolution-data-server (>= 2.32.0) but it is not going to be installed
             Depends: evolution-data-server (< 2.33.0) but it is not going to be installed
E: Broken packages

```

Once more... note that I've removed Danilo's repository.

Can someone tell me how to reinstall evolution?

Thx. DOX

---

### Post by dox_drum on 2011-05-21
Bump!

---

### Post by greggc2006 on 2011-05-22
I did not add danilo's ppa but have the same issue:-
```
$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 evolution : Depends: evolution-data-server (< 2.33.0) but 3.0.0-1~build1 is to be installed
E: Broken packages

```

---

### Post by dox_drum on 2011-05-22
I've installed Thunderbird temporally... but I prefer Evolution :-(

---

