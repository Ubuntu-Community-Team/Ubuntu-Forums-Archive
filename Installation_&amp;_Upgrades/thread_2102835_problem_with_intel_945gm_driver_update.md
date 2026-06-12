---
title: "problem with intel 945gm driver update"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by dady on 2013-01-08
Hello. Sorry for my bad english. 
I have ubuntu 12.04 and I Wanted upadet my graphics card intel 945gm.But here comes the problem . In Synyptic I have problem whit one of my package.They tell me that I have broken package libdrm-dev   2.4.40-precise-ppa1. In update manager give me a change that I update LP-PPA-glasen-intel-driver -----  libdrm-nouveau1. But I cant update this package. 
What can I do now ? 
Thank you for help

---

### Post by forkandles on 2013-01-08
Have a close look at this link for fixing broken packages:
[http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

In Synaptic you **may **be able to fix the broken package simply by using Custom Filters > Broken and then following further instructions. Try these 2 first.

You say that you cannot update the update LP-PPA-glasen-intel-driver.

Has your /etc/apt/sources.list file been modified to include this PPA's repository?

Look at this link:
[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

Go to &#8220;Adding this PPA to your system&#8221;, select your Ubuntu version (12.04)
And then copy these 2 lines to your /etc/apt/sources.list

```
deb http://ppa.launchpad.net/glasen/intel-driver/ubuntu precise main 

deb-src http://ppa.launchpad.net/glasen/intel-driver/ubuntu precise main
```

You can access your Sources List by opening Terminal and typing:

```
sudo gedit /etc/apt/sources.list
```

Click on "Reload" in Synaptic OR, in Terminal:

> sudo apt-get update

---

### Post by dady on 2013-01-08
Ty for helping me. Now is everyting ok. 
):P

---

