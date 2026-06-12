---
title: "Help with CUDA &amp; Pyrit on Ubuntu 11.10"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by Spagnum on 2011-11-13
Hi guys

I have been trying to get CUDA to work on Ubuntu so I can use my GeForce GTX 550 Ti.

The reason I use Ubuntu, it is so easy to install via Wubii and then  dualboot next to my Windows machine, and thereby have access to the GPU  in contrast to virtual machines.

My graphics card should be supported by CUDA:
[http://en.wikipedia.org/wiki/CUDA#Supported_GPUs](http://en.wikipedia.org/wiki/CUDA#Supported_GPUs)

After I turning off the Xserver service (which have then been converted  into a lightdm service in 11.10), I used this guide to setup CUDA,  except the last part where you change the LINKFLAGS line becourse that  ****** it up so I could not compile it. But without it compiled fine.
[http://www.dickscheid.net/2011/10/19-cuda-ubuntu-1110/](http://www.dickscheid.net/2011/10/19-cuda-ubuntu-1110/)

Pyrit was pretty easy setting up..

My problem is that when I run Pyrit, it does not seem like it finds any  CUDA device. Besides, I can not start GUI for Ubuntu anymore. If i try  startting the Xserver service again it just gives me a black screen...

Any help would be appreciated!

---

