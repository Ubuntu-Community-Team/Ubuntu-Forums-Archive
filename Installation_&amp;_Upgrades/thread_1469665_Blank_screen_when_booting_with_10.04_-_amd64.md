---
title: "Blank screen when booting with 10.04 - amd64"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by kalamcs on 2010-05-02
Hi

I have a Asus A8N-E motherboard with AMD64 processor and NVidia 6600 GT graphics card.

I downloaded the AMD64 version of 10.04 (the boot+live cd) and tried booting with it. After looking at the screen showing Ubuntu loading with 5 dots moving forward for about 5 minutes, the screen went blank (not completely blank as power-off but a very dark grey color). I waited for about 10-15 minutes in this state but nothing happened.
During this whole 10-15 min period the disk usage on the machine was high.

Eventually, I just turned off the machine and booted into windows (which was already present on my machine) successfully.

Is that blank screen for such a long duration a normal step during installation or was a different process expected?

Any comments/ideas?

Thanks
Kalam

---

### Post by reiki on 2010-05-02
I've had trouble booting the live CD as well. It does eventually get to a desktop but it takes a really long time. I had better luck by creating a bootable USB flash drive. You might try searching for -nomodeset as a parameter to boot the Cd. I think you get to where you can enter that by hitting shift as soon as you see the little keyboard = stick person at the bottom of the screen.  But search for nomodeset and get better instructions

---

