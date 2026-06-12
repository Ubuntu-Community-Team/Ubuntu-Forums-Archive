---
title: "Network Manager not detecting Wireles in Ocelot"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by BalaViknesh on 2011-10-14
After the update to Ubuntu 11.10, i just lost my Wi-Fi connection. 
 
While loading Ubuntu it says "Waiting for network configuration" followed by "Waiting 60 seconds for network configuration". 

After this the login screen comes and after logging in except network manager everything works fine. 

Am using Lenovo Laptop on which Ubuntu 11.04 worked really well. 

Note: When i Switch on Wireless, only Bluetooth gets enabled. 

Somebody help me out here.

---

### Post by highlander2 on 2011-10-15
I've had the same problem. When an Ethernet cable was connected to my notebook, everything was OK, but after I  unplugged the cable and re-booted then I got the same message.
To fix it I edited my /etc/network/interfaces and changed it to

auto lo
iface lo inet loopback

After that I don't see the message anymore.

---

### Post by varunendra on 2011-10-17
Please open a terminal, enter the following commands and post their outputs:
```
sudo lshw -C network
lsmod
ifconfig -a
iwconfig
rfkill list all
```

Also, considering how highlander2 solved his problem, contents of /etc/network/interfaces.

---

