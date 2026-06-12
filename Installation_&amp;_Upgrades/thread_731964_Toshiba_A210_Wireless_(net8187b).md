---
title: "Toshiba A210 Wireless (net8187b)"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by damphoud on 2008-03-22
Hello, having a hard time with toshiba wireless :( ... I've installed ndiswrapper with out any problems/errors, drive net8187b, but i can't find any wireless networks. I have been able to find them, maybe once or twice, but even then, when I went to enter in my WEP passphrase, it wouldn't connect.


```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

$ ndiswrapper -l
net8187b : driver installed
        device (0BDA:8197) present

```

```

$ lspci
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```

thanks!

---

### Post by damphoud on 2008-03-22
sorry, moved thread to network & wireless. thanks

---

### Post by Skerit on 2008-06-15
I'm having the same problem with my Toshiba L350-107, which has the same wifi card. I actually do get to see my network ... if I'm sitting on top of my router!

Does anyone have any ideas?

---

### Post by quanta4135 on 2008-06-19
Bump. I'm also having the same problems with my A210.

---

