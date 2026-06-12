---
title: "Gutsy + not installing system updates on install"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by crunchyblack on 2008-09-25
Hey,

When i was installing gutsy, I remember seeing an error about not being able to install some system updates and what not. Firsty, im interested on how i can install these updates now that gutsy is running on my laptop.  Secondly, whenever i try to "sudo aptitude install" something, nothing happens... It can never find any packages and nothing ever gets installed. for example:

sudo aptitude install envyng-gtk


It finds nothing...there were a couple other things i tried as well, but it didn't download, upgrade or install any packages.

Any idea whats going on?


edit:
sudo apt-get update && sudo apt-get dist-upgrade

I also tried this to get the updates...same thing:

reading packafe lists....done
reading packafe lists....done
Building dependancy tree
reading state information...done
calculating update...done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:(:(

---

### Post by Partyboi2 on 2008-09-25
Open up Software Sources (System>Admin>Software Sources) and on the first tab make sure  that  all of the boxes except source code or installable from cd are enabled. Then click on the update tab and make sure that the first two are enabled, then close Software sources and try upgrading again or installing packages.

---

### Post by crunchyblack on 2008-09-25
thanks man, i only had universe and multiverse selected, was wondering why i could'nt get libstdc++5 to install my gfx card drivers. thanks so much!

---

### Post by robert shearer on 2008-09-25
envyng is for Hardy 8.04
envy is the app for Gutsy.7.10

see here for details....
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

