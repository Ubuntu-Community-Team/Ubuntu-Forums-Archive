---
title: "Cannot even Start Install Lose Video After Kernel Load"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by phimuskapsi on 2008-02-06
So I have a very strange problem, I was able to install Ubuntu on an XP 64-bit machine with Vmware 6.0 Workstation. I decided to try and install it on it's own drive rather than thru a virtual machine and I burned the same ISO to a CD, reboot the computer get to the screen with all the options:

Start or Install ubuntu
Start Safe Mode
etc.
etc..

I select Start or Start in Safe Mode and the very SECOND the kernel load finishes my screen turns off. CD spins and such but no video, doesn't matter which monitor I use or whether it's DVI or VGA connected.
It does say something about PCI Device unable to allocate resource 0 on Device [0000:0000] at the top but it goes too fast.

Why would this work on a VM but not on the actual machine? I read that I should remove the last two flags on the install instructions and start in safe mode but where is the break between switches? Which two should I remove?? Thanks!

---

### Post by taurus on 2008-02-06
What video card and monitor do you have?  Another option is to use the alternate CD to install Ubuntu on your machine.

---

### Post by phimuskapsi on 2008-02-06
Can't believe I forgot all that stuff

MSI K8-Neo V Mainboard
ATI X800 XL AGP Card
AMD 64 X2 4200+ Dual-Core
1GB of Ram

Now I have a Gateway EV710 17" CRT and a Dell 17" LCD monitor, I have tried it with both monitors and it works fine. What do you mean by "Alternate CD"?

---

### Post by taurus on 2008-02-06
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/)

---

### Post by jan quark on 2008-02-06
alternate cd installs ubuntu in text mode 
here is a good installation guide

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

