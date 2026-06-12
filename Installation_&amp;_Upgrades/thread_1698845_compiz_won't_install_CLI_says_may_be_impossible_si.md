---
title: "compiz won't install: CLI says may be impossible situation"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2011-03-02
```

 sudo apt-get install simple-ccsm compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core but it is not going to be installed
                               Depends: compiz-core-abiversion-20091102
 compiz-fusion-plugins-main : Depends: compiz-core but it is not going to be installed
                              Depends: compiz-core-abiversion-20080618
 compiz-plugins : Depends: compiz-core (= 1:0.9.2.1-0ubuntu2~webupd8~maverick) but it is not going to be installed
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages


:~$ sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-core : Breaks: compiz-fusion-plugins-extra (< 0.9) but 0.8.6-0ubuntu1 is to be installed
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages




```

I upgraded from 10.04 and my compiz wasn't working so I uninstalled it in order to reinstall it and since then I've been having this issue.

Can anyone tell me how to fix this and get compiz back and working in maverick?

---

### Post by maddbaron on 2011-03-03
bump

---

### Post by hardfire_avk on 2011-04-30
I am having a similar issue

```

$ sudo apt-get install simple-ccsm
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

```

how do we go about this issue ?

---

