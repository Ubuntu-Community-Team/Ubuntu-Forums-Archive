---
title: "Cannot update software"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by thepopasmurf on 2010-04-10
Hi,
I was messing with the synaptic trying to get it to authenticate third party software. It didn't work and now somehow none of my software updates will install. 

An example error I'm getting is

```
W: Failed to fetch http://ie.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.4ubuntu2.1_i386.deb
  403  Forbidden

```

Is there a way to revert to the default settings in the software manager?

---

### Post by Kyluke on 2010-04-10
Go to the synaptics package manger go to settings --> repositories --> then open the tab "Authentication" there will an option in the bottom right hand corner to "Restore Defaults" once that is done close that settings window and inside the synaptics package manger select the reload option.

---

