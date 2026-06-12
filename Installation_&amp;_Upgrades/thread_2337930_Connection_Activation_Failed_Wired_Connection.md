---
title: "Connection Activation Failed Wired Connection"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by billwagner3 on 2016-09-22
Hi Guys,

I am new to Linux and have just installed the latest version of Ubuntu. For some reason, I am having this issue with internet connection:

I am wired, and when I log in to Ubuntu it says I have a connection, but when I go to browse with Firefox or Ubuntu Web Browser, it says "Network Error". When I go to click on the network arrows in the top right of the screen and click on Wired Connection 1, it comes up with "Connection activation failed (2)Active connection removed before it was initialized, but then it says it established connection again in upper right of the screen, but there is still no accessibility to the internet. I've made sure I have the right settings to connect to my router, but to no avail. 

If someone could advise me on debugging this, it'd be great. 

I am running a machine that also has two version of Windows on it: 7 and XP. 7 and XP are running fine. 

I use Grub2 for Boot Menu. 

Thanks guys,

Bill

---

### Post by billwagner3 on 2016-09-22
Here's some more data on what I have tried so far:

1. tried--  ifconfig eth0 192.168.0.15 netmask 255.255.255.0
SIOCSIFADOR: No such device
SIOCSIFNETMASK: No such device

2. tried-- route add default gw 192.168.0.1
SIOCADDRT: Network is unreachable.

---

### Post by billwagner3 on 2016-09-23
I revolved this by running apt-get remove --purge resolveconf then
apt-get install --reinstall resolvconf

I rebooted and now I'm connected.

---

### Post by trrrmmer on 2016-09-29
> **billwagner3 said:**
> I revolved this by running apt-get remove --purge resolveconf then
apt-get install --reinstall resolvconf

I rebooted and now I'm connected.


Thank you very much for that instruction. :(
I've lost my internet connection now despite being connected to the wlan.

I even reinstalled resolvconf from other sources but that didn't help.

Could anyone tell me how to fix that issue?
Thank you,
trrrmmer

---

