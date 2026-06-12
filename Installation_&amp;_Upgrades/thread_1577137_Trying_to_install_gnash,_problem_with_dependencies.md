---
title: "Trying to install gnash, problem with dependencies."
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by gnush on 2010-09-18
Hello! I've been trying to install gnash but the installation has failed due to some dependencies not being installable. How do I fix this problem?
[I]

Some general specifications:[/I]

[LIST]
[*]64-bit.
[*]Ubuntu 10.04 Lucid Lynx.
[/LIST]

```

$sudo apt-get install gnash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnash: Depends: gnash-common (= 0.8.7-0ubuntu1) but it is not going to be installed
E: Broken packages

``````
$ sudo apt-get install gnash-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnash-common: Depends: libboost-date-time1.40.0 (>= 1.40.0-1) but it is not installable
                Depends: libboost-thread1.40.0 (>= 1.40.0-1) but it is not installable
E: Broken packages

``````
$ cat /etc/apt/sources.list.d/gnash-ppa-lucid.list
deb http://ppa.launchpad.net/gnash/ppa/ubuntu lucid main

``````
  gnash-common: Depends: libboost-date-time1.40.0 (>= 1.40.0-1) but it is not installable
                Depends: libboost-thread1.40.0 (>= 1.40.0-1) but it is not installable
```How do I install the dependencies?


[I]P.S.
Tell me if you want more information.[/I]

---

