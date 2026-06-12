---
title: "Lubuntu 12.10 Mythtv dependencies"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by johnleonard on 2012-11-15
Hi

Trying to install mythtv on Lubuntu 12.10 through the Software Center but am getting a message saying that Package dependencies cannot be resolved.

Through apt-get I get this output:

john@john-desktop:~$ sudo apt-get install mythtv-frontend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 mythtv-frontend : Depends: mythtv-common but it is not going to be installed
                   Depends: libmyth-0.25-0 (>= 2:0.25.2+fixes.20120802.46cab93) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Has this happened to anyone else? 

Thanks

---

### Post by wyliecoyoteuk on 2012-11-15
try 

```
sudo apt-get update
sudo apt-get upgrade
```
first

---

### Post by johnleonard on 2012-11-15
Same result. Could it be that MythTV has not been updated in the repositories?

---

### Post by ringzhz on 2012-11-15
For me, libx264-120 was the root missing package. I manually downloaded and installed the appropriate *.deb file from [https://launchpad.net/ubuntu/quantal/+package/libx264-120](https://launchpad.net/ubuntu/quantal/+package/libx264-120) after selecting the "Published Version" appropriate for my computer. After installing that, apt-get should be able to successfully install the mythtv-backend package and its remaining dependencies.

---

### Post by someitalian123 on 2012-11-16
I also was having this issue when trying to update mythtv through the software updater. There is a dependence issue in the ubuntu repo, I had to add the mythbuntu 0.26 ppa. But the mythfrontend in 0.26 isn't as stable, it locks up every time I exit, I'm about to try downgrading libx264 to reinstall the version in the ubuntu repo.

---

### Post by johnleonard on 2012-11-17
> **ringzhz said:**
> For me, libx264-120 was the root missing package. I manually downloaded and installed the appropriate *.deb file from [https://launchpad.net/ubuntu/quantal/+package/libx264-120](https://launchpad.net/ubuntu/quantal/+package/libx264-120) after selecting the "Published Version" appropriate for my computer. After installing that, apt-get should be able to successfully install the mythtv-backend package and its remaining dependencies.


That worked. Thank you

---

