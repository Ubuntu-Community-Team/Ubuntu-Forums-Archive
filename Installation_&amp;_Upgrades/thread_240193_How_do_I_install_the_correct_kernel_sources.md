---
title: "How do I install the correct kernel sources?"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by luvr on 2006-08-20
I have just installed Ubuntu 6.06, and the **uname --all** command tells me the following about my kernel:
```
Linux wkst1 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
```
I would like to install the NVIDIA binary drivers from the NVIDIA web site, but I need the linux kernel sources to do that. However, when I fire up the Synaptic Package Manager, I cannot seem to find any *2.6.15-23* sources;  I **do** find **2.6.15.24** and **2.6.15-26.46** sources, though.

Where can I find the correct sources for the kernel that is installed on my system?

I had this very same problem with Ubuntu 5.10; I have never been able to correctly install the kernel sources so that I could compile the NVIDIA driver with that Ubuntu release, either.

In fact, under Ubuntu 5.10,  I initially installed the driver through Synaptic, but the driver got broken after I upgraded the kernel, and I have never found a way to get it to work again. That is why I decided to try and  install the driver downloaded from the NVIDIA site, but I have never gotten that to work, either.

I would very much appreciate it if you could help me find the appropriate sources (or an upgraded kernel with corresponding sources; that will do just as fine). Please be so kind as to **NOT** suggest that I install the NVIDIA driver through Synaptic; I really wouldn't want to go through that disaster again!

By the way - I'm not a Linux expert (in fact, I feel like a complete beginner), but I did experiment with Slackware before I came to Ubuntu. Under Slackware, I got the X Window System and KDE set up just fine, with the NVIDIA binary driver, and I succeeded in recompiling the kernel and reinstalling the driver under my custom kernel. Just to point out that I *am* somewhat familiar with the kernel, and its sources... ;)

---

### Post by luvr on 2006-08-21
Hmmm... I think I found a description of a procedure to install a 2.6.17 kernel from kernel.org. I lost the link, though, so I'll have to look it up again.

That will also be an insteresting opportunity to learn about compiling a kernel the Ubuntu/Debian way.

---

