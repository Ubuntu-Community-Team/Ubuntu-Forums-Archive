---
title: "HOW to check if CUDA in installed correctly on Ubuntu 10.04?"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by alfchung on 2011-02-27
Hi, I am trying to install CUDA on a server running Ubuntu 10.04. I followed the NVDIA instructions and installed the "CUDA toolkit for Ubuntu Linux 10.04", "GPU Conputing SDK code samples",and "Developer Drivers for Linux (260.19.26) (64 bit)", my system is 64 bit. This installation seems successful. everything downloaded from [http://developer.nvidia.com/object/cuda_3_2_downloads.html#Linux](http://developer.nvidia.com/object/cuda_3_2_downloads.html#Linux)

According to the messages of the installation packages, I added /usr/local/cuda/bin to PATH, /usr/local/cuda/lib64:/usr/local/cuda/lib to LD_LIBRARY_PATH

Then, I tried to run the sample programs. This strange things is, some of them can be run, and some of them don't even through they can be made with no problem.

For example,
$ ./convolutionSeparable will just stop there without any message, I can kill it by ctrl + c.

$ ./matrixMul outputs a line Device 0: "Quadro 5000" with Compute 2.0 capability

and stop there, again can be killed by ctrl + c

$ .clock works, outputs PASSED time = 12574

Press ENTER to exit...

$ ./simpleMultiCopy outputs PASSED

$ ./MonteCarlo outputs PASSED

$ ./simpleZeroCopy outputs PASSED

$ ./bandwidthTest stops there with blinking cursor for ever.

What is wrong with this?! How can I check if my CUDA installation is successful ? What is wrong wit those programs don't run? They don't even have a eror message.

Thanks a lot!

---

