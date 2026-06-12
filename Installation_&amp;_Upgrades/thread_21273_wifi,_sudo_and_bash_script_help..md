---
title: "wifi, sudo and bash script help."
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by fabiang on 2005-03-21
Hi,

I can't see what wireless net are here,  prismstumbler do not work for me. Today
i use windows to see trhe ssid of the nets, i wrote the information and make a sh file like this:

$ cat conecta.sh
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=miSsid authtype=opensystem
sudo ifconfig wlan0 192.168.1.222

Questions:

1. i would like use dhcp to take an ip, ¿what changes i need do?
2. how i can put more options to network, aka: default getaway, dns...
3. i need a program to see the ssid of the nearly wifi nets (or a program to do al of this automaticly) 
4. where is rc.local to put this sh script there?

Today i open a console and i run this sh script to connect, but i need put mi password, for me is ok, but i don't like add to sudo group another users of my computer and they need use the wireless network.

sorry for mi bad english

---

