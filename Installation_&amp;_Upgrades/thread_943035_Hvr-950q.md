---
title: "Hvr-950q"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by mbw290 on 2008-10-09
I just bought an HVR-950q tv tuner and I can't get it to work.  I think I installed the firmware and software correctly, but ME TV says theres no tv tuner device.  Please help

---

### Post by cariboo on 2008-10-10
What is the output of dmesg when you plug your device in?
In a terminal type:

```
dmesg
```

Post the output in your next post.

I just tried me-tv and I get the same message. I use TVtime and it works perfectly. TVtime is in the repositories

Jim

---

### Post by mbw290 on 2008-10-12
74.715210] usb 7-3: new high speed USB device using ehci_hcd and address 5
[   74.801268] usb 7-3: configuration #1 chosen from 1 choice

---

### Post by andymcca on 2009-10-24
I had the same dmesg output when I was trying to get my 950Q working. I mentioned that I had eeebuntu installed and someone pointed out that this uses the Array kernel. I believe all of the netbook versions also use Array. I installed a generic kernel image with Synaptic and set that to my default boot. I had to add the backported drivers for my wireless again, but otherwise nothing was hurt by the switch (1005HA-P).

After booting with the generic kernel image the rest of the dmesg that various websites indicate you should get comes pouring right out! Afterwards a /dev/dvb/adapter0 appeared and everything worked!

PS you did install the xc5000 firmware, right? If not, google it and you'll find it right away. Since you got that much in dmesg you probably already have it thought.

---

### Post by markackerman8@gmail.com on 2010-04-09
Has anyone had any success with this card and MythTV when watching livetv from an analog cable source (NTSC)?? soooo frustrated!!!

---

