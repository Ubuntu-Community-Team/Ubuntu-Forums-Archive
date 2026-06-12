---
title: "what is the use of the Kubuntu DVD"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Ioky on 2007-05-06
I have a Kubuntu DVD and yes it work with my computer fine. but there is not selection of the package that i want to install in the installion. it only install the base system. with almost nothing in it. Synaptic is not in it. I just don't know how to get package from the DVD. And i wonder is that possible that you can install all the software and package you want in the installion? 

I am new on ubuntu-kubuntu. however it seem good to me but it just difference from the distro that I use before. In the matter of fact, I order the Kubunut 7.04 set from Linux Store.ca I wonder how to use all the Cd that come with it too. 

Thanks

---

### Post by aysiu on 2007-05-06
Paste these command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install gksu synaptic
gksudo synaptic
```

---

