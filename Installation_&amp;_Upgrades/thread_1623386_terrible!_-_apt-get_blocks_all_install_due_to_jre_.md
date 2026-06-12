---
title: "terrible! - apt-get blocks all install due to jre deb"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by lastguy on 2010-11-16
I googled such topic, many people have same problem and no solid solution.
Likely, it come from I manually installed and may be removed sun jre or gnu jre 1.6. I think Ubuntu installed gnu version by default that is bad. I used to manually install jdk using alternatives on CentOS and it work fine. After I failed to use apt-get to install jdk1.5 I manually installed it. 
It is also possible due to some s/w installation, Anyway, now I try to use apt-get to install any s/w it says:

The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I tried all methods, force, repair, purge/remove/install, remove deb, list deb and manually remove all related folders I can found, no help. 

Ubuntu apt-get seems designed that when it try to remove a package it seeks dependency and if the dependecy is fail it is dead - whole apt-get dead. Repair/Remove cannot handle such simple case. Jdk is sth relatively independent, usually you untar and add link it works. 
I'm new to Ubuntu and used to admire it, now very disappointed after I tried 10.04/10.10 32/64 bit. Package mgr is a good thing, but hiring details from user is terrible idea. On this 10.10, I still need to manually install BCM wireless driver - I suppose such old device would have a stable driver built in.

Thank you very much for any valuable advice. Pls don't say sth like "you should use apt-get" as no help, things happen and I just need a solution to remove jre 1.6 register entry from apt-get.

---

### Post by drs305 on 2010-11-16
Edit: Post removed as overriding APT was not necessary. (See next post).

---

### Post by lastguy on 2010-11-16
problem solved. problem happens when you install jre it pops up a grey windows for license, and you must use cursor key to hilgh light <OK> then Enter, or else it enter such annoy state.
Just "sudo apt-get -f install", it continues on previous installation and use above method to complete it. After that you can remove/purge if you like.

---

