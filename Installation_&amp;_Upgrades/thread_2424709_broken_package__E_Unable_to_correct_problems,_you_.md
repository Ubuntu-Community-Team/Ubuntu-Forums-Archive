---
title: "broken package  E: Unable to correct problems, you have held broken packages."
date: 2019-08-13
forum: Installation &amp; Upgrades
---

### Post by thomas109 on 2019-08-13
Hi

strangewise i have a problem:
con not be solved by 
```
sudo apt upgrade --fix-missing
```
```
sudo dpkg –configure -a
```

leads to : strange: ```
dpkg: error: need an action option

Type dpkg --help for help about installing and uninstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;



```

```
sudo apt-get install --reinstall linux-headers-generic-hwe-18.04 linux-image-generic-hwe-18.04  linux-generic-hwe-18.04Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 linux-headers-generic-hwe-18.04 : Depends: linux-headers-5.0.0-25-generic but it is not installable
 linux-image-generic-hwe-18.04 : Depends: linux-image-5.0.0-25-generic but it is not going to be installed
                                 Depends: linux-modules-extra-5.0.0-25-generic but it is not installable
E: Unable to correct problems, you have held broken packages.



```


any idea how to solve this?

Thanks T

---

### Post by Impavidus on 2019-08-13
> **thomas109 said:**
> 
```
sudo dpkg &#8211;configure -a
```

leads to : strange: ```
dpkg: error: need an action option


```
That command should be```
sudo dpkg --configure -a
```That is, two dashes, not one en-dash. Did you copy the command via a word processor? Those applications often change pairs of dashes into en-dashes.

Let's see what's going on:```
dpkg --list | egrep -v ^ii\|^rc
dpkg --list | grep linux-
df -h
```
It looks like you somehow got the metapackage for kernel 5.0.0-25 (maybe from proposed), but the latest kernel in the repos is 5.0.0-23.

Edit: 5.0.0-25 is now in the repositories, so this should now be trivial to fix.

---

