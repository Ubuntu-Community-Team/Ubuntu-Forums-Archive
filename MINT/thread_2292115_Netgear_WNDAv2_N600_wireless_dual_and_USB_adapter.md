---
title: "Netgear WNDAv2 N600 wireless dual and USB adapter"
date: 2015-08-25
forum: MINT
---

### Post by nathanp950 on 2015-08-25
Now I am new to these threads as well as LinuxMint and am not familiar with the commands (but capable of doing them via instructions). I have read similar posts about this device but get redirected to different versions, can anyone help me install this. For some reason I cannot connect through a wired connection so I am doing the downloads of the drivers via USB but I am not sure exactly how to go about installing the drivers on the new OS. Please help

---

### Post by howefield on 2015-08-25
Thread moved to the ""*MINT* forum.

---

### Post by nathanp950 on 2015-08-25
How did that happen?

---

### Post by howefield on 2015-08-25
> **nathanp950 said:**
> How did that happen?

You are welcome to post your question in [this]("http://ubuntuforums.org/forumdisplay.php?f=453") forum, but you may find that you are missing out on the support of the [MINT community]("http://forums.linuxmint.com/").

---

### Post by chili555 on 2015-08-25
I understand your device is 0846:9014. I suggest you read this post: [http://ubuntuforums.org/showthread.php?t=2221251&page=3](http://ubuntuforums.org/showthread.php?t=2221251&page=3)> At this time, I know of no way to get the device working. If you can find Windows XP 64-bit driver files, that is .inf and .sys, we can try ndiswrapper again.

---

### Post by amit-dear25 on 2015-08-25
i got your problem its drivers can be updates  through terminal you just have to type sudo apt-get update
and go to system settings/software and update/additional drivers and updates..
after that you will get yr drivers n through update u can update yr system for better performance

---

### Post by nathanp950 on 2015-08-25
Will I need to be connected to internet? It wont connect to wired it just keeps saying "connecting to wired connection" and never gets through.

---

### Post by chili555 on 2015-08-25
> **amit-dear25 said:**
> i got your problem its drivers can be updates  through terminal you just have to type sudo apt-get update
and go to system settings/software and update/additional drivers and updates..
after that you will get yr drivers n through update u can update yr system for better performance'Additional Drivers' only provides wireless drivers for Broadcom devices. It won't help his Mediatek in any way. Sorry.

---

### Post by nathanp950 on 2015-08-25
Ok so it's a v3 not a v2, the drivers wont work for v3 like they would for v2? Why is mediatek so different? I cannot get the "Wired" connection to work either, i dont understand what''s going on..

---

### Post by chili555 on 2015-08-25
It's not Mediatek that's being difficult; it's Netgear. They changed the chipset and therefor the version. Your usb.id of  0846:9014 tells us it's a V3 and a Mediatek chipset. You can verify it:```
lsusb
```

I suggest you start a new thread for your ethernet. Be sure to include:```
lspci -nn | grep 0200
```

---

### Post by nathanp950 on 2015-08-25
Sorry, I figured out the ethernet issue so that's good, ran the update like he suggested and just to ensure everything else was up to date as well which it is. So far through hours of searching all i found was one post where someone was somewhat creating their own driver that basically backpacked off of another version and i guess made progress but then stopped posting about how exactly, and didn't give any specs on how to do that either so I guess I'm just stuck with the wired connection for now. I got that adapter for a computer I was planning on using only for gaming (while it still had XP) and of course the version i bought was the version that has no known compatibility for Linux at this point in time -_-

---

