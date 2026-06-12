---
title: "Installing .deb packages"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by anilriazi on 2009-12-03
Dear all
when I run the sudo dpkg -i pakagename.dbe command to install some package downloaded from packages.ubuntu.com site it failed with following message " dependency problems prevent configuration of packagename". what can I do for succesful installation without conection to internet, becuase I have problem with my dial up conection.
 
thanks a lot

---

### Post by Eremis on 2009-12-03
Go to Synaptic Package Manager, and see if anything pops up.
If you have a dependency problem it usualy fixes it for you.

---

### Post by ajgreeny on 2009-12-03
In gnome, gdebi does that as well. I don't know if there is an equivalent to that in kubuntu, but have a look.

Also, in gnome, if you double click the .deb file, gdebi opens and tries to install, telling you if dependencies are missing, and what they are.

---

