---
title: "need to install gd"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by mujahied on 2011-12-10
hi all i am trying to install gd with all the dependencies i even downloaded the gd package and still shows that it hasnt been installed 

when running install this is the error

[PHP]apt-get install php5-gd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-gd: Depends: libjpeg62 (>= 6b1) but 6b-15ubuntu1 is to be installed[/PHP]

---

### Post by raja.genupula on 2011-12-10
sudo apt-get install -f
in your terminal type that code and then try installing again

---

