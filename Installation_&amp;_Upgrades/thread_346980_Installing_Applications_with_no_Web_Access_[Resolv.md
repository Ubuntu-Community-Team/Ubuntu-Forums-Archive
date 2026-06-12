---
title: "Installing Applications with no Web Access [Resolved]"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by baloo56 on 2007-01-26
I have been using ubuntu 6.06 at home now, as my primary O/S, for 6 months with no problems this forum couldn't help me fix (thank you all). I started to use Ubuntu 6.06 at work recently on a development box and the install was flawless. A few tweaks here and there with the addition of a FAT32 partition and all was well. However, I wanted to burn a DVD with k3b but k3b was not installed by default. I do not have Internet access to my dev. box at work and can not get it. So I tried to install k3b using Synaptic and selecting add CD (Ubuntu 6.06) but it appears that k3b is not on the DVD. 
What is the best way to install applications & updates to a Ubuntu box that has no Internet connection and insure that all "dependencies" are taken care of?

---

### Post by aysiu on 2007-01-26
The best way is to boot a live CD on the computer that *does* have internet access, "install" K3B there, copy all the files from /var/cache/apt/archives in that live session to a USB key, copy them from the USB key to the desktop of your Ubuntu installation, and then type this code in the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` By the way, Nautilus doesn't burn DVDs?

---

### Post by baloo56 on 2007-01-29
Thank You Aysiu.....I had a chance to try your recommendation Re: loading programs with no web access and it worked just fine.

---

