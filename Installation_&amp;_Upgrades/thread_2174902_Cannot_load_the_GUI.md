---
title: "Cannot load the GUI"
date: 2013-09-16
forum: Installation &amp; Upgrades
---

### Post by vincent8 on 2013-09-16
Hi everyone,

I've installed ubuntu on my new Toshiba Satellite CD40(Processor: AMD A4-500 Graphics chipset: AMD Radeon 8330). I've installed the Ubuntu 13.04 desktop amd64 version(with a USB key). I've partiotionned the Hard Drive myself because in the installation process Ubuntu wouldn't detect windows 8, and I wanted to dual boot. My problem is that I can't access the GUI, I'm always stuck in the command line interface. I've tried to restart lightdm but then I just got a black screen. I've also tried to type ''startx'' but I got a error message that said ''No screens found''. I've tried to configure Xorg but that didn't work neither. I've tried to launch ubuntu in a try session, but I got the same command line interface. 

I guess it might be related to some graphics chipset drivers issue, but I'm not sure.

Could anyone help me?



Vincent


PS1: This is the first time I've installed linux on one of my computer so I'm not really used with it.

---

### Post by debodas on 2013-09-16
I don't use AMD graphics personally, so can't confirm whether these work or not, but [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) has installation instructions for the AMD graphics driver.

---

### Post by vincent8 on 2013-09-17
Thanks a lot for your reply. In fact, I only had to create a Xorg file in the right folder.

---

