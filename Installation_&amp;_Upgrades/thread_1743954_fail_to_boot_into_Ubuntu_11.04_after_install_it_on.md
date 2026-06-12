---
title: "fail to boot into Ubuntu 11.04 after install it on windows 7"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by higherzl on 2011-04-29
Hi, everybody. I've got some trouble, and I hope somebody could help me out.

Here is the trouble: After I successfully installed Ubuntu 11.04 from LiveCD, I failed to boot into it. Everytime I restarted my PC, it directly boot into my windows 7 as usual.

My partition as follows:
sda1: SYSTEM_DRV (windows 7 reserved)
sda2: WIN7_OS
sda3: linux_swap, 2G
sda4: root of Ubuntu, EXT4
I'm really new to Ubuntu, and this is really my first time installing Ubuntu. One thing I'm not sure was that when I installed Ubuntu, there's a menu asking "Device for boot loader", and I chose my disk0 which is sda, rather than sda1(SYSTEM_DRV of windows 7) or sda2(OS of windows 7). Should I have chosen sda1?

Is there any way I can quickly fix it, such as fix grub2 or something?

I then tried to install it again and choose sda1 this time, but still fail to boot into Ubuntu.
What's wrong? I think I should be fine because most people do install this way and their systems do work well.

Problem solved. I followed the rules of "select the root partition as the **"Device for boot loader installation"**" from this article 
[http://www.terabyteunlimited.com/kb/article.php?id=279]("http://www.ubuntuland.com/where-should-i-install-the-ubuntu-bootloader-on-my-netbook/")

---

