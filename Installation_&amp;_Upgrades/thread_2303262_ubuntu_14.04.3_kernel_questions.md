---
title: "ubuntu 14.04.3 kernel questions"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by razor_keen on 2015-11-17
Ive found a lot of information that seems helpful. I  was able to use a generic linux kernel and apply an rt patch, but this  is not enough for an ubuntu kernel. so i searched for an ubuntu kernel  that matched the headers found in the linux kernel projects rt site and i  think they may be compatable. The sites and documentation are as  follows:

1) a read me file explaining how to take the root linux kernel and turn it into an ubuntu kernel.

2) Directory of the ubuntu wily kernels used...( im pretty sure mine will be one of the amd64.deb versions.

3) directory of the rt patch that closely corresponds with these kernels.

4)  a wiki where there was some syntax in which someone modified a stock  kernel and kept the same headers (scroll down to the syntax

1) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.12-wily/README]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v4.1.12-wily/README")
2) [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.12-wily/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v4.1.12-wily/")
3) [https://www.kernel.org/pub/linux/kernel/projects/rt/4.1/](https://www.kernel.org/pub/linux/kernel/projects/rt/4.1/)
4)                         [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)
  
what i was hoping for was that someone with more terminal skills could provide me with the syntax required to build this kernel, and not change the config of the stock kernel. apparently i seem to misconfigure the stock kernel while making new kernels, using xconfig, which i dont like anyways. menuconfig seems more intuitive. 

i was hoping it would allow me to use ubuntu but when i need a machine controller for robotics i could switch to the rt kernel and still be familiar with the os. im new to linux and ubuntu but what ive found is that ubuntu is a totally diffrent animal than linux, so i thank you in advance for your help

its weird because getting a kernel from kernel.org is easy and applying the coresponding patch is as well but these do not allow ubuntu to function fully.

pls escuse that my shift button does not always work and i was wondering, later i could create a version that could switch between machine controller mode and regular ubuntu. itt most likely involve a custom bios and i need to create custom commands in term  so i can easily switch between the two. 

remember i am on a dell d830 using the nvidia quatro 140 so if there is something i need to do to load the driver in advance it needs to be included

---

### Post by razor_keen on 2015-11-17
Ive made some progress over the last three hours ive found apt get w3m may help

---

