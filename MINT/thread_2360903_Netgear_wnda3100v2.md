---
title: "Netgear wnda3100v2"
date: 2017-05-09
forum: MINT
---

### Post by lowdown762n on 2017-05-09
Ok.  Well this one took a bit but I got it to work full speed on my Linux Mint "Sarah" 32 bit.  Sorry old laptop.  The steps I took are these

1. I installed the bcmn43xx32.inf via the windows wireless driver app.
    The bcmwlhigh5.inf installed but showed not present but the bcmn43xx32.inf installed and showed present.

2. I stopped the Network Manager.
    Not sure if that was needed or not.  If it is I will probably disable it totally as it starts at boot.

3. I did a iwconfig and it showed an 802.11 named wierdly enc********. but that was the interface name I needed for Wicd. The *'s are to replace some of the long name, not the actual characters.

4. I opened Wicd and went to the preferences. On the line labeled as wireless interface I put the interface name of enc********.  Yours maybe different.

5. It started scanning and found my network.  With the password entered it connected quickly and I was able to surf.

Before using network manager I would never get an IP address.  I tried manually and still it wouldn't connect to the internet.  Now however I am "THANKFULLY" having no issues.  I hope this will help someone else as I went through every loop around until this worked.

---

### Post by jeremy31 on 2017-05-09
*Thread moved to **MINT**.*

---

