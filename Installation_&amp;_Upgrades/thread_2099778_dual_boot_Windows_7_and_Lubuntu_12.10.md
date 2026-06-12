---
title: "dual boot Windows 7 and Lubuntu 12.10"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by Old-un on 2012-12-30
Have successfully managed to dual boot Windows 7 and Lubuntu 12.10 and while everything in windows works great. The only problem i have encountered when booting into Lubuntu is that i cannot get online. Could someone help me please. Thanks

---

### Post by gnush on 2012-12-30
Try to include as much relevant information as possible.

What have you tried so far? What kind of connection are you using (wireless, wired, mobile, etc.)?

---

### Post by Old-un on 2012-12-30
Hi gnush

I am in the process of trying to locate the networkmanager in lubuntu in the hope that i may be able to sort out the problem from there? I am using a wireless connection.

---

### Post by ajgreeny on 2012-12-30
What machine  and what wireless adaptor?  If you don't know, let's see the output from terminal of command ```
lspci
```

---

### Post by Old-un on 2012-12-30
As i can't get online via Lubuntu could i get the same information from Windows 7 as it is sharing the same hard drive?

---

### Post by jmate24 on 2012-12-30
the network manager is in the bottom right corner of the screen next to the power button you need to click on it and choose the network (SSID) and then enter the password for the ISP modem (Wi-Fi password you entered in Windows) it should get you on-line after you enter a new password for the "Default Keyring".

If there is no (SSID) then it may be a Hidden Wireless Network and you want to (Click) on "Connect to Hidden Wirless Network" then enter the (SSID "the name of the network") and then enter the password for the network. Then enter a new password for the "Default Keyring"

If that does not work and you cannot see any (SSIDs) then you need to change your Wireless Adapter. Which sadly means you have to go out and purchase a new adapter. But there is another option to installing a card in your computer there are USB Wi-Fi adapters and it just requires an open USB port.

The one I would recommend is an AirLink AWLH6075 Wireless N Adapter it is just Plug and Play and it does not need a disk or any kind of configuration at all. It supports both PC and MAC.

I know that it works with Lubuntu because I have Lubuntu currently installed on 4 systems and it works in every one even going from a 32-bit to a 64-bit computer.


Best of Luck,

jmate24

---

