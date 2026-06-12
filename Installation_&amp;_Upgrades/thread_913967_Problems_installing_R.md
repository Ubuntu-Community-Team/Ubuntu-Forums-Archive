---
title: "Problems installing R"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by rgriffiths on 2008-09-08
I am trying to install R, and receiving the following error message:

sudo apt-get install r-base-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  r-base-core: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages


I tried to install libpango, but got the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
libpango1.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


Any suggested would be really appreciated.

-R

---

### Post by ekh on 2008-09-08
Maybe this is caused by a non consistent setup of your machine.

If you use 8.04 

Try changing the sw source to another mirror. 
( System > Administration > SW sources )

Then 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get update

and try installing again.

If you use 8.04 these steps are harmless, and maybe they solve your problem.

---

