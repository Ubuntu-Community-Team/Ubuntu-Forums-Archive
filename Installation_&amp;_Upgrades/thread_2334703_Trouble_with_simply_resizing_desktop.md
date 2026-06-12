---
title: "Trouble with simply resizing desktop"
date: 2016-08-21
forum: Installation &amp; Upgrades
---

### Post by dannyboy-alive on 2016-08-21
I just installed Ubuntu for first time in years. Trying to escape windows once and for all. Problem is my desktop is bigger than my screen size and I can't seem to simply resize screen or zoom out, so I lose 1 inche and most of the icons as they are off the screen.

I have RX 480 graphics card. Under Nvidia there seemed to be a resize command. I can't find any settings that would enable me to do this.

Can someone help.

---

### Post by Bucky Ball on 2016-08-21
Please post the output of this command:

```
sudo lshw -C video
```

Look in Additional Drivers. Is there an NVIDIA driver offered there? Have you installed any drivers manually to this point? If not, don't just yet.

---

### Post by gordintoronto on 2016-08-22
I have seen several cases where this was fixed by changing the settings on the monitor.

---

