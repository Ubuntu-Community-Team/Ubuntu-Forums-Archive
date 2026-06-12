---
title: "Network  Live Image Installation Issue"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by jack56 on 2014-03-27
[COLOR=#000000][FONT=Verdana]I've even trying for weeks to install Ubuntu over the the network. I have been successful at setting up dhcp sever for my Ubuntu sever 10.04 and also I am able to get my clients to pxe boot and everything else is working fine except that after the installation there is no internet. I am having an issue where "iface eth0 inet dhcp" changes to "iface eth0 inet manual" no matter what image I use, I always get the same result why?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I read about it being a bug here [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+s...ty/+bug/388060]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/388060")[COLOR=#000000][FONT=Verdana] and here [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+s...er/+bug/946215]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/946215")

[COLOR=#000000][FONT=Verdana]I am not sure what to do is there a guide to fix this issue?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I want to add that no matter what Ubuntu image I use no matter if I use a Debian or Ubuntu server I always get the same result. I never have internet connection after installation. I don't know if I am skipping a step or not configuring a file or changing a script. I have used this tutorial:[/FONT][/COLOR]

[http://www.serenux.com/2010/05/howto...ubuntu-server/]("http://www.serenux.com/2010/05/howto-setup-your-own-pxe-boot-server-using-ubuntu-server/")
[http://www.serenux.com/2010/05/howto...-a-pxe-server/]("http://www.serenux.com/2010/05/howto-get-an-ubuntu-live-cd-to-boot-off-a-pxe-server/")
[http://www.serenux.com/2012/06/howto...e-environment/]("http://www.serenux.com/2012/06/howto-fix-networking-not-working-after-installing-ubuntu-desktop-from-a-pxe-booted-live-environment/")

[COLOR=#000000][FONT=Verdana]Like I said everything works fine except after the installation I never have internet connectivity. I dont know what I am missing, If someone can point me to what I am not doing or some step I might be skipping, I would gladly appreciate it. Is there a special way of installing a live image over the network, some special instructions that I am not aware of? I need help, any help would be appropriated. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Thank you[/FONT][/COLOR]

---

### Post by Iowan on 2014-03-27
Have you tried editing */etc/network/interfaces* and changing "manual" to "dhcp"? 
Is the DHCP server on a separate machine (hopefully)?

---

### Post by jack56 on 2014-03-27
Yes and by editing the interface after installation the internet works but I don't want to do that every time after every installation because others will be helping with installation and wouldn't want them messing around with root privileges and such. 

The dhcp server is installed on the server I use whether it be a Debian or Ubuntu server same result.

---

### Post by jack56 on 2014-03-27
Any ideas anyone? Should this thread be on a different section of the forum?

---

