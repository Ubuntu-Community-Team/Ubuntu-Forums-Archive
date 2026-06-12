---
title: "Chromium browser on 12.04.3"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by gkp2 on 2013-09-07
Hello all,

I have installed ubuntu 12.04.3 from scratch on my PC. I am trying to install chromium browser; but i get follow conflicts for packages:

```
$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 chromium-browser : Depends: libnss3-1d (>= 3.12.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Anybody having the same issue? Seems like the packages for 12.04.3 are broken. Is this a candidate for bug?

Thanks & Regards.

---

### Post by Frogs Hair on 2013-09-07
Post the output of the following.  ```
sudo apt-get update && sudo apt-get upgrade 
```

---

### Post by gkp2 on 2013-09-10
> **Frogs Hair said:**
> Post the output of the following.  ```
sudo apt-get update && sudo apt-get upgrade 
```

Thanks, it worked. I had disabled ubuntu-update repo in synaptic; had to enable it before.

---

