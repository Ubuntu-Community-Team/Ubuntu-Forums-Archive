---
title: "Lost Unity 3d after update"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by mhndm on 2011-11-17
when i install ubuntu 11.10 in my laptop the unity 3d work fine ..
but
when i add gnome and kde to my ubuntu 11.10 , i don't find the Unity 3d, only the Unity 2d work !
when i try to reinstall it i have the following error message :
---------------------------------------------------
sudo apt-get install unity
[sudo] password for xxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 unity : Depends: compiz-core-abiversion-20110828
         Depends: compiz-plugins-main-default but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
---------------------------------------------------------------------------
note the ccsm is installed i don't find the Unity plug-in into it.

---

### Post by mhndm on 2011-11-18
any help ?

---

### Post by raja.genupula on 2011-11-18
use 

```
unity --reset
```

if not then reinstall again 
```
sudo apt-get install --reinstall unity
```

if you got any problems like dependency issues then do 
```
sudo apt-get install -f
``` 
and then again do the installation. 

all the best .

make sure that unity plugin was enabled in your ccsm.

---

