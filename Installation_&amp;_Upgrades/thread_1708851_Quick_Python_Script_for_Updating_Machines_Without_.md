---
title: "Quick Python Script for Updating Machines Without Internet"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by Yujingtao on 2011-03-17
I've been having some problems trying to get a new netbook working with China Telecom's 3G service (works wonderfully in Windows, but still trying to figure Ubuntu out), so until I figure out the problem with this Huawei modem, I've written a quick python script to handle updates/installations on the Ubuntu side. (Synaptic does fine on generating download scripts for packages, but it needs an option to handle updates as well) 

If anyone else has a use for this, you're welcome to use it. Please let me know what needs to be changed to make it work on your box.

---

### Post by ChipOManiac on 2011-03-17
Nice Job! :D

---

### Post by Yujingtao on 2011-03-27
Thanks for the compliment! I try to do the best that I can to give back to the community. I actually don't need this script anymore now that I have gotten my 3G dongle to work, but I have made an updated version available for prosperity in case anyone else gets stuck in the same situation.

For those of you using China Telecom's 3G service, don't bother using the included software on the modem. It's very nice looking, but it fails miserably to setup DNS properly. Instead, use wvdial with

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem = /dev/ttyUSB0
Modem Type = USB Modem
Baud = 460800
ISDN = 0
Phone = #777
New PPPD = yes
Stupid Mode = yes
Username = [email]ctnet@mycdma.cn[/email]
Password = vnet.mobi

in /etc/wvdial.conf after you add yourself to the dip group, and all is well. I'm working on a script to automatically update connection time, sent bytes, and received bytes so that you'll know at a glance what you have used for the month since we have a 100 hours per month limit here.

For interested parties, the 3G CDMA modem with 

Bus 002 Device 036: ID 12d1:140c Huawei Technologies Co., Ltd.

works wonderfully in Linux.

Hope this helps someone out!

---

