---
title: "Video Goes Out During Install"
date: 2013-12-30
forum: Installation &amp; Upgrades
---

### Post by borgward on 2013-12-30
I tried installing Ubuntu on Cyberpower Model No. P50CA1. AMD 64 dual core CPU. ATI video. I could boot from optical drive. Ubuntu would appear briefly, and then the screen would go blank. Could hear the optical drive churning for a while. I finally put the HDD in another laptop and installed Ubuntu. Ran the other laptop. No Problems. 

I then took that HDD and put it back in the Compaq. It would boot and I would have video briefly. The screen would go blank and the HDD would churn for a while. I suspect that Ubuntu has a problem running the ATI video. Is there a Ubuntu version or another distro that will run ATI video?

---

### Post by dsc1596 on 2013-12-30
First of all, what version of Ubuntu are you installing? Also, try going into a tty (ctrl+alt+F1)if so, you can try to install a proprietary driver from there. Sometimes even with a black screen you can access a command prompt.

---

### Post by borgward on 2013-12-30
Linux Mint 16 Cinnamon 64 bit. Might consider Ubuntu 10.04, but nothing newer. Tried later Ubuntu with the retro desktop, but still did not like the experience.

So are there problems running with ATI video? is the AMD Dual Core 64 a problem? I really likeed the AMD Athlon processors in my old 32 bit machines. Much better than P4, but Intel turned the tables with their 64 bit Dual cores.

---

### Post by dsc1596 on 2013-12-30
oh, I see. I'm not as familiar with Linux Mint I'm afraid. There shouldn't be problems necessarily with ATI video in general, but perhaps the card is no longer supported out of the box with the default driver. I'll have to install a VM and try it out. My experience with Linux is mostly based on Ubuntu and Kubuntu.

---

### Post by dsc1596 on 2013-12-30
What model video card do you have exactly? After trying out Linux Mint on a VM, and doing some searching, I found [this site]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide") that may help with your video issue. They give a nice walkthrough of how to install proprietary AMD drivers on Saucy (which is what Petra is based on) From my own experience, it could also be the kernel that you are using with that version of Linux Mint. If according to that website your card is still supported try to install the amd driver, and if it still doesn't work, you may try updating the kernel to 3.12 using the walkthrough [here.]("http://ubuntuhandbook.org/index.php/2013/11/linux-kernel-3-12-released-install-ubuntu-or-linux-mint/") The AMD driver may work better with the newer kernel.

---

