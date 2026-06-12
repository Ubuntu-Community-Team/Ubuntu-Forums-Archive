---
title: "Solving unmet dependencies within the same application"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2012-09-06
Is there any solution to this?
> $ sudo apt-get install apache2-mpm-prefork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 apache2-mpm-prefork : Depends: apache2.2-common (= 2.2.22-1ubuntu1) but 2.2.22-1ubuntu1.1 is to be installed
                       Depends: apache2.2-bin (= 2.2.22-1ubuntu1) but 2.2.22-1ubuntu1.1 is to be installed

Somehow, the apache2-mpm-prefork provided in Synaptic is not compatible with the other elements of Apache. Why would this be? Can I fix this? 

I'm trying to switch from apache2-mpm-worker to apache2-mpm-prefork because thats what the mediawiki package requires.

---

