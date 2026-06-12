---
title: "Problem installing kismet on 12.04"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by marcus-rangel on 2013-08-11
Hello everyone,

I am trying to install kismet on my 12.04 system and ran into this error below. I couldn't find anything similar on Google or here. Does anybody know what is happening ? Thanks in advance.

$ sudo apt-get install kismet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 kismet : Depends: libnl-3-200 (>= 3.2.7) but 3.2.3-2ubuntu2 is to be installed
          Depends: libnl-genl-3-200 (>= 3.2.7) but 3.2.3-2ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.


$ uname -a
Linux frink 3.2.0-51-generic #77-Ubuntu SMP Wed Jul 24 20:18:19 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by marcus-rangel on 2013-08-12
I had the wrong configuration in my "/etc/apt/sources.list". It was:

deb [https://www.kismetwireless.net/code/](https://www.kismetwireless.net/code/) oneiric kismet

When it should be:

deb [https://www.kismetwireless.net/code/](https://www.kismetwireless.net/code/) precise kismet

---

