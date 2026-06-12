---
title: "Can't edit grub default boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by tvphil on 2011-05-02
I think my Natty 64 bit install is missing a dependency for gk, even though it shows up install in Synaptic. I have also tried using Start up Manager and the changes I make there don't show up after restarting either. I just want to change the default boot to number 4, Windows. Any suggestions are welcome, but I have tried all the ones I've found on this forum so far and none have worked, including editing etc/grub/default and saving with sudo update-grub. That's when I get a "gk not found" error.

---

### Post by wilee-nilee on 2011-05-02
> **tvphil said:**
> I think my Natty 64 bit install is missing a dependency for gk, even though it shows up install in Synaptic. I have also tried using Start up Manager and the changes I make there don't show up after restarting either. I just want to change the default boot to number 4, Windows. Any suggestions are welcome, but I have tried all the ones I've found on this forum so far and none have worked, including editing etc/grub/default and saving with sudo update-grub. That's when I get a "gk not found" error.

The ppa linked for the grub customizer has natty in its list, and drs305 is detailed in keeping thse upto date or stating otherwise, check it out.
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by tvphil on 2011-05-03
I failed to mention, I tried Grub Customizer too, with a different problem. After I did the admin login, it would tell me I need root privileges, which is stupid, because I just did that. But just for the hell of it, I logged out of my user desktop and into the root desktop as root. Same problem, so I was done chasing my tail with Grub Customizer. It seems to work for most people that use it, just like Start up Manager, that's why I think I'm missing a dependency, I just don't know which one.

---

