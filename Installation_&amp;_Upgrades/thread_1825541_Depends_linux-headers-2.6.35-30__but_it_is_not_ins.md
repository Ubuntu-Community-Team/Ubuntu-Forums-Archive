---
title: "Depends: linux-headers-2.6.35-30  but it is not installable"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by Kirk Wolf on 2011-08-15
The Update manager installed a new kernel for me, but the headers would not install.   I don't have a package "linux-headers-2.6.35-30"

> uname -r 
2.6.35-30-generic-pae

My /etc/apt/sources.list -

```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
```



[HTML]> sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-headers-2.6.35-30-generic-pae: Depends: linux-headers-2.6.35-30 but it is not installable
E: Broken packages
[/HTML]

Any help would be appreciated!

Kirk Wolf

---

### Post by phuzzie on 2011-08-15
I also ran into this issue today on my 10.04 box running the backported 10.10 kernel. It would seem that the repository metadata files are not up to date as the package is available via HTTP but is not found by Synaptic/apt-get even after a re-fetch.

Here's the work-around I performed:

>  wget http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.35-30_2.6.35-30.56_all.deb
 dpkg -i ./linux-headers-2.6.35-30_2.6.35-30.56_all.deb 
 sudo apt-get install linux-headers-`uname -r`

Hope that helps!
phuzzie

---

