---
title: "Karmic eat my WIFI connection!"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by YukaToshi on 2009-08-01
It was fine when I turned it off, but when I turned on this morning it doesn't connect or show the detected networks list. Funny thing is it still detects the WIFI dongle, and I can enable/disable wireless connections from the network applet. 

Any ideas how to fix this?

---

### Post by psyke83 on 2009-08-01
Check the wireless switch (physical or software-controlled)

You should give more information about your hardware if you expect others to troubleshoot (such as the name/chipset of your wireless card).

---

### Post by taavikko on 2009-08-01
> **YukaToshi said:**
> It was fine when I turned it off, but when I turned on this morning it doesn't connect or show the detected networks list. Funny thing is it still detects the WIFI dongle, and I can enable/disable wireless connections from the network applet. 

Any ideas how to fix this?

```
rfkill list
```

```
nm-tool
```

For starters for a bit of more information.

---

### Post by YukaToshi on 2009-08-01
```
yukatoshi@yukatoshi-desktop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
yukatoshi@yukatoshi-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:19:66:82:EE:E1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2500usb
  State:             disconnected
  Default:           no
  HW Address:        00:1D:0F:DF:42:65

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


yukatoshi@yukatoshi-desktop:~$ 

```The weird thing is it says disconnected there but the right click enable wireless option on the NetworkManager Applet disappears when I take the dongle out, and reappears when I plug it back in.

Oh and I've tested the dongle on my laptop and friends PC and it works fine, so the dongle isn't the issue.

---

### Post by taavikko on 2009-08-01
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/396417](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/396417)

New 2.6.31rc5 was released yesterday and it should find its way to ubuntu in a very near future, which could resolve this issue.

---

### Post by YukaToshi on 2009-08-01
> **taavikko said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/396417](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/396417)

New 2.6.31rc5 was released yesterday and it should find its way to ubuntu in a very near future, which could resolve this issue.

It was working fine on the 2.6.31 RC4 kernel yesterday. Anyway weird, I'll just have to jack the router from my parents at some point and manually update on wired! :D

---

### Post by YukaToshi on 2009-08-01
Oh and how rude of me, thank you for your help taavikko.

---

