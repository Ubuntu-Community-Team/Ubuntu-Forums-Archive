---
title: "Installing 2 Linux distros on external HDD, how?"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by DJRWolf on 2010-02-06
I took my brother-in-law's old non working laptop and removed the 60GB HDD from it and put it in an external enclosure. I was wondering if I could connect it to the computer
(before powering on) and install Ubuntu and Fedora onto it. The reason for those two flavors are I want to try Ubuntu and a class I'm going to take in the summer about Linux uses Fedora. I've had very little experience wit Linux so any tips, hints, or advice?

---

### Post by darkod on 2010-02-06
It should be fine. Just make a plan in advance how you want to split the disk (50-50 or what ever) instead of installing ubuntu on whole disk and then shrinking to make space for fedora.
Another important thing is: you don't need the bootloader from both of them. I would install ubuntu and its grub2 bootloader. Then check it's working fine. Then install fedora and before starting the install there should be Advanced options somewhere, tell it not to install a bootloader.
After that the computer will boot ubuntu directly. Open terminal and do:

sudo update-grub

it should detect the fedora install and create entry in the grub menu automatically for you.

---

