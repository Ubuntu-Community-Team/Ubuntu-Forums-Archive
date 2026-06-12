---
title: "Wireless adapter issues"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Craige4107 on 2008-10-28
I recently installed 8.04 on a Toshiba Satellite Laptop.  I am dual booting with Vista 32.  I have an AMD Turion 64 processor.  My wireless network card is a Realtek RTL8187B.  Ubuntu hardwires without issue.  My NIC is a Realtek as well.  When I check in the Network Manager, no wireless network is detected.  When I try to install manually, I get a beep when I try to enter the ESSID, and it will not accept any keyboard strokes.  The information regarding wireless networking is daunting.  I have tried a few commands, usually met with, "Command not found".  I am not a programmer, but I am far from a novice either.  Networking is my weak point however.  My question, what is the "typically" issue with wireless networks when Ubuntu is installed initially.  Any help would be much appreciated.

1shw -C network
1spci
ndiswrapper -1

Just some of the commands that came back with "Command not found".

1wlist scan:  Unable to scan, if I remember correctly

Thanks again.

---

### Post by pytheas22 on 2008-10-28
Many wireless cards 'just work' in Ubuntu out-of-the-box because the drivers are built into the kernel, but those that don't usually require manual installation of drivers.  Please post the output of the following commands so that we can figure out what you need to do:

```
lsusb
lshw -C Network
uname -m
ndiswrapper -l
```

(Note that those are lowercase L's, not the number one, as you were typing before to generate the 'command not found' errors...a common mistake :))

---

