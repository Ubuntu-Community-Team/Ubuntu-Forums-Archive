---
title: "Second Ubuntu breaks wifi"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by vikdak on 2011-07-16
I installed 11.04 on an Ideapad Z570 with a BCM4313 wireless card. Everything mostly managed to work, except the wifi. Plus the screen brightness does not seem to change. The wifi worked after I allowed the broadcom driver to be installed and I did

sudo rmmmod -v acer_wmi
sudo rfkill unblock all

I made it permanent by blacklisting acer_wmi in /etc/modprobe.d/blacklist.conf. 

Now, I have a Nvidia 520M Optimus graphics card, so I thought that I should try out bumblebee. Only I was scared that it would break the installation. So I decided to make another partition of 11.04. Unfortunately, it broke wifi on both partitions. I tried to do the same process on the other partition, but nothing. 

Finally I did sudo grub-install /dev/sda and sudo update-grub and then used gparted to remove the other natty install. 

I restarted the other install, and it was still broken. So I removed the drivers, removed the blacklist statements, restarted, did the whole thing again, and remarkably it went back to normal. 

I am listing all the process so that if somebody else actually encounters it, hopefully this process will be an indicator, but my question is why is it happening? Because I still want to make a separate partition and try bumblebee.

---

