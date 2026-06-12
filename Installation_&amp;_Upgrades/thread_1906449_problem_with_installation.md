---
title: "problem with installation"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by Ranjith1610 on 2012-01-09
I have installed ubuntu 10.10 in my xps 14 where in which there is no inbuilt 
intel hd graphics card(i7 first gen) 
when i tried to install my graphics card  driver using 

apt-get install nvidia-current 

it says that 

"The following packages have unmet dependencies:
 nvidia-current : Depends: dkms but it is not going to be installed
                  Depends: patch but it is not installable
                  Recommends: nvidia-settings but it is not installable
E: Broken packages"

even when i tried in synaptics package manager it says
that "You have held broken packages"

pls someone help for the problem

---

### Post by Basher101 on 2012-01-09
you seem to have some corrupt packages. Since i am not very familiar with package problems, i can currently only recommend a fresh re-install of Ubuntu to fix your problem.

regards

---

