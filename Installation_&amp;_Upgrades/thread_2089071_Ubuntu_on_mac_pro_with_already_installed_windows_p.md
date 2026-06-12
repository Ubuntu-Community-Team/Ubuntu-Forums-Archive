---
title: "Ubuntu on mac pro with already installed windows partition"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by Wuway on 2012-11-28
Hello guys, I am totally noob to ubuntu. 

I have been always using MAC OS at home, but after mountain lion I got tired of it. At work we have fedora and performance really impressed me.

My problem is I am in the middle of a personal project and I wouldn't like to have any trouble about booting again into OSX till I get used to linux enough  to make the final jump.

Here is my question: I have a partition in my mac with a useless windows on it. If I install ubuntu from there, do I have to install the boot application recommended in the mac dual boot ubuntu installation? Or is there anyway to jump that step , install ubuntu over that windows partition and leave the boot of mac intact?

My computer is an 8 core mac pro early 2008

Thanks in advance for your advice 

PD I was looking in the threads for a similar question but I couldn't find it, if I missed it up I apologize.

---

### Post by 2F4U on 2012-11-28
> My problem is I am in the middle of a personal project and I wouldn't  like to have any trouble about booting again into OSX till I get used to  linux enough  to make the final jump.

Dual and even more triple booting can always be a problem. So if you can't afford any disturbance, why don't you try Ubuntu in a virtual environment such as VirtualBox. This can be installed either in OSX or in Windows and would allow you to run Ubuntu on top of any of the other OS's.

> Or is there anyway to jump that step , install ubuntu over that windows partition and leave the boot of mac intact?

My understanding is that OSX is not able to boot Ubuntu, so you would either need to use rEFIt or Ubuntu's boot manager grub. rEFIt can boot any amount of operating systems and is usually the suggested solution for triple booting.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by Wuway on 2012-11-28
> **2F4U said:**
> Dual and even more triple booting can always be a problem. So if you can't afford any disturbance, why don't you try Ubuntu in a virtual environment such as VirtualBox. This can be installed either in OSX or in Windows and would allow you to run Ubuntu on top of any of the other OS's.



My understanding is that OSX is not able to boot Ubuntu, so you would either need to use rEFIt or Ubuntu's boot manager grub. rEFIt can boot any amount of operating systems and is usually the suggested solution for triple booting.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
Thanks for your quick reply 2F4U. I think you are true, its not a good moment to make experiments, I better try it in a virtual machine till I can get rid of the project.
 
About the rEFIt thing I was wondering if having already installed a working windows would help, but I see if I want a double boot cant jump the rEFIt step no matter windows or not windows. 
Thank s again for taking your time to reply.

---

