---
title: "Help Needed"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by mrdfield on 2010-04-04
Hello I have been running Ubuntu 9.10 with no problems ,i decided to install Kubuntu 9.10 with a dual boot I installed them side by side I cannot connect wifi with Kubuntu and would like to delete it from my hard drive and keep Ubuntu 9,10 with all my files my question is I do not know how to do this and i dont want to erase the wrong one can anyone hekp in simple term thank you very much David

---

### Post by zvacet on 2010-04-05
If you have just these two partitions I suppose you installed Ubuntu first so  it should be at sda1 and Kubuntu at sda2.You said that on Ubuntu are all your files.Install gparted from synaptic and find it under system>administration.Opoen it ans see witch partition have more used space.That one is probably your Ubuntu partition.To be sure back up your files on dvd,usb.... just in case.Boot your Ubuntu live CD and when you get to installation stage delete partition you want.

P.S. If you just want to try Kubuntu you didn´t need to dual boot.You can simply install kubuntu-desktop with 

```
sudo tasksel install kubuntu-desktop
``` 

and if you don´t like it remove it with 


```
sudo tasksel remove kubuntu-desktop
```

---

