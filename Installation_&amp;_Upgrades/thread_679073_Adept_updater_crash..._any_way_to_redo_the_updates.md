---
title: "Adept updater crash... any way to redo the updates?"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by Kleaefmiir on 2008-01-26
I just have installed Kubuntu 7.10
Adept Updater told me I had 129 updates to do, so be it, I click to download them all.

However, silly Adept Updater decided to crash during the downloading of the updates.
Then, it was not working... so I did "sudo dpkg --configure -a" and Adept Updater was able to launch again.
However, it told I only had 46 updates to do... what happened to the rest that was downloaded but not installed??
Is there a way to redownload them to make sure they were properly installed?

Thanks!

---

### Post by Pumalite on 2008-01-26
The others are probably already downloaded and installed, if you have a working apt-get.
Try:
sudo apt-get update
sudo apt-get upgrade

---

### Post by Kleaefmiir on 2008-01-26
Thanks! I'll know from now on! :D

IT seems they werent installed since it got them all again and installed them! :D
Yay for code lines!

I hope the adept-manager will get fixed...

---

