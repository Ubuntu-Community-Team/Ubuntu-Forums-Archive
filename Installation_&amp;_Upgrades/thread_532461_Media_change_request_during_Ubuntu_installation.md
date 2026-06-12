---
title: "Media change request during Ubuntu installation"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by martin.klvana on 2007-08-22
Hello,

I posted this message first to the Hardware & Laptops forum, maybe Installation & Updates forum is better suited for my problem:

I have Fujitsu-Siemens AmiloPro V2030 notebook with VIA P4M800Pro motherboard and VIA/S3G Unichrome Pro IGP.

I tried to install Fedora 7 (which I am using on my desktop PC) but failed to set higher than making-me-dizzy 800x600 screen resolution. So I decided to try Ubuntu but I encounter troubles to install the system (ubuntu-7.04-alternate) though I was able to boot live-cd.

During "select and install software" section of the installation of Ubuntu, after about 85 percent is completed, the following notification appears on the screen:

Media change: please insert the disc labeled 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (2007041' in the drive '/cdrom/' and press enter

I do not understand why it requests anything. I verified the installation disc by MD5sum and it is OK. Besides I cannot eject CD drive. I googled the message and found that it sometimes happen as post-installation problem and can be easily solved by editing /etc/apt/sources.lst but what about if that problem occurs already during the installation process which is my case.

When the message appears I do not know any way to abort the installation so I simply wait for the battery getting empty. Is there another way to abort the installation at that point?

What kind of software is being installed around 85percent of completition? Is the software installation somehow optional - I did not see an option to select which software to install and which not. Perhaps if it is possible to get ubuntu running in a minimum mode then I can install rest of the software afterwards(?)

martin

---

### Post by Pumalite on 2007-08-22
Try this: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by martin.klvana on 2007-08-22
Thank you.

---

### Post by Pumalite on 2007-08-22
You are welcome. Glad it worked for you.

---

