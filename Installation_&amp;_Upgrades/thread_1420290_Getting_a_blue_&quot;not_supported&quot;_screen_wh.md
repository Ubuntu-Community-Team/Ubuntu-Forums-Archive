---
title: "Getting a blue &quot;not supported&quot; screen when attempting to boot Ubuntu"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by mcar2185 on 2010-03-02
I have an HP Verde PC with 5GB RAM, 500GB hard drive and nvidia 6150SE graphics card. I'm using my Vizio 26in HDTV as a monitor for the computer. Yesterday I installed Ubuntu 9.10 and after going to the GRUB menu and selecting Ubuntu, Ubuntu tries to load and then I am greeted with a blue "not support" screen. I'm confident that this is due to my monitor and the fact that xorg isn't configured correctly for this. I know because I had 7.04 on my old Desktop and had this exact same problem. Going through sudo dpkg-reconfigure xserver-xorg etc. worked for the old problem, but not for this one since apparently xorg has changed. 

So, here's my question: how do I reconfigure xorg via strictly the terminal? Graphics aren't supported, so it's gotta be through a method similar to [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760). Any ideas? I'm just about ready to give up on installing Ubuntu.

---

