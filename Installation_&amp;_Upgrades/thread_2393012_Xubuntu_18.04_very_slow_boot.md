---
title: "Xubuntu 18.04 very slow boot"
date: 2018-05-28
forum: Installation &amp; Upgrades
---

### Post by ulissipus on 2018-05-28
I did a fresh install of Xubuntu 18.04 on my Toshiba Satellite A-205 (CPU - 1.6GHz; RAM - 2GB; HD - 160GB).  

The computer works as fine as ever were it not for the booting: between turning it on and getting to the Xubuntu's initial screen (after the password screen) it goes for 5-6 minutes! Shutdown also takes for a long time though not as long as turning on.

I have reduced the swap from 60 to 10. That was of no help.

Any ideas on how to make my Toshiba boot/turn on-off quick?

---

### Post by uRock on 2018-05-28
I'd recommend more RAM and/or an upgrade to SSD. I have an old ASUS laptop that takes forever to boot on the regular HDD, but when I drop the SSD in it, that time is reduced to seconds. It already has 4GB of RAM.

---

### Post by ulissipus on 2018-05-29
Thank you very much. What you say does make sense but I do not think it is worthwhile making such an investment in my Toshiba. I do like Xubuntu and it is not the case to migrate to another distro. The computer works fine, only the booting time is a bit (understatement) long.
Best

---

### Post by Claus7 on 2018-05-29
Hello,

you could start by issuing the commands:
```
systemd-analyze blame
systemd-analyze time
```

and check from there what is causing the slow boot. I think that it is not normal to have such a slow boot time.

Check also if you have any startup applications that interfere with your boot. Also, verify that snap is not slowing you down, yet I do not think that this is affecting that much.

Regards!

---

