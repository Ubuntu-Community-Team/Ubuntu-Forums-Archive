---
title: "'Unresolvable' problem while initializing  package information"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by eduardo saxel on 2011-07-05
After that it says: "Please report this bug against the 'update-manager' package and include the following error message:


'E:Type '123456' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'"

---

### Post by dFlyer on 2011-07-05
What package were you trying to install?

---

### Post by eduardo saxel on 2011-07-06
None. It was an automatic update Ubuntu does almost every day.But now that you mention it, the problem started when I tried to install Geogebra:

[http://www.geogebra.org/en/wiki/index.php/Package_for_Ubuntu_and_Debian](http://www.geogebra.org/en/wiki/index.php/Package_for_Ubuntu_and_Debian)

 after that:

Ubuntu 10.04 and earlier

Open Applications > Accessories > Terminal and paste following commands into it (confirm by enter):

echo "deb [http://kondr.ic.cz/deb](http://kondr.ic.cz/deb) lucid main" | sudo tee -a /etc/apt/sources.list
wget [http://kondr.ic.cz/kondr.key](http://kondr.ic.cz/kondr.key) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install geogebra


And I did so... without being sure of what Ubuntu version I have.

---

### Post by plucky on 2011-07-07
> And I did so... without being sure of what Ubuntu version I have. 

From a terminal ```
lsb_release -a
``` should tell you which version you have.

> 'E:Type '123456' is not known on line 54 in source list /etc/apt/sources.list, E:The list of sources could not be read.'" 


Post output of ```
cat /etc/apt/sources.list
```

---

