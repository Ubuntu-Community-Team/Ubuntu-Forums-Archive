---
title: "WTF? Sound cards are gone!"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-09-23
I'm using kernel 2.6.30, because 2.6.31 is unstable and slow for me (xl2tpd problem here: [https://bugs.launchpad.net/bugs/400748](https://bugs.launchpad.net/bugs/400748)). But both soundcards are gone in 2.6.30, although they are seen in 2.6.31.

---

### Post by Joe_Bishop on 2009-09-23
dmesg tells nothing about sound card:
```

07:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD$
        Subsystem: ASUSTeK Computer Inc. Device 8275
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at 1000 [size=256]
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: AV200
        Kernel modules: snd-virtuoso

```

---

### Post by psyke83 on 2009-09-23
I don't need to remind you that you're using an unsupported configuration, right?

Anyway, it may be a conflict due to the ALSA kernel modules being older than the userland libraries.

---

### Post by Joe_Bishop on 2009-09-23
Do you mean hardware configuration or kernel-userland one? Hardware is fully supported (it's ASUS Xonar DX, supported since 9.04 or even 8.10). About software: 2.6.31 is one big bug for me, it always drop in kernel panic or hangs up, I can't use it (hm, they call this stable?)

---

### Post by umberstark on 2009-09-23
The soundcard in my Amilo 1718 disappeared after the first or so set of updates to Alpha 6 were downloaded and installed.

---

### Post by philinux on 2009-09-23
I'm sure my card was listed before now it's gone. Just have to wait for a PA update.

---

### Post by todak on 2009-09-23
> **Joe_Bishop said:**
> (hm, they call this sh1t **stable**?)
Not very descriptive of your situation. You are posting your message in the **Karmic Koala Testing and Discussion** forum, after all. Right now you are **testing** an **alpha** release. That means it is **NOT** stable. There are ongoing updates and I am quite certain that future updates from now up until the final release of Karmic Koala will resolve your issue. Patience Grasshopper. :)

---

### Post by Joe_Bishop on 2009-09-23
> Not very descriptive of your situation. You are posting your message in the Karmic Koala Testing and Discussion forum, after all. Right now you are testing an alpha release. That means it is NOT stable. There are ongoing updates and I am quite certain that future updates from now up until the final release of Karmic Koala will resolve your issue. Patience Grasshopper. 
My issue is on the bugtracker for a long time, but no one have noticed it yet.

---

### Post by philinux on 2009-09-23
It needs someone to go to that bug and change it's status from new to confirmed. Someone with same gear etc.

---

### Post by talkingwires on 2009-09-23
My soundcard went missing with this morning's updates. I'm using some generic Crystal Audio chip they threw into low-end laptops seven years ago.

---

### Post by shakaran on 2009-09-24
May this help you:

```
sudo rm -rf ~/.pulse ~/.pulse-cookie && sudo killall pulseaudio
```

---

### Post by philinux on 2009-09-24
I tried the above. Did not work. Reinstalled alpha6 and applied updates worked.

---

### Post by umberstark on 2009-09-29
Worked out why my card went missing.

It was when I installed the Smartlink Modem driver through the restricted Drivers program.

When I removed the driver through the same program, my soundcard was automatically back and working again, no restart required etc.

---

### Post by ffi on 2009-09-29
try, it should work instantly if it works but not persist boot:
```
sudo udevadm trigger
```

---

### Post by Joe_Bishop on 2009-09-29
> **ffi said:**
> try, it should work instantly if it works but not persist boot:
```
sudo udevadm trigger
```
I can't do it now. I've reinstalled ubuntu completely (I had a mess in my ~ and /etc) from Alpha 6 LiveCD, so, I don't have 2.6.30 instance. But I've faced with the horrible incompatibility between 2.6.31-11 and xl2tpd. In most cases the system hangs up after successful connection with l2tp server. I want to try openl2tp now, but it doesn't have compiled 64-bit version for debian systems, and the source itself can't be built without tweaking. Will try to build it next weekend.

---

