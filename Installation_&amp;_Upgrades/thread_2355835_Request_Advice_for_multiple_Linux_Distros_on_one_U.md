---
title: "Request Advice for multiple Linux Distros on one USB Drive"
date: 2017-03-17
forum: Installation &amp; Upgrades
---

### Post by paul258 on 2017-03-17
I have a (16 GB) USB Drive with Ubuntu installed on it. Can I install another distro on that same USB Drive or do I have to format the USB and then install 2 or 3 distros on that USB drive and when I boot into it how can I choose which distro that I want to use?   Thank You all in advance.

---

### Post by Bucky Ball on 2017-03-17
My first question would be how are you going to squeeze two or three *buntus on a 16Gb stick? You will have about 14Gb to play with. Add a 2Gb /swap partition and that gives you 12Gb. You might get two on there, but three? Doubtful unless they are very lightweight, slim installs (and definitely not Ubuntu but Lubuntu or Xubuntu or, top choice, the Ubuntu minimal install with next to no software installed).

To your original question. With a blank USB, you would install to the USB using 'Something Else' and create partitions just big enough to hold the installs. During the first install, create a /swap partition. That only need be 2Gb. All other installs can use that same /swap so no need to create one for each install.

In your current situation with Ubuntu installed on a USB already, you will either need to boot to Gparted from a live session on another USB or on a hard drive install and shrink the current Ubuntu partitions to leave free space for your next install(s).

Hope that gets you some of the way there.

---

### Post by paul258 on 2017-03-17
[Bucky Ball]("https://ubuntuforums.org/member.php?u=504316") , I am new to Linux and do not know much. I appreciate any and all help given. Thank You
[Bucky Ball]("https://ubuntuforums.org/member.php?u=504316")

---

