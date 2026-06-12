---
title: "Lynx: eee pc 1000H How to fix wireless"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andreab on 2010-03-27
I have a netbook eee pc 1000H and my wireless connection worked under ubuntu 9.10.

Now using Lucid Lynx has problem to connect to a wpa protected wireless. From time to time it connects but just for few minutes. The problem is linked to the kernel, but I do not know exactly what is

Anyway to solve it I installed the 2.6.33 kernel and I compiled the rt2860 driver

1- download the kernel from the ubuntu mainline:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

linux-headers-2.6.33-020633-generic_2.6.33-020633_i386.deb
linux-headers-2.6.33-020633_2.6.33-020633_all.deb
linux-image-2.6.33-020633-generic_2.6.33-020633_i386.deb

2- install them
sudo dpkg -i linux-*deb

more info to install the kernel here: 
[http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2010/02/25/linux-kernel-2-6-33-installation-guide-for-ubuntu-linux/)

3-reboot and select the new kernel from grub
...the wireless will NOT work

4-then install the driver following the info here:
[http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)

If you know a simpler way to solve the problem, please let me known

---

### Post by nrdlnd on 2010-04-11
I have a PCI-card with RT2860 in my desktop. After compiling and installing v 2.3.0.0 of Ralinks driver I got full N-speed with the old kernel and Lucid beta2. Before that only g-speed. I'm using wpa2.

---

### Post by zordo on 2010-04-26
I'm having similar troubles that are described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443"). Is this kernel update the only way to get the wireless working on eeepc 1000h? I see that this problem is pretty old and it has been reported more than a month ago. Is it going to go away with the official release of lucid?

I do get a connection but it takes several attempts(1-15) to get it to work. And to make things worse, sometimes the connection just cuts off with no visible reason.

---

### Post by tahina on 2010-04-28
> **zordo said:**
> I'm having similar troubles that are described [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/545443").

I have the same on an eee pc 901. 

The "undecided" severity and "unassigned" assignment, seems unfortunate. 

Wireless has been known to work in karmic, which makes this a regression, ie particularly irritating bug, right? And the 901 and 1000H are quite common netbooks, I should imagine.

But I don't know. Maybe there are enough legitimately higher priorities.

---

