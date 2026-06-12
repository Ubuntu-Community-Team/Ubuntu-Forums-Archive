---
title: "unable to boot ubuntu, gets the purple screen"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by aayus on 2013-06-27
I have Ubuntu in the Windows through WUBI. A week ago i upgraded the Ubuntu to the 13.04. Initially it worked completely fine but since today morning, Whenever I try to boot the ubuntu I get the Purple screen.
I power on my lappy, It shows me the two options whether I want to boot WINDOWS 7 or UBUNTU, whenever i chosse the ubuntu it goes to the purple screen and hangs there, nothing happens. On the contrary, the windows boots perfectly fine. 

Please anyone help me, I have some useful stuff in the ubuntu partition which i don't want to loose. 

How to get rid if this problem??

---

### Post by Bucky Ball on 2013-06-27
*Thread moved to **Installation & Upgrades**.*

There are not too many Wubi gurus about. It is really intended to 'try before you buy', or in this case install, not a long-term solution. Good luck with it. ;)

* Update: I am a bit confused. I thought Wubi had been dropped in 13.04. Read here:

[https://duckduckgo.com/?q=13.04+wubi+ubuntu](https://duckduckgo.com/?q=13.04+wubi+ubuntu)

Maybe that has something to do with your issue.

---

### Post by aayus on 2013-06-27
I installed ubuntu 12.10 through wubi and then updated it to 13.04 a week ago.

---

### Post by grahammechanical on 2013-06-27
Something in this thread might help you


[http://ubuntuforums.org/showthread.php?t=2157931](http://ubuntuforums.org/showthread.php?t=2157931)

It seems that you select Ubuntu and as it loads you hold down the right shift key. That should bring up the Grub menu. From there Ubuntu should be highlighted. Select Advance Options for Ubuntu and press Enter. Select Recovery Mode and at the Recovery Mode screen select Resume. If that gets you to a desktop go to System Settings and open Software & Updates and go to the additional Drivers tab and activate a video driver. You may need to experiment. Allow the utility time to search for drivers.

Regards.

---

