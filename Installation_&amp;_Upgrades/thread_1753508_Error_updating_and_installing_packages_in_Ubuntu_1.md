---
title: "Error updating and installing packages in Ubuntu 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by rahul1810 on 2011-05-09
Suddenly since the last two days I am not able to install from Synaptic or apt with the error of broken packages.

I ran **sudo apt-get update** and got the following at the end. This I used to get earlier also and I just used to ignore it, because my packages were getting updated I was geting list of available upgrades from these packages.

```
Failed to fetch http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/rlinfati/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/rlinfati/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```But when I tried to install something (dropbox plugin ) I get the following.
```
sudo apt-get install unity-dropbox-share 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-dropbox-share : Depends: nautilus-dropbox but it is not installable
                       Depends: dropbox-index but it is not going to be installed
**E: Broken packages**

```The broken filter is of no help and I have googled a  lot on this but of no use.

I get this error when I try to update from Synaptic
```
[SIZE=3]**Could not download all repository indexes**[/SIZE]

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

---

### Post by zvacet on 2011-05-09
Those PPA doesn't have Natty packages and that is reason why you can not install.Look if you can find other PPA for packages you need with Natty packages it them.Of course remove PPA's you have in your source list and after that

```
sudo apt-get update
```

---

### Post by rahul1810 on 2011-05-09
> **zvacet said:**
> Those PPA doesn't have Natty packages and that is reason why you can not install

Thanks for the reply. 
These PPAs were working correctly till yesterday and were also receiving updates. They also in Mozilla Daily Build's PPA. 

I also searched using the script mentioned here, but the outcome showed that all PPA were compatible

[http://www.webupd8.org/2011/03/find-out-if-when-your-favourite-ppas.html](http://www.webupd8.org/2011/03/find-out-if-when-your-favourite-ppas.html)

---

### Post by zvacet on 2011-05-09
I didn´t run script.Simply added links to browser and here are results

[http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/]("http://ppa.launchpad.net/amandeepgrewal/notifyosdconfig/ubuntu/dists/")
[http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists]("http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/dists")
[http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/]("http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/")

and so on....

You see there is no natty packages.Search for other PPA for packages you want to install and use.

---

### Post by rahul1810 on 2011-05-09
Thanks for the reply. I deactivated all the PPAs giving the 404 error, and executed following.
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```However I am still getting the broken packages error

---

### Post by zvacet on 2011-05-09
Try with

```
sudo apt-get -f install
```

---

### Post by rahul1810 on 2011-05-10
Have tried that but still the same result. This is what the terminal shows now.

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-dropbox-share : Depends: nautilus-dropbox but it is not installable
                       Depends: dropbox-index but it is not going to be installed
E: Broken packages

```

UPDATE:
It seems the problem is with that particular package and everything else is working fine. Thanks for all the help zvacet!

---

### Post by zvacet on 2011-05-11
Is that package from PPA?If it is try to find other PPA if you really need that package.

---

