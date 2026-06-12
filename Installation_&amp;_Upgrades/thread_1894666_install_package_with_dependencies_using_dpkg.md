---
title: "install package with dependencies using dpkg"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by bilol on 2011-12-13
hi,
Say, I have a directory containing 10 debian packages p0.deb,p1.deb ,...and p9.deb. I can install all these packages at one go by `dpkg -i p*.deb`. But I want to install say,package p4.deb only.Let also p4.deb depends on p7.deb and p7.deb in turns depends on p2.deb.
My query is : how can I install p4.deb using dpkg so that p7.deb and p2.deb get automatically installed ? I must not install any other package than these three.
Any help will be highly appreciated.

---

### Post by zvacet on 2011-12-13
Try with 

```
sudo dpkg -i deb4 deb7 deb2
```

---

### Post by bilol on 2011-12-13
sorry .. this is not the solution I want. Please note that I know the package to be installed is p4.deb but don't know the name of the packages(p7.deb and p2.deb)upon which p4.deb depends.

---

### Post by Lampi on 2011-12-13
```
dpkg-deb --control p4.deb
```
will show you what p4.deb depends on

edit: easiest way:

```
dpkg-deb --field p4.deb depends
```

---

### Post by drmrgd on 2011-12-13
I'm not sure how to point to local .deb files that are dependencies.  However, if you dpkg -i a .deb file and there is an unmet dependency, you should be able to follow that up with:

```
sudo apt-get -f install
```

That should download and install the dependencies that you need to get you going again.  

Update:  after a quick Google search, I found this:

[Apt HowTo]("http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html")

This describes how to configure Apt for local packages, although it's a bit tedious perhaps.

---

### Post by bilol on 2011-12-14
To Lampi,
    Thanks a lot....I shall try it out.

To drmrgd,
  
   > That should download and install the dependencies that you need to get you going again.
 sorry...I assume that all the dependent .deb packages are pre-downloaded to the local folder.

---

