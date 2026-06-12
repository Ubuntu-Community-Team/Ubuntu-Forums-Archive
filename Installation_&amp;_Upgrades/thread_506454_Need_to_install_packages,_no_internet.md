---
title: "Need to install packages, no internet"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by MobileDev on 2007-07-21
I'm sorry if this my seem like a redundant question, but I can't find exactly what I am looking for in this forum. You see, I do not have an internet connection, but I overcame that limitation by using a USB hard drive and the local library computer room. My problem is that I want to know how to add a directory on my USB hard drive so that Synaptic knows about all the packages I downloaded from the library (that is, I can view them in the main window and install them). I have been using the GDebi thing that opens up every time I double click on a package for a while now, but it can only install one package at a time. I wanted to install the SDL development libraries so that I could learn how to make games, but it seems that three dependencies (libxext-dev, libxi-dev, and x11proto-xext-dev) all depend on eachother, meaning that each one has the other on the dependencies list. How do I install all three at once? Please help me.

---

### Post by drekon_v1 on 2007-07-21
You can install all three three packages at once on the command line:
```

cd /path/to/files
sudo dpkg -i pkg1.deb pkg2.deb pkg3.deb

```

If it complains about unresolved dependencies, you'll have to download those packages you need and install those as well in the same manner.

There's also APTonCD which can create repositories on DVDs and CDs:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by MobileDev on 2007-07-22
But is there any way to add my USB hard drive(or any local directory for that manner) to Synaptic's database so that it always shows packages that I have downloaded at the library? I will try your suggestion and let you know if it worked or not.

---

### Post by melancholeric on 2007-07-22
Here's a nice howto: [http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/)

Here's another: [http://cutecomputer.wordpress.com/2006/01/12/local-software-repository-for-apt-get/](http://cutecomputer.wordpress.com/2006/01/12/local-software-repository-for-apt-get/)

They all assume you have the .debs at /var/cache/apt, but that doesn't make a huge difference really.

---

