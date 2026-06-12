---
title: "Help with upgrading Ubuntu 7.10 to 686 kernel"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Timn on 2008-02-19
Hi Everyone,

I am hoping someone can help me out with this as I have been searching for about 2 days now and cannot find any more information. I have a T60 laptop with a centrino duo processor and have been trying to change the kernel from the 386 generic one to the 686 kernel. Everything I have found says I should be able to run synaptic and search for "linux-image" to find the packages I need for 686. The problem is there is no 686 packages in the list. I also have tried running the following commands but both ended in cannot find package:

sudo apt-get install linux-686
sudo apt-get install linux-image-686

Any help on this would be much appreciated.

Thanks,
Timn

---

### Post by manuelg on 2008-02-19
The reason why there are no 686 packages is because they don't exist.  If you want to install a kernel specific to the i686, you'll need to compile your own kernel image and kernel headers. Having said that, for most people the generic kernel will work just fine.  But if you want to learn how to do it, there are plenty of tutorials, check around.  

Best regards

---

### Post by Timn on 2008-02-20
Thanks for the info.

Timn

---

