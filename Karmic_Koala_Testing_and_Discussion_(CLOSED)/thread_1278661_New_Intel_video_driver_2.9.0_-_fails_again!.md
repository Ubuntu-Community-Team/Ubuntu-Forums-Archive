---
title: "New Intel video driver 2.9.0 - fails again!"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-09-29
**[SIZE="6"]UPDATE: It has been fixed! With using the newest kernel "Linux 2.6.31-12-generic" and 2.9.0 installed.[/SIZE]**
It started working with the newest kernel12 and 2.8 driver, but was slower than molasses running uphill in winter. But now it has been restored. No more freezing.

I just installed the new 2.9.0 video driver and no change on my i865. Even with what was reported as a major fix:

```
Major fixes in 2.9.0 compared to 2.8.0
======================================
* Multiple fixes to make the driver stable for 8xx chipsets, (855GM,
  865G, etc.). The 2.8 driver series was extremely unstable with many
  of these chipsets.
```

Go [here]("http://lists.freedesktop.org/archives/xorg/2009-September/047439.html") to read about the newest driver.

There's several LP reports on i865 using karmic still pending. Maybe someone else will have better luck.

---

### Post by Amaranth on 2009-09-30
Did you also install the latest kernel, libdrm, and mesa? These things tends to build on each other.

---

### Post by VMC on 2009-09-30
> **Amaranth said:**
> Did you also install the latest kernel, libdrm, and mesa? These things tends to build on each other.

No I didn't. Thanks for the tip. I wasn't aware I needed to. I'll look into that.

  Oddly enough [PartedMagic]("http://partedmagic.com/index.php") distribution has both xorg-server-1.6.4, xf86-video-intel-2.9.0 installed on there test iso and it works. Totally different subsystems I know, but in the past I needed to install the old intel-2.4.1 on that system as well.

---

### Post by VMC on 2009-10-06
[COLOR="Red"]**I updated the first post so if you have at least an i865 video chip onboard, it has been fixed!**[/COLOR]

---

