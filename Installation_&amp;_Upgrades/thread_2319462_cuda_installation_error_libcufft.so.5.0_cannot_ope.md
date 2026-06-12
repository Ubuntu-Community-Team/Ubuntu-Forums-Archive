---
title: "cuda installation error libcufft.so.5.0: cannot open ......"
date: 2016-04-04
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2016-04-04
Hi,
    I recently installed CUDA support for an nvidia card on a PC running CENTOS without problems. I now tried the same on my Ubuntu-14.04 box but failed: When starting a program that uses CUDA I get the message:
    error while loading shared libraries: libcufft.so.5.0: cannot open shared object file: No such file or directory
    and, definitely, this library is not present. I went through the procedure described for Ubuntu here: [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads) but without success....
   libcufft.so.5.0, and many other cuda-related libraries are present under CENTOS here: /usr/local/cuda-7.5/targets/x86-64-linux/lib but under Ubuntu I do not find this file at the same location but just libcufft_static.a and a number of other files with these extensions. 
What do I have to do? Sorry, maybe a stupid question but I am lost!

Thanks a lot for hints, D-E

---

