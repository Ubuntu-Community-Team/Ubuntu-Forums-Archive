---
title: "No internet access after upgrade, even wired connection not working"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Rul on 2012-05-17
I have just upgraded from 11.04 to 11.10, and I can't connect to the internet. Not only wireless is not working, if I connect the computer to the modem I still get no internet access. It was working fine before the upgrade, and it's still working fine in the Windows partition.

I don't know what to do to solve this, please help.

---

### Post by darkod on 2012-05-17
If it's only a modem, not a router, you might need to create a dial connection for it to work.

Do you have a dial up connection configured in windows?

---

### Post by Rul on 2012-05-19
No, I don't need dial up conection to conect in windows. Before upgrading I didn't need it neither in Ubuntu, I would just conect the cable to get internet

---

### Post by hansdown on 2012-05-20
Hi, Rul.

Can you right click the internet icon, and set it up there?

---

### Post by Rul on 2012-05-20
Nop, it says that the cable is unpluged even when it is conected. Also all the wireless options are greyed out in the network manager

---

### Post by sikander3786 on 2012-05-20
Please post the outputs of these commands:

```
cat /etc/udev/rules.d/70-persistent-net.rules 
ifconfig
cat /etc/network/interfaces
```

While replying, press the # icon in post menu to generate [code] tags and paste the outputs between those tags.

---

### Post by Rul on 2012-05-30
Here is the output that I got
```

tanya@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.

# See udev(7) for syntax.

#
# Entries are automatically added by the 75-persistent-net-generator.rules

# file; however you are also free to add your own entries.


# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="88:ae:1d:07:31:55", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4357 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:e4:00:f1:8e:ba", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

tanya@ubuntu:~$ ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12194 (12.1 KB)  TX bytes:12194 (12.1 KB)


tanya@ubuntu:~$ cat /etc/network/interfaces

auto lo
iface lo inet loopback


tanya@ubuntu:~$ 



```

---

### Post by raja.genupula on 2012-05-30
its not detected here too ,
post the output of ```
lspci
```

---

