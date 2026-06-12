---
title: "How can I install Ubuntu with a different partitioned home directory?"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by thenetduck on 2007-03-21
Hi, 
  I have an iMac and us Parellels for linux because I just like Ubuntu better for most things (Except Reson, and Photoshop stuff) and would like to install it. I can install it just fine, however I have heard or read about partitioning your "Home" directory in a different partition so that you can install the "New" updated version of Ubuntu and not loose all of our programs and information. Does anyone know how I can do this? I don't really know what it's called so I didn't know what to search for. Thanks, 

 The Net Duck

---

### Post by alamba on 2007-03-21
This is how it goes (afaik):

You can create partitions for specific purposes, e.g. a / (root) partition is a must, a /opt partition is optional, a swap partition is a must (not sure about this???), similarly, if you create a seperate /home partition you can install a new version of ubuntu without reformating the /home partition and just adding it into fstab once the new version is installed. 

This saves you the hassle of backing up your data during a upgrade/re-installation. 

A

---

### Post by thenetduck on 2007-03-21
ya that's what I would like to do, but will it also keep my settings and programs I have installed by just saving my /home directory? 

 The Net Duck

---

### Post by floke on 2007-03-21
Yep. See this: 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

