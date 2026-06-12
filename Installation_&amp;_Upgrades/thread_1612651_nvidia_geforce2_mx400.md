---
title: "nvidia geforce2 mx400"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by michaekcharlton on 2010-11-03
I have been unable to find a driver for my nvidia geforce2 mx400.  It's running in failsafe graphics mode.  Does anyone know what I need to do to make it work?  I'm a linux beginner, so please avoid jargon.

---

### Post by tommcd on 2010-11-03
What version of Ubuntu are you using? The newest Ubuntu is version 10.10.
The **nvidia-96** driver should support your MX400:
[http://www.nvidia.com/object/linux-display-ia32-96.43.18-driver.html](http://www.nvidia.com/object/linux-display-ia32-96.43.18-driver.html)
It is present in the Ubuntu repos:
[http://packages.ubuntu.com/maverick/nvidia-96](http://packages.ubuntu.com/maverick/nvidia-96)
See this to install it:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Note: You should not have to reomove **xserver-xorg-video-nouveau ** as it says there, as it should be blacklisted by default when you reboot the system. I did not remove it when I installed the nvidia driver for my 8600GT.

Write back if you need more help.

---

### Post by michaekcharlton on 2010-11-04
Ubuntu 10.10.

---

### Post by junaid_572 on 2012-02-21
I can help you if you still have this issue???, You have to install drivers from nvidia (version 96) and then edit xorg.conf, i will send you this file if you need it.

---

### Post by overdrank on 2012-02-21
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

