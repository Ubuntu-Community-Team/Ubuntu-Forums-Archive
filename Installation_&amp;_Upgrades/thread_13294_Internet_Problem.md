---
title: "Internet Problem"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by rigo on 2005-01-30
Hi,

Yestesday I have been installed Ubuntu . I configured my adsl account and ia have made some update with synapotic from de ubuntu.org repositories. Everything was ok. Today i 've boot my ubuntu box and i have problems because i don't have internet connection, frist i thing that was a DNS problem but if a try to ping to an IP directly does not work instead. Is anybody here with the same problem??. I does not  change any network config before shot dow my sistem yesterday ...

---

### Post by rudi on 2005-01-30
hi rigo, could you please post the exact error you've encountered?

---

### Post by rigo on 2005-01-30
Hi,

The problem was as follow:

1.- I've installed and run ubuntu box, i've update some packages (update firefox, uninstal openoffice )via synaptic from ubuntu's apt-source via Internet. (adsl conecction configured with pppoeconf with no problems). When i finished i shut down  the machine

2.- Next day i've  boot my sistem and try to surf the web and the broswer don't find the hosts. The i try to test my dns with "nslookup" i have error, The i try to ping the 200.1.123.7, 200.27.168.254, 200.1.123.4 IP and i got the "Network unreachable "  error". I didn't change my dsl config or routing table.

---

### Post by rudi on 2005-01-31
is your adsl adapter still recognized, installed by the system? try to run **lsmod **and look for a (cryptic) description of your adapter. Also, when you're system boots, you'll see a lot of [ok] , follow the messages to see if there're something not right there (especially the network configuration).
 
 You can also see if the kernel still recognizes your adapter, run the command **dmesg** and search for your adapter/ network related messages.

---

