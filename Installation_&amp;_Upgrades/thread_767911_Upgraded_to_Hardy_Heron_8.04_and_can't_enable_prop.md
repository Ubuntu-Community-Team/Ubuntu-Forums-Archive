---
title: "Upgraded to Hardy Heron 8.04 and can't enable proprietary nvidia drivers anymore"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Tiny Grasshopper on 2008-04-26
Hello

I had Ubuntu 7.10 installed with dual SLI on a pair of nvidia 7600GTs. It was using the proprietary nvidia driver that was enabled via the restricted drivers manager. I was getting random freezes when I played games so I thought I would upgrade the nvidia drivers to the ones on nvidia's site. So I uninstalled the nvidia-glx package downloaded the .run file from the nvidia site, ran it and it worked. Then I forgot about it.

Fast forward a couple of months and I upgrade to Hardy without thinking about it. I reboot and I get a dialog box stating that it couldn't figure out the monitor. The Configure... button on that dialog box says it was using the nv drivers. It also let me choose a monitor for which I chose the generic 1680x1050 lcd monitor which is my monitor (A Sceptre 20" monitor). Clicked OK and came to the desktop.

Now at this point I thought I could switch to the nvidia-glx drivers from the Hardware Drivers dialog, but when I bring it up it doesn't list the nvidia drivers as any proprietary drivers that I can enable. I check synaptic and the nvidia-glx-new package is installed.

Although I chose the 1680x1050 generic monitor, 1680x1050 is not a choosable resolution from the screen resolution applet. So I want to switch to the nvidia-glx-new package's drivers (Plus I would like to play Enemy Territory again). I check the nvidia site's readme and it says that enabling the driver is simply a matter of running nvidia-xconfig.

My question is, is it really as simple as booting into the rescue/single user mode and running that command? Does anyone forsee anything blowing up in my face? Is there anything that I should check or enable beforehand?

---

### Post by Rocket2DMn on 2008-04-26
I would try uninstalling the existing drivers first:
```
sudo apt-get remove --purge nvidia-glx-new nvidia-glx
```
Then you can use the new version of Envy called EnvyNG to automatically install the restricted nvidia drivers from nvidia's website
```
sudo apt-get install envyng-gtk
```
If it doesn't run right away, you can access it from Application->System Tools->EnvyNG

---

### Post by duncan_m on 2008-10-17
> **Rocket2DMn said:**
> I would try uninstalling the existing drivers first:
```
sudo apt-get remove --purge nvidia-glx-new nvidia-glx
```
Then you can use the new version of Envy called EnvyNG to automatically install the restricted nvidia drivers from nvidia's website
```
sudo apt-get install envyng-gtk
```
If it doesn't run right away, you can access it from Application->System Tools->EnvyNG


Perfect answer, solved my issues too! Many thanks for taking the time to contribute..

Cheers, Duncan.

---

