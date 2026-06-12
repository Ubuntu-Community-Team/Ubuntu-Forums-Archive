---
title: "Ktorrent dependencies broken, cannot install"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Voluntaryist on 2011-04-16
I have Ktorrent installed via the repositories and its always worked perfectly. Today I ran software update with KPackageKit and it installed updates. It told me that KTorrent had to be removed to continue and without thinking I hit ok. Now my KTorrent is gone. 

When I try to install it on the terminal with ```
sudo apt-get install ktorrent
``` it gives me this error. 


```
$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ktorrent : Depends: ktorrent-data (= 4.0.3-0ubuntu1) but 4.0.5-3ubuntu1~maverick1~ppa1 is to be installed
E: Broken packages
```

If I remove and reinstall ktorrent-data it doesn't help. build-dep doesn't help. autoremove and then trying to reinstall doesn't help.  

I'm not running some strange dev version of anything. I have a standard Kubuntu 10.10 amd64 installation and my KDE version is 4.6.2 from the regular repositories. I run updates (standard repositories) almost every day and have never seen anything like this before.

Can someone please help? I really like KTorrent and would very much enjoy using it again.

---

### Post by Dutch70 on 2011-04-16
Have you tried running...
```
sudo apt-get install -f
```

---

### Post by idef1x on 2011-04-16
I've the same problem and running "apt-get install -f"  doesn't help :-(

---

### Post by idef1x on 2011-04-16
just tried a work-around, but don't know yet if it breaks the system:

Just download the ktorrent-data_4.0.3-0ubuntu1_all.deb file from [http://packages.ubuntu.com/maverick/all/ktorrent-data/download](http://packages.ubuntu.com/maverick/all/ktorrent-data/download) 

then deinstall the wrong ktorrent-data:
```
apt-get remove ktorrent-data
```install the downloaded version : 
```
sudo dpkg -i ktorrent-data_4.0.3-0ubuntu1_all.deb
```after that just install ktorrent with : ```
apt-get install ktorrent
```**AND DON'T UPDATE THE KTORRENT-DATA package again!** ;-)

---

### Post by ~Plue on 2011-04-16
the problem would probably go away if you remove the PPA from which the 4.0.5 version is being pulled from..

---

### Post by idef1x on 2011-04-16
@~Plue most likely, but then the question is which PPA it comes from ;-)

Anyway I just did an "sudo apt-get update" again (did it allready before) and now apperently it does work with 4.0.5, so for the oriignal poster : just do an "sudo apt-get update" and install ktorrent again :-)
Should be solved now?

---

### Post by ~Plue on 2011-04-16
> **idef1x said:**
> @~Plue most likely, but then the question is which PPA it comes from ;-)

well, only someone who is using it would know the definite answer to that  :)
i'd take a guess at the kubuntu backports ppa or having maverick backports enabled, because 4.0.3 is supposed to be the stable release for the maverick repos.

(this *could* be wrong though)

---

### Post by Zorael on 2011-04-17
Use **aptitude** instead of apt-get. It will suggest solutions where apt-get just freaks out and exits.
```
$ sudo aptitude install ktorrent
```
In your case you want to downgrade ktorrent-data.

To show which ppa a package is from, you can use **apt-cache showpkg**. If the ppa has been removed it can't tell, though.
```
$ apt-cache showpkg ktorrent
```

---

### Post by idef1x on 2011-04-18
Thanks for the tips Zorael! Will be usefull next time apt doesn't understand :-)

---

