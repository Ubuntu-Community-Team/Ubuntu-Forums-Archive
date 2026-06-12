---
title: "PCMCIA wlan only works when inserted after booting"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by doyenne on 2005-11-23
When I put my Belkin wireless lan pcmcia card into my laptop and then turn it on, the following happens:
[LIST]
[*]GRUB loads
[*]Ubuntu loads
[*]Login screen appears
[*]I can login with username and password
[*]Ubuntu hangs!!
[/LIST]
At this moment, I have to remove the pcmcia card. Immediately after that, Ubuntu continues, I hear the startup sound, and the desktop appears on the screen. After that, I have to do the following to bring my wlan up:
[LIST]
[*]Insert the pcmcia card (lights remain off)
[*]Start a terminal
[*]type: modprobe ndiswrapper (one light on)
[*]go to network configuration, select wlan0, click on activate
[/LIST]
Now the network is running nicely.

Of course, it would be preferable if I could insert the pcmcia card before booting, without having to perform all the above described steps!

I don't know what to do. Perhaps it has sth to do with /etc/modules? The contents now are:

lp
mousedev
psmouse
(lines starting with # skipped)

Many thanks for any help!

---

### Post by doyenne on 2005-11-24
I changed the following:```
sudo echo ndiswrapper >> /etc/modules
```Now I can boot with the wlan pcmcia card inserted, the network comes up during the boot process, the time is correctly synchronised via the internet, the login screen appears, I can login, but then... Ubuntu hangs!!!

I don't know where to look now. Should I consult some system log files for example? Who can give me a hint in what direction I should look?

---

### Post by towsonu2003 on 2005-12-04
no idea what's wrong but, just to give some pointers... first, if you wanna undo the change made by ```
sudo echo ndiswrapper >> /etc/modules
``` just comment line ndiswrapper with an # in file /etc/modules. 

possible logs to look would be ```
dmesg
``` and /var/log/messages for errors... I would post their output here and I would also file this as a bug with ubuntu.

---

