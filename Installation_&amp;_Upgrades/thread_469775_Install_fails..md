---
title: "Install fails."
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by mckechan on 2007-06-10
I recently bought a barebones system very similar to this one:
[https://www.novatech.co.uk/novatech/specpage.html?BB-AM381GB](https://www.novatech.co.uk/novatech/specpage.html?BB-AM381GB)

and I had fesity running nicely on an hold hard drive.

I then bought the following graphics card:
[https://www.novatech.co.uk/novatech/specpage.html?NOV-76GT](https://www.novatech.co.uk/novatech/specpage.html?NOV-76GT)

 and a SATA II hard drive to replace my old IDE ones.

I've just set up XP running nicely for my games but now I tried installing Ubuntu and it fails. If I select
start Ubuntu it comes up with the splash screen but then it just goes blank and eventually overheats!

The same thing happens if I try to start it in safe graphics mode too.

I guess this is because of my graphics card. What is the best way to resolve this problem?

cheers,

Dave

---

### Post by zvacet on 2007-06-10
Boot in recovery mode and type
```
dpkg-reconfigure xserver-xorg
```

and select** vesa** driver.When you get graphic search for your card driver

---

