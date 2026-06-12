---
title: "WiFi connected but not actually working (HP RTL8723BE Wireless Adapter)"
date: 2017-10-30
forum: MINT
---

### Post by asdf1234asdf1234 on 2017-10-30
Hello,

My laptop sometimes connects to the wifi network just fine, and sometimes it doesn't. When it doesn't, the "connecting" thing keeps spinning and eventually I get a notification that I'm disconnected.
When it does connect though, I'm not able to ping anything or visit any website. It does this with every "normal" wifi network I've tried, with WPA/WPA2 PSK encryption. When I make a wifi bridge on my phone though, it connects and I can ping and view any website just fine. Can anyone help me with this?

Edit:
I just discovered something new. Linux only discovers networks that have a really strong signal. When I'm at home and upstairs, it doesn't find any networks, while my phone, and Windows on that same laptop, both discover and connect just fine. 

Regards,
Julian

I've attached the output of the wireless info script below.
[ATTACH]277353[/ATTACH]

---

### Post by wildmanne39 on 2017-10-30
*Thread moved to **MINT for a better fit **.*

---

### Post by jeremy31 on 2017-10-31
See if my post @ [https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389](https://ubuntuforums.org/showthread.php?t=2365020&p=13661389#post13661389) helps find more access points.  Some HP's with rtl8723be chipsets used only one antenna

---

### Post by asdf1234asdf1234 on 2017-10-31
Thank you very much for your help. It seems as if it's fixed now. I'll report back in a while when I've better tested it, but I think this worked.

---

