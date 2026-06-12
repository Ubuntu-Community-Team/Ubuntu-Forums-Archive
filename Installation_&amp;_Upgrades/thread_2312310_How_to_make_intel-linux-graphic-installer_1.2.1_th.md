---
title: "How to make intel-linux-graphic-installer 1.2.1 think my Ubuntu 14.04 is the 15.10?"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by luisspb on 2016-02-03
Hi people,

I would like to install the latest Intel graphics drivers for my i3 CPU (I need to do this for OpenCL programming purposes).
But I only use the LTS versions of Ubuntu. And the intel-linux-graphics-installer only supports the latest release (that today is the 15.10).
Accepting all the risks, I would like to try the Intel installer anyway, before I convince myself that the only solution is to upgrade to 15.10, before the next LTS is released, as I would like to wait.

So, I ask you all: how can I deceive the Intel installer to think that my Ubuntu is actually the 15.10?
Is there any easy or secure and reversible way to do this?
(Like changing /etc/issue or anything like that - I tried that and, obviously, did not work).

Thanks in advance!

---

### Post by Vladlenin5000 on 2016-02-03
Intel graphics driver are already installed. You **don't need** anything else.

---

### Post by grahammechanical on 2016-02-03
There is a reason for everything

[https://01.org/linuxgraphics/forum/graphics-installer-discussions/do-not-use-ubuntu-14.04](https://01.org/linuxgraphics/forum/graphics-installer-discussions/do-not-use-ubuntu-14.04)

I hope you are not experimenting with your only working installation. Put in a dual boot of 15.10 or do it in a VM. That would provide the simple easy fix that you desire.

Regards.

---

### Post by mastablasta on 2016-02-04
You should use LTS enablement stack to pull in new drivers : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

and at the same time stay on 14.04 ;)

---

### Post by luisspb on 2016-02-09
Thank you, but

- if you read the entire post: yeah, as I've wrote before, I **needed** to run the intel-linux-graphic-installer. (I love when people do not stick to the question)

- "... folks began to experience difficulties when using the Graphics Installer." --> It seems a very weak reason for me.

- I had already done the LTS enablement stack. The installer does not work even with it, because it still sees the Ubuntu as 14.04, not as 15.10.

So, as I saw no solution for this problem, I did the 15.10 upgrade (clean install, actually). Sad :/
Thank you for your replies.

---

### Post by luisspb on 2016-05-27
I've finally found the solution. It's described here:
[https://allanbogh.com/2016/01/05/ubuntu-16-04-installing-the-intel-graphics-drivers-using-the-intel-graphics-installer-for-linux](https://allanbogh.com/2016/01/05/ubuntu-16-04-installing-the-intel-graphics-drivers-using-the-intel-graphics-installer-for-linux)

Regards,
Luiss.

---

