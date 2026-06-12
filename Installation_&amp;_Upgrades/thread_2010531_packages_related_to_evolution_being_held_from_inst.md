---
title: "packages related to evolution being held from install"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by nighthawk3001 on 2012-06-25
I recently upgraded my computer from ubuntu 10.10 to 11.10. After that though, I noticed something odd happening when i run apt-get. Whenever I go to upgrade packages via the terminal, I get the following response:

```
root@shuttlecraft-5:/home/crazednighthawk# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  evolution-common evolution-plugins
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```


In light of that, I try to install evolution to see if I can clear up the two held packages, but the following happens:

```
root@shuttlecraft-5:/home/crazednighthawk# apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.2.2-0ubuntu0.1) but 2.32.2-0ubuntu7 is to be installed
E: Unable to correct problems, you have held broken packages.
```


I tried to remove evolution but since evolution isn't installed, it doesn't do anything. I use Thunderbird for my calendar and my email so I don't actually use evolution at all.

My question is there any way of either installing the packages for evolution so I can release the packages or can I just simply remove them from being held?

---

