---
title: "Need help installing oneiric-proposed kernel"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2011-10-21
I am subscribed to bug 872711:
"Kernel does not report some USB printers correctly, making them not being detected by CUPS", and I received an E-mail from Launchpad:
> This bug is awaiting verification that the kernel for Oneiric in
> -proposed solves the problem. Please test the kernel and update 
> this bug with the results. 
It goes on to reference this page for instructions on how to install the proposed package:
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)
I checked that my sources included oneiric-proposed, and proceeded to create a file /etc/apt/preferences as indicated (but with "natty" replaced with "oneiric"). Then I went to the next step:
sudo aptitude -t oneiric-proposed
I hit 'u' to update, but when I looked at "Upgradable Packages (1)", and hit enter, the only thing there was: net, main, and then google-chrome-beta. So I obviously did something wrong. I thought I was going to find this proposed kernel. Could someone help me out?
Thanks.
-- David

---

