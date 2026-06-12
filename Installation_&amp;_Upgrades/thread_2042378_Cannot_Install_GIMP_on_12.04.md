---
title: "Cannot Install GIMP on 12.04"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by AceWholes on 2012-08-14
Hello everyone,

I had GIMP installed and working fine on my previous install of Ubuntu (11.10), and when I updated to 12.04, each time I would start GIMP, it would bring up errors and crash.

I removed Gimp, purged etc, however now when I try to install GIMP again, I get the following errors:

```

nick@nick-P5K-Premium:~$ sudo apt-get install gimp
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nick@nick-P5K-Premium:~$ 

```

I also tried to follow [this]("http://www.linuxquestions.org/questions/linux-newbie-8/e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-temporarily-unavailable-360554/") thread over at LQ.org but I was still getting the same error.

I have also tried to fix broken packages using **Synaptic>Edit>Fix Broken Packages** and I get the message at the lower left of the screen stating: "Successfully fixed dependency problems!"

Not sure what else to try...

Any help would be gratefully received.

---

### Post by AceWholes on 2012-08-14
Update:

By carrying out the following command:

```
sudo rm /var/lib/apt/lists/lock

```

I now get the following:

```
nick@nick-P5K-Premium:~$ sudo apt-get install gimp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gimp : Depends: libgimp2.0 (<= 2.6.12-z) but 2.7.3-2011052002~nn is to be installed
        Depends: gimp-data (<= 2.6.12-z) but 2.7.3-2011052002~nn is to be installed
E: Unable to correct problems, you have held broken packages.
nick@nick-P5K-Premium:~$ 

```

---

### Post by ajgreeny on 2012-08-14
The version of gimp that is trying to install is 2.7.3, so I presume you had a ppa for that beta version enabled in 11.10 and the ppa is still enabled now in precise.

The repository version of gimp in 12.04 is 2.6.12, so what you must do is disable or purge the ppa from your software sources, refresh/update the packages and then try again to install gimp.

You should always disable or better completely remove any ppa repositories from your software sources before doing a distro upgrade as they will normally present you with exactly the problem you have seen because the wrong distro version of the ppa will be enabled, ie onieiric instead of precise.

I suggest that having removed that incorrect ppa, you add the new one for gimp 2.8.  It is a very good gimp version and works well in 12.04.
[http://www.ubuntugeek.com/how-to-install-gimp-2-8-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gimp-2-8-in-ubuntu-using-ppa.html)

---

### Post by AceWholes on 2012-08-14
Thank you very much for your help!

I removed the ppa's from the old installation using **Synaptic>Settings>Repositories** click **Other Software** tab, and removing the ppa's which were added for the old version of GIMP.

I then followed the installation process that was in the link you sent, and (after ensuring that Synaptic was closed) it installed GIMP 2.8 successfully.

Thanks once again AJGreeny! :D

---

