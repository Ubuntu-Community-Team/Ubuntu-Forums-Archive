---
title: "Upgrading 12.04 LTS to 14.04 LTS; Lost All Sound Support"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by Eric_H._Bowen on 2014-08-16
Hello All--

I have been using Ubuntu 12.04 LTS for a couple of years now with no major issues. I am using an ASUS M5A88-M motherboard with AMD CPU, 8 GB RAM, and an AMD graphics card with HDMI output. There is also HDMI from the motherboard's on-board graphics, as well as on-board sound. The sound worked fine under 12.04. I have made no hardware changes. Before the 14.04 upgrade I was running system update to make sure that everything was as up-to-date as possible. The software packages updated without any notable issues, but there was a hardware update item which I clicked on that required a system reboot. After that, I never got 12.04 back up again after multiple reboots. As I was upgrading to 14.04 anyway, I built a USB install stick with my Windows PC, booted from that, and upgraded. Everything appears to work fine, except the sound. There is no sound whatsoever and the Sound Settings shows no device except the "Dummy Output".

I followed the troubleshooting guide located at [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) without success. Steps 1-3 do not apply. Step 4 yields the result:

```
aplay: device_list:268: no soundcards found...
```

Step 5A yields the result:

```
find: `/lib/modules/3.13.0-34-generic': No such file or directory
```

Step 5B yields the result:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-3.13.0-34-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.13.0-34-generic'
```

So for right now I'm stuck. Does anyone have any suggestions?

---

### Post by Eric_H._Bowen on 2014-08-17
It appears this was a temporary glitch; the next day I downloaded the latest software updates for 14.04 and my sound hardware started working. Sorry for any false alarms.

---

