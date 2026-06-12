---
title: "Internet connection"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by flamefox_9 on 2010-01-10
Hey, i dont know if this is the right area to post this thread... but ill ask anyway. I have just installed ubuntu recently, but i cant connect to the wireless internet _anywhere_. I dont know what the problem is and i have already tried connecting in the live cd. The windows 7 on my other partition can connect just fine and that confuses me even more! Can somebody tell me whats wrong? Thanks in advance!

---

### Post by Ishwon on 2010-01-10
Did you verify if your wireless adaptor is installed?

Can you provide more information on your adaptor?

---

### Post by derekmbarnes on 2010-01-10
Open Applications > Accessories > Terminal and run this:

```
lspci -v | less
```

This will give you a comprehensive list of every PCI device built into your machine. Your wireless adapter should be listed at or near the bottom as "network controller;" if you don't see a line about the device driver, it's probably missing and needs to be installed. (Drivers don't work across platforms; that's why it works in Windows.)

Post the output you get here and we'll see if we can point you in the right direction.

---

### Post by flamefox_9 on 2010-01-10
> **derekmbarnes said:**
> Open Applications > Accessories > Terminal and run this:

```
lspci -v | less
```

This will give you a comprehensive list of every PCI device built into your machine. Your wireless adapter should be listed at or near the bottom as "network controller;" if you don't see a line about the device driver, it's probably missing and needs to be installed. (Drivers don't work across platforms; that's why it works in Windows.)

Post the output you get here and we'll see if we can point you in the right direction.
It is installed, but after a hardware driver window appeared, i dont even think that is the problem. It said that i was using a proprietary driver and it was causing problems. Do you think this is it? Oh, and I couldnt post the output or get any information of my adapter... sorry.

---

