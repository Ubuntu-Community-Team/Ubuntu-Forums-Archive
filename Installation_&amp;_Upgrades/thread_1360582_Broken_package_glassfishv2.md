---
title: "Broken package glassfishv2"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by dominik_ap on 2009-12-21
Hello I have problem which already takes more than 2 months :) and I can't find any help on the internet.
When i want to run any action as apt-get install or upgrade or whatever i get this:
```

You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  glassfishv2: Depends: glassfishv2-bin but it is not installable
               Depends: imqv2 but it is not installed
               Depends: sun-javadb-core but it is not installed
E: Unmet dependencies. Try using -f.
```

I already run many times -f install and the results are following:

```
The following packages were automatically installed and are no longer required:
  sun-javadb-common imqv2 sun-javadb-core
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  imqv2 sun-javadb-common sun-javadb-core
Suggested packages:
  sun-javadb-client sun-javadb-doc sun-javadb-javadoc sun-javadb-demo
The following packages will be REMOVED
  glassfishv2
The following NEW packages will be installed
  imqv2 sun-javadb-common sun-javadb-core
0 upgraded, 3 newly installed, 1 to remove and 116 not upgraded.
...
Removing glassfishv2 ...
sh: Can't open /usr/share/glassfishv2/config/install/stop.sh
dpkg: error processing glassfishv2 (--remove):
 subprocess installed pre-removal script returned error exit status 2
glassfishv2-cddl-l license has already been accepted
Errors were encountered while processing:
 glassfishv2

```
and this is a problem. I can't upgrade my system, i can't do anything, because first it wants to remove glassfishv2, but it is broken somehow.
Even tried sudo dpkg --configure -a, but it makes no output

can you help me somebody?

PS: Before I had only this in glassfishv2 directory:
```
3RD-PARTY-LICENSE.txt  COPYRIGHT  jbi  License_Notice_Translated.pdf  LICENSE.txt
```
now I downloaded something from the internet, but didn't help me.

I am really confused, what I did wrong during upgrade of new kubuntu?

---

### Post by dominik_ap on 2009-12-21
bump

---

### Post by dominik_ap on 2009-12-25
hmm 3 days and nobody helped me... :( :( :(

---

