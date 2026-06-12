---
title: "Wireless"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by jan00b on 2007-07-27
Hello, My friend  just installed Ubuntu 7.01 on my computer with an AMD Athlon64 3200+ processor for me and got me internet without downloading any special drivers but using a Manuel Install for wireless, so i know all my hardware is compatible. I reinstalled Ubuntu and it was going swell at first. I tried to get myself wireless but it won't work for some reason. Ok so i understand the feilds that must be filled in for my internet to work

ESSID:
Key Type:
Network Password:
Connection Type:

when I go to my Dlink DI-524 router here are the feilds i see.

SSID: default
Key 
Password: 7i88y (the password prompted after typing the routers gateway IP in browser)
WEP Encryption: 64bit
Key Type: Hex
 Authentication: Shared Key
Key1: 0123456789 (The only key i use to connect wireless windows computers)
DHCP Server: Enabled

With this knowlage I go click on the upper right hand black moiter icon. Now i choose manel Connection, Wireless then make the previous feilds

ESSID:  default
Key Type: WEP 64/128bit
Network Password: 7i88y
Connection Type: DHCP

I saved, closed out then started firefox. I can't load any sites with it. Weird thing is, In Ubuntu it says default is at 87% (i assume this is signal strength) and my router says "linux-desktop" is connected but i  still can't use firefox to brows the web, what does that mean?

Now I put the connection on roaming modejust so i can edit some other stuff.

Now I try "Connect To New Network". I put in default as my network name, choose 64/128bit WEP and finaly 0123456789 as my key with a Shared Key enebled

What am i doing wrong?, how do i get this to work? My friend did it in 30 seconds, how hard cold it be?

---

### Post by moore.bryan on 2007-07-27
> **jan00b said:**
> Hello, My friend  just installed Ubuntu 7.01 on my computer with an AMD Athlon64 3200+ processor for me and got me internet without downloading any special drivers but using a Manuel Install for wireless, so i know all my hardware is compatible. I reinstalled Ubuntu and it was going swell at first. I tried to get myself wireless but it won't work for some reason. Ok so i understand the feilds that must be filled in for my internet to work

ESSID:
Key Type:
Network Password:
Connection Type:

when I go to my Dlink DI-524 router here are the feilds i see.

SSID: default
Key 
Password: 7i88y (the password prompted after typing the routers gateway IP in browser)
WEP Encryption: 64bit
Key Type: Hex
 Authentication: Shared Key
Key1: 0123456789 (The only key i use to connect wireless windows computers)
DHCP Server: Enabled

With this knowlage I go click on the upper right hand black moiter icon. Now i choose manel Connection, Wireless then make the previous feilds

ESSID:  default
Key Type: WEP 64/128bit
Network Password: 7i88y
Connection Type: DHCP

*try changing the network password from 7i88y to 0123456789*

---

