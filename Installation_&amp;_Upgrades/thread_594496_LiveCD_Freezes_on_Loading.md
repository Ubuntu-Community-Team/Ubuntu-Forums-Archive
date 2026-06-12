---
title: "LiveCD Freezes on Loading"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Speedboxer on 2007-10-28
Hello,

I have a Compaq Presario F565CA laptop (AMD Sempron Mobile 3000+ 1.8 GHz, nVidia GeForce Go 6100, 120 GB SATA 2 hard drive and a DVD-RW Drive with LightScribe). I wanted to dual-boot with Vista and Ubuntu. So, I download the Ubuntu 7.10 ISO, burned it to a CD, and made my Vista partition smaller.

I booted into the CD and chose the default option. After it said "Compiling Linux" it said "BIOS Bug #81" and then when the screen with the Ubuntu logo and loading bar.

The bar froze after a few seconds, and a few seconds after that the disc drive stopped spinning. Then, a few seconds after that, you could here what I think is the lens docking back to it's standby state.

After that nothing happens.

I tried using the boot options "apic=no" and "lapic=no" as mentioned in the sticky thread on Ubuntu 7.10 and HP laptops. That didn't work either.

I upgraded my BIOS from version F.18 to F.1C and the BIOS bug still showed and the same thing happened.

What could be causing this, and is there a way to fix it?

Thanks,
Speedboxer

---

### Post by mikewhatever on 2007-10-28
Have you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29") checked the iso? It is always advised to, unless you download via bittorrent.

---

### Post by Speedboxer on 2007-10-28
> **mikewhatever said:**
> Have you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29") checked the iso? It is always advised to, unless you download via bittorrent.

Yes, and it was correct.

---

