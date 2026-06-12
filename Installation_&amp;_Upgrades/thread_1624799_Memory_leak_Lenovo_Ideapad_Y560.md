---
title: "Memory leak Lenovo Ideapad Y560"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by mikeperrycanada on 2010-11-18
I installed Ubuntu 10.4 and everything works great "out of the box"! I didn't install any drivers.
Only one problem, a major one...
When I type "top" right after a reboot, around 1GB of RAM is in use. After a few min it grows to 2GB, even 2.5GB for no reason. Luckily, my machine has 6GB of RAM but it's still a major issue for me. 

I read on another forum another user with the same problem on the same Lenovo machine and he solved it by installing the newest driver for his ATI device. I don't have ATI, but I have the impression that I can solve my problem the same way. Do you have any idea what driver my cause that? I checked the Intel site for a new Intel HD graphics driver but they don't have ones for Linux. Is there a good software that can help?

Thanks!
Mike 

Here you can see my laptop specs [http://www.cdwg.com/shop/products/de...px?EDC=2180810](http://www.cdwg.com/shop/products/de...px?EDC=2180810)

---

### Post by dino99 on 2010-11-18
so you are either using the 64 or pae kernel. Mainly ubuntu (linux) load into memory a larger number of packages if it find a large amount of ram.
But you might watch logs to know about problems

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a

---

### Post by mikeperrycanada on 2010-11-18
> **dino99 said:**
> so you are either using the 64 or pae kernel. Mainly ubuntu (linux) load into memory a larger number of packages if it find a large amount of ram.
But you might watch logs to know about problems

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a

Yes, I'm using Ubuntu 10.4 64bit. Could you please explain a bit what these 3 commands do? thanks!

---

