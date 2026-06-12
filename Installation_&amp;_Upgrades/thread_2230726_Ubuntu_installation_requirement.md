---
title: "Ubuntu installation requirement"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2014-06-20
I am thinking of installing LXDE on an old laptop for another user. But I don't want to confuse them, 'cause they already have Ubuntu 12.04 on their desktop. What are the minimum/recommended requirements for Ubuntu 12.04 32 bit?

This computer's specs:
Model: Acer Aspire 3680-2682
CPU: Intel Celeron M 1.86 GHz, 533 MHz FSB (probably only a single core)
Graphics: Intel Graphics Media Accelerator 950
HDD: 80 GB
RAM: 512 MB DDR2
LAN: 802.11 b/g Wireless LAN

---

### Post by papibe on 2014-06-20
Hi kakashi_12.

[Here]("https://help.ubuntu.com/12.04/installation-guide/i386/minimum-hardware-reqts.html") they are.

Although the laptop is within the recommendations, vanilla Ubuntu would lag a little on that hardware. I'd recommend taking a look at [Xubuntu]("http://xubuntu.org/") (Xfce), or maybe the even lighter based LXDE [Lubuntu]("http://lubuntu.net/") (as you are guessing).

There are even lighter distributions outside the Ubuntu family. For instance: Bodhi, CrunchBang Damn Small Linux, Puppy Linux, SliTaz, Tiny Core, etc.

Hope it helps. Let us know how it goes.
Regards.

P.S.: a run of their live environment (on USB) should give you a good hint on how they are going to perform.

---

### Post by yancek on 2014-06-20
You might take a look at the page below which gives minimun/recommended hardware for Ubuntu and several derivatives.  512MB RAM is absolute minimus for Ubuntu so if you get it installed it will probably be very slow.

[http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavor-of-ubuntu-desktop](http://askubuntu.com/questions/333795/what-are-the-system-requirements-for-each-flavor-of-ubuntu-desktop)

---

### Post by kakashi_12 on 2014-06-20
Thank you for clearing that up. I've heard good reviews about Pupply Linux. I use LXDE myself. Do any of these have a Software Center where I can click an Install button for programs? Rather than downloading a tar gz file and extracting it? I don't know where to extract files or how to download programs in Linux without the Software Center or Synaptic Package Manager.

Use also needs something that is friendly with Flash player. They go on facebook and youtube a lot.

---

### Post by mörgæs on 2014-06-21
Don't download and install stuff unless you are absolutely sure it's the only way. Lubuntu has a software centre and Synaptic, and else you should install using **apt-get**.

Flash will work but not fast.

---

