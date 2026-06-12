---
title: "Win 7 freezing after installing ubuntu 12.04 LTS as dual boot system"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by irfan5 on 2013-08-29
hello , this is my first post

Here's what I did exactly in detail

I have win 7 on a SSD and a secondary drive. Second drive (1TB) had three partitions. I emptied the last partition and installed ubuntu on it. Before install, I deleted this partition by GParted using liveCD and later during install I made partitions root, swap and home (there were some tutorials on how to do that on youtube) and everythign went well.
Then i modified boot menu using easyBCD from within win7. and almost everything works ok with few problems i see now

win7 freezes intermittantly for few seconds randomly, this had never happened before I did install ubuntu. So there must be something related to this. Either hard drive. Should i have used a dedicated third hdd for linux install?

Another thing is my graphics card. The default drives in ubuntu looked perfect and gave good resolution on my PC (1920xsomething i dont remember atm). But there was option of have additional proprietry drivers, so I installed Nvidia drivers, and boom everything breaks up. The screen resolution went down to 800x600 and fonts started looking blurry. And when I revert back to xorg drivers, ubuntu wont boot anymore to UI. So I installed it again second time from scratch, and now its running on default drivers. This looks bit funny to me, that default xorg drivers looked fine but the propriety drivers dont work.

Any observations why this freezing is occuring in windows (not occuring in ubuntu) would be nice. and any suggestions to solve this problem. This is my first time installing solid ubuntu on physical hdd, I have used it prior in vmware and I liked it.

my system is

Core i7 2600K (im not overclocking)
Nvidia 560Ti graphic card
16 GB RAM
120 GB SSD +1TB HDD (IDE mode, simply installed win7 on SSD)

Thanks in advance for any help.
kind regards

---

