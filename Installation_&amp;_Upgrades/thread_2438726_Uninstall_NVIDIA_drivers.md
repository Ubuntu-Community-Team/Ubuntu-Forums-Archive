---
title: "Uninstall NVIDIA drivers"
date: 2020-03-17
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-03-17
Hello,

I am completely overwhelmed by compatibility problems of different components of my system, related to acceleratinng computing, i.e. NVIDIA drivers, CUDA, cuDNN, TensorFlow. On a forum I was suggested to use Anaconda which is, apparently, able to manage all this. The problem now is to remove all this staff before proceeding with Anaconda. I started with drivers using approach to this link:
[https://linuxconfig.org/how-to-uninstall-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-uninstall-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)
And immediately a problem:
```
pavel@ALABAMA:~$ sudo dpkg -P $(dpkg -l | grep nvidia-driver | awk '{print $2}')
[sudo] password for pavel: 
dpkg: dependency problems prevent removal of nvidia-driver-440:
 cuda-drivers depends on nvidia-driver-440 (>= 440.33.01).

dpkg: error processing package nvidia-driver-440 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 nvidia-driver-440

```

So, I'm looking for a robust approach that allow to remove whole NVIDIA staff.
Any suggestions ?
Thanks.

---

