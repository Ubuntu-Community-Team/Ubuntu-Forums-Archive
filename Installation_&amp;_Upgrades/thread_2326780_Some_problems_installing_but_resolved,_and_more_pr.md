---
title: "Some problems installing but resolved, and more problems afterwards"
date: 2016-06-04
forum: Installation &amp; Upgrades
---

### Post by Dsoslglece on 2016-06-04
Hi,
Wanting to install Kubuntu (to replace Vista) on a friend's laptop (hp Compaq 6715s), was very hard, but finally, I managed to only install Kubuntu 14.04, but without update (it refuses then to restart), and after having tried Kubuntu 13, 15, 14.10, 16.04, 16.10, Ubuntu 14, 16, Xubuntu, Lubuntu!!... #-o
But finally, Kubuntu.14 worked as a charm as it was. BTW, I'm using it just now to write this post

But now, starts the real fun!
From time to time, no sound!
I'd verified everything under the sun with no result; and suddenly, and without having done anything special, sound again! 
Finally I first thought it may be a faulty sound board, but then, I thought that it may also be caused by a faulty sound board driver.
So, looking for a solution, I found the proper commands for it;
 
1. purge remove to de-install the Linux sound board base, alsa base and alsa utils.
2. install again the same elements

It seemed to have worked well, and for one and an half day it was 100%.
But then, yesterday, no sound again... restarted, looked everything again, nope!
So, I did de-install and re-install the card driver, and it was OK for a while, and then again no sound...
Maybe I should compile this driver from scratch, but not quite sure of how to do : I am working generally on OSX, and even if I've also installed kubuntu and ubuntu on my mac, I'm not as used to work on Terminal than my cousins from Linux :)

Would someone have some suggestions? any?

Thanks in advance

Dsoslglece

---

