---
title: "how do I upgeade to 10.10 from 8.04?"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Scubamom on 2010-11-22
I don't want to dual boot. I put Ubuntu 8.4 on my desk top and cannot get my cable modem to issue an IP address to the desk top. So I was told to upgrade to 10.10 and that may fix the problem. I ordered a new copy because the ones that others gave me did not work. Now I have the same problem because I don't know how to upgrade to the 10.10. The cd runs/opens but I don't know what to click to start the installation. Also will this installation solve the cable not giving IP address to desktop?
PG

---

### Post by gradinaruvasile on 2010-11-22
Well you should give more details about the cable nodem, what method do you use etc.

Basically you have to have a DHCP server running on the modem - most do by default.
Then you have to run a dhcp client on your box.
If i remember correctly, the default network manager settings is to have it enabled - whenever you plug a cable in, it automatically tries to acquire a network address via dhcp.

There is a potential problem 
- the Linux networking uses a file called /etc/network/interfaces (with full path) that has the settings of all network interfaces in it.
- network-manager is another layer of networking program that has the gui to configure connections. It has its own settings files and all, separate from the above mentioned Linux networking.
- network-manager is set to disregard any interfaces that are setup in the interfaces file - this is because in some cases may be interfaces that have fixed settings and the user does not want them to be managed by network-manager (the basic Linux networking is in fact more reliable, but you have to know some terminal commands to make them work right).
So, you will have a "device not managed" menu entry if you have any kind of set up in the interfaces file of a certain network interface (such as eth0, the main network interface for most people).

---

### Post by srikanthganta on 2011-01-15
> **Scubamom said:**
> I don't want to dual boot. I put Ubuntu 8.4 on my desk top and cannot get my cable modem to issue an IP address to the desk top. So I was told to upgrade to 10.10 and that may fix the problem. I ordered a new copy because the ones that others gave me did not work. Now I have the same problem because I don't know how to upgrade to the 10.10. The cd runs/opens but I don't know what to click to start the installation. Also will this installation solve the cable not giving IP address to desktop?
PG
Is there any way to Upgrade my **Ubuntu 8.04 - the Hardy Heron**   to the latest **Desktop edition 10.10**
Please give me good tutorials/videos/links to upgrade.

---

