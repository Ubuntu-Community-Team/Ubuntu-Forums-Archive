---
title: "? about synaptic and packages"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by braganfamily on 2008-05-31
I have a computer at the office which is connected wirelessly to my router.  I am wanting to install Hardy on it but the wireless driver will need ndiswrapper (belkin f5d5070 rev.e).  Whe I install ubuntu, I will not be able to connect a wired connection to load ndiswrapper and associated dependencies.  Is there a way to load them on another computer and transfer them to that computer inorder to load the packages for ndiswrapper?

I hope I was clear enough.  I want to load ndiswrapper on a pc to enable the wireless.  That pc will not have an internet connection until after it is loaded.  is there a way to get ndiswrapper loaded without an internet connection?

Thanks.

---

### Post by aysiu on 2008-05-31
Yeah, you can download them from [http://packages.ubuntu.com](http://packages.ubuntu.com), transfer them via USB stick to your Ubuntu computer's desktop and then type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by braganfamily on 2008-05-31
aysiu,

Thanks!  I'll give it a try.  Will the package for ndiswrapper have all dependencies?

bobby

---

### Post by aysiu on 2008-05-31
> **braganfamily said:**
> aysiu,

Thanks!  I'll give it a try.  Will the package for ndiswrapper have all dependencies?

bobby
No. You will have to download all the dependencies manually.

---

### Post by braganfamily on 2008-05-31
ok.  Thanks.

bobby

---

