---
title: "Install third party packages after Ubuntu setup"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by Vuk Serbia on 2012-09-18
Hi there,

I have installed Ubuntu 12.04 without internet connection from USB live disk, so I didn't get third party software, and other packages that would come if i had internet connection.

Is it possible to install all those packages once setup is finished. 
I have installed Ubuntu while traveling so I had no internet connection, but now i have stable access to internet.

Thank you in advance

---

### Post by cortman on 2012-09-18
If you have internet access, you can open up the Ubuntu Software Center and install programs from there. It's as simple as clicking "Install".
If you don't have internet access, it gets a bit trickier. There are a number of ways you can install offline; using Synaptic, Keryx, etc. I even wrote little vb program for downloading .deb files for offline installation, which is what I use.

---

### Post by Vuk Serbia on 2012-09-18
That's ok, 
but I was wondering if I could install all of packages, that I would get through Ubuntu installation process

---

### Post by Vuk Serbia on 2012-09-18
Could it maybe be:

```
sudo apt-get install ubuntu-restricted-addons
```?

---

### Post by cortman on 2012-09-18
> **Vuk Serbia said:**
> That's ok, 
but I was wondering if I could install all of packages, that I would get through Ubuntu installation process

You want to do* what*?
If you installed Ubuntu, it comes with all the packages that Ubuntu comes with, regardless of whether or not you were online when you installed it.
Or are you referring to multimedia codecs? If so you want

```
sudo apt-get install ubuntu-restricted-extras
```

---

