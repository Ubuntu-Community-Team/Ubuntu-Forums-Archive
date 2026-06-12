---
title: "[Linux Mint] Can't connect to WiFi"
date: 2016-03-29
forum: MINT
---

### Post by meh2 on 2016-03-29
WiFi connections are visible but I can't connect to them .....sometimes it connects but a few minutes later it just disconnects and doesn't connect again. Can someone help me out? I'm new to Linux.
I have a RTL8732BE WiFi card.

---

### Post by jeremy31 on 2016-03-29
[https://forums.linuxmint.com/viewtopic.php?f=53&t=219125#p1148421](https://forums.linuxmint.com/viewtopic.php?f=53&t=219125#p1148421)
```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be
```

Unless you have a newish HP laptop you can ignore the instructions from the link after reboot

---

### Post by howefield on 2016-03-29
Thread moved to the "*MINT*" sub forum.

---

