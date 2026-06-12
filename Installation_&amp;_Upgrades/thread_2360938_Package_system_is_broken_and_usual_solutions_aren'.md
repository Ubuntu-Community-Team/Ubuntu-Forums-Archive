---
title: "Package system is broken and usual solutions aren't working"
date: 2017-05-10
forum: Installation &amp; Upgrades
---

### Post by steedvlx600 on 2017-05-10
UbuntuMATE 16.04.02

I was installing Viber from their debian package. I have it installed on two other nearly identical systems with no problems. (The only differences are video adapters) But, for some reason the installation froze for a very long time... and broke my package system...

This has happened before. And, I thought it would be easily fixed using:

```
$ sudo apt-get install -f
```

Which returned the following:

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package viber needs to be reinstalled, but I can't find an archive for it.
```

So, I tried:

```

$ sudo apt clean
$ sudo apt-get update (finished normally)
$ sudo apt-get install -f (Returned the same results as before)
$ sudo dpkg --configure -a (finished normally without output)
```

Whenever trying to purge viber, I receive the same message the "viber needs to be reinstalled, but I can't find an archive for it."

I tried 
```
$ sudo apt-get purge --force-yes viber 
```

Which gives me:
```

$ sudo apt-get purge --force-yes viber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package viber needs to be reinstalled, but I can't find an archive for it.
```

I cannot run synaptic because it is not installed on this system... And, I cannot install it until I fix this problem

Anyone see what I am missing here?

---

### Post by ian-weisser on 2017-05-10
Two steps to fix:

1) Download the 'viber' package from [http://packages.ubuntu.com](http://packages.ubuntu.com). Or launchpad.net. 
Works best if you match the exact version number of the package.
Place the downloaded package in /var/cache/apt/archives.
The downloaded package should be owned by root.

2) Tell apt to reinstall the package (use the --reinstall flag)

---

### Post by steedvlx600 on 2017-05-10
Thank you for the suggestion. I was unsuccessful in getting this to work.

Neither  of the sites are listing a package for viber... It was initially downloaded  directly from viber.com in a deb package. I put THAT package in the  indicated directory and attempted the reinstall... which gave me:

```
$ sudo apt install --reinstall viber
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package viber needs to be reinstalled, but I can't find an archive for it.
```

I also tried everything in the original post with the same results.

---

### Post by ian-weisser on 2017-05-10
That usually means the viber deb is in the wrong dir, or it has the wrong permissions.
The latter is more likely if you manually downloaded and moved the deb.

Did the software ever work?
Are you actually trying to reinstall? Or do you simply want it to begone?

---

### Post by steedvlx600 on 2017-05-10
At this point, I would rather it begone.

I downloaded and installed using Gdebi package manager without moving the file anywhere. (I didn't know it was recommended) So, the package still sits in the Downloads directory.

It HAS worked on other systems with no problems. But, it has never worked on this particular system.

Thanks

---

### Post by ian-weisser on 2017-05-10
Try, and please show us the complete output:

```
sudo dpkg --install /path/to/viber.deb
```
Obviously, you must edit the path and package name appropriately.

---

### Post by steedvlx600 on 2017-05-11
Thank you. The fact that this was not obvious to me just shows how much I don't know about Ubuntu.

That, indeed shook it loose. The update system is functioning again. Although Viber still persists as a "dead" application. Fine for now. 

I will try to remove it later.

Thank you for explaining that.

---

### Post by steedvlx600 on 2017-05-11
Wenat ahead and issued:

$sudo apt remove viber

And, nothing bad happened. YAY!

---

