---
title: "Pulling what little hair I have out!!!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Richardljohnson on 2009-12-30
I convinced my boss to hold out for 9.10 but I have multiple issues that I can not get by even with 2 weeks of searching and 'playing'. 

1. Display size will only go up to 800x600 (I need a min of 1024 and 1280 would be great).

DETAIL: I am going through an older ROSE KVM Switch so detections is not possible of the ASUS monitor. I ran X -configure and took this file and put it in as /etc/X11/xorg.conf. This worked for a little while (about 10 reboots)and then it got to where another problem came up. 

2. Auto login was set with a 15 second delay. This worked for a while then when auto login it would fail. It looked like when X tried to start. I finally got in as root about about 10 more manual login tries(another issue is failsafe would not work). I then deleted xorg.conf and then restarted and auto login would work.

3. I have 3 nic's in the system but the 2nd and 3rd would not be found so I did a manual configuration buy adding the info to the /etc/network/interfaces file(different network) But while this showed to be up from the system it was refusing all inbound communication...

I can actually live with the nic issue but the display and the autologin problem are a royal pain....any suggestions:confused:

---

### Post by dstew on 2009-12-30
Did you try plugging in the monitor directly, bypassing the KVM switch, and then trying to get the monitor detected?

I don't have any suggestions for your multiple NIC issue, sorry.

---

