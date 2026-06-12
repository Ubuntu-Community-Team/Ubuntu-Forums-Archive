---
title: "Partial package upgrades with Unity ppa"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by ddas4 on 2010-08-13
I am trying to get the talked about Unity netbook shell through my Lucid installation. When i add the repository ```
ppa:canonical-dx-team/une
``` i am offered a list of packages for upgrade which system says is also a partial upgrade.

I know i should not be accepting a partial upgrade since it runs the risk of breaking my Lucid install itself - so i have not.

How do i not reject these partial upgrades due to the repo addition & still install Unity ?

---

### Post by dino99 on 2010-08-13
looking at this ppa , there is a plasma failure on amd64, so if your system is a 64 bits installation, you cant install this package

otherwise into synaptic repo tab: deactivate (uncheck) this ppa then update to clean the sources

run: 
sudo apt-get install -f
sudo dpkg --configure -a

reactivate the ppa then update again, and see if things are better

---

### Post by Paqman on 2010-08-15
First of all, wait. New packages go into PPAs all the time, which may resolve any conflicts. In the meantime you could check the update out in Synaptic instead of Update Manager. It'll show you exactly what it intends to do to make the update happen, so you can find out what the problem is. If you're happy with what it's suggesting, run the update from Synaptic.

---

### Post by ddas4 on 2010-08-16
I was able to install Unity.
Did it over the terminal - works best.

---

