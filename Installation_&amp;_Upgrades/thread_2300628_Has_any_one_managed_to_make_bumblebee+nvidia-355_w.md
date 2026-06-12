---
title: "Has any one managed to make bumblebee+nvidia-355 work on 15.10 ?"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by jeremy-munsch on 2015-10-27
I sadly trying to make this work without success, actually it is working but i get a blackscreen on boot, i think i915 won't load.
I have opened the following threads giving more related info :
[URL="http://http://askubuntu.com/questions/689924/bumblebee-intelnvidia-on-15-10-blackscreen-issue"]
http://askubuntu.com/questions/689924/bumblebee-intelnvidia-on-15-10-blackscreen-issue[/URL]
[https://www.kubuntuforums.net/showthread.php?69190-Bumblebee-Nvidia355&p=381043](https://www.kubuntuforums.net/showthread.php?69190-Bumblebee-Nvidia355&p=381043)

Know to be quick i know there is a i915 issue with 4.2 kernel, but i tried other kernels without success.
Some people recommends using nvidia-prime, but lets be honest, nvidia-prime is not a solution whereas bumblebee is, i don't understand why development has stopped for the bumblebee project omg.
But bumblebee is actually working i'm sure of it, it was working under 15.04 and 15.10 after upgrade but on fresh install of 15.10, nah just black screen.

If anyone has a clue of what component is spitting in the soup, please tell the world !

I have finally manage to make it work:
see [https://www.kubuntuforums.net/showthread.php?69190-Bumblebee-Nvidia355&p=381043](https://www.kubuntuforums.net/showthread.php?69190-Bumblebee-Nvidia355&p=381043)


1 install nvidia-355 and  nvidia-prime
2 select intel driver in nvidia panel and logout,
3 install bumblebee  only (not bumblebee-nvidia),
4 edit as  needed /etc/bumblebee/bumblebee.conf, 
   line22 KernelDriver=nvidia
   replace nvidia-current by nvidia-355
6 /etc/bumblebee/xorg.conf.nvidia
   uncomment    BusID  "PCI:01:00:0"
   as described here [http://askubuntu.com/questions/29044...vices-detected]("http://askubuntu.com/questions/290443/bumblebee-cannot-access-secondary-gpu-error-xorg-ee-no-devices-detected"),
7 you can now boot under intel card and use optirun and primusrun. It is working for me so far&#65279;, test with primusrun glxinfo

---

