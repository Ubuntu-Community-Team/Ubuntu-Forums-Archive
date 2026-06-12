---
title: "Install SSH &amp; Make w/o network (yet)"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by joseph_d on 2007-06-06
Hello,

It appears Ubuntu 7.04 doesn't have OpenSSH nor GCC/Make installed by default.

What I believe I need to do is set the CD-Rom as my source for sudo apt-get. 

The reason I need GCC/Make (if I'm asking for the right apps) is I'm trying to run make install on an ndiswrapper install and it's failing.

Does anyone have assistance for these steps? If I can get SSH on, then I'll be able to bring my desktop by the router and get on the network. Or, if anyone knows a way to do what I'm asking using a jumpdrive or the Ubuntu CDrom, please let me know.

Joseph

---

### Post by arkham on 2007-06-07
This is a little confusing.  I assume you can't just run apt-get install ssh or similar because you have not yet got your wireless card working and so do not have networking capability.  If that is the case and you cannot plug in the machine to physical ethernet temporarily then SSH will not help you because you will till be unable to get onto the network even if you do install it and hence will be unable to reach any other machines.

If you can connect to a physical ethernet port temporarily, then you can install the various packages easily like so once connected:

```
sudo apt-get install build-essential
sudo apt-get install ssh
```

---

