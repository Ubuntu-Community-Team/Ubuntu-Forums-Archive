---
title: "Wireless in not working, help please!"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by elperrillo on 2008-04-10
Hi, I'll try to make it plain and simple so everybody can understand.

I installed UBUNTU on my Acer TravelMate 2413LCi and I have not bee able to get it to work, Ubuntu seems to recognize the card, here is what **iwconfig** tells me:

[B]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

The signal meter does not report any signal at all, I even installed GTKwifi and all I get when I run it using **"gtkwifi run-in-window"** is a tiny window with a signal meter and no signal.

Can anybody help?

---

### Post by Pumalite on 2008-04-10
This might help:
[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by elperrillo on 2008-04-10
I am very new to Ubuntu and I did the following command to install the driver from the web..

sudo apt-get install b43-fwcutter

However it gives me the following message...

Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter

What can I do? I read something about getting the right repositories, but I've tried to update all the repositories that I've been able to find but it is still giving me that message.

Can anybody help?

---

### Post by Pumalite on 2008-04-10
Read this:
[http://ubuntuforums.org/showthread.php?t=709259](http://ubuntuforums.org/showthread.php?t=709259)
Check # 10

---

### Post by elperrillo on 2008-04-10
Hi thanks for your help however I've tried that command a thousand times.. when I do...

[B]
sudo apt-get install b43-fwcutter [/B]

I get:

**E: Couldn't find package b43-fwcutter**

Why?

---

### Post by Pumalite on 2008-04-10
It's in Synaptic in 8.04 Beta

---

### Post by elperrillo on 2008-04-10
Thank you, I am upgrading from Gutsy to Hardy now.

---

### Post by Pumalite on 2008-04-10
Good luck.

---

