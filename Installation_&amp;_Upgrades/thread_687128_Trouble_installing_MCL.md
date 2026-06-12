---
title: "Trouble installing MCL"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by sior9842 on 2008-02-04
okay so im fairly new to using ubuntu and pretty much all linux operating systems.  i play a mud called achaea a lot and i wanted to dl a client for it so i found one called 'mcl' on google.  i dwnloaded the one that will open with something called 'deb' and it worked fine, opened after the download finished with the 'package installer.'  but it says

"Error: Dependency is not satisfiable: libstdc++5

what does that mean and how can i fix it?  thanks in advance for any help you guys can offer.

---

### Post by Partyboi2 on 2008-02-04
Mcl is in the ubuntu repo's to install it make sure under Software Sources (System>Admin>Software Sources) on the first tab you have the universe repo ticked.
then open a terminal (Applications>Accessories>Terminal) and type
```
sudo apt-get install mcl
```
this will take care of the dependencies for you.

---

