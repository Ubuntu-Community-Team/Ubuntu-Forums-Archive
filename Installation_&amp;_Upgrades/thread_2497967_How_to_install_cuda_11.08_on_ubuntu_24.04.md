---
title: "How to install cuda 11.08 on ubuntu 24.04"
date: 2024-05-24
forum: Installation &amp; Upgrades
---

### Post by vahidihooman on 2024-05-24
Hello. I have Ubuntu 24.04 on my PC and my graphic card is GeForce GTX 780ti. The latest version of Nvidia driver for this card is 470.239 and as it is mentioned in installation guide, Cuda 12.x is compatible with drivers >=525.60.13. So I have only one choice and it is install Cuda 11.x. But there is not any Cuda 11.08 deb(local) file for ubuntu 24.04. Can I use files related to ubuntu 22.04 instead of it? In other word, I download deb(local) file for ubuntu 22 and use it on ubuntu 24? Is it possible? How?
Is it possible to install a deb file belonged to a specific version of ubuntu on another version?
I appreciate if anyone guide and help me
Thanks

---

### Post by ubfan1 on 2024-05-24
Get the .run file you want from the Nvidia site, and see [https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063)
[https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010](https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010)

Have a running Nvidia driver, run the .run script,  skip the offer of an Nvidia driver, and option the lib and bin installs to the ...cuda-11.x directory. Avoiding the dependency problems and keeping all odd versions of libs out of the system areas.

---

### Post by MAFoElffen on 2024-05-25
Oh no. Not again... LOL ](*,)

Do a Forum search in the "Installation & Upgrades" Section. 

There is a long thread there were it was worked out was needed to do this for 22.04. It should be the same for 24.04, with minor changes in the underlying package versions in the base system.

---

### Post by MAFoElffen on 2024-05-25
I was wrong...

It was for 22.04 and installing the dependencies for Cuda 12.1 (also a previous version).

But what was used there for installing a previous version of Cuda might give you some hints.

---

