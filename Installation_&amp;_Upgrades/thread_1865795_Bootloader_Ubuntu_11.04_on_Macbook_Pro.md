---
title: "Bootloader Ubuntu 11.04 on Macbook Pro"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by dracotux on 2011-10-20
Dear Ubuntu fans,

I finally was able to install Ubuntu 11.04 on a Macbook Pro 8.1 early 2011. It took me a while, but I finally found out.

The next thing, is to get Ubuntu booted. I updated the EFI bootloader, as suggested on multiple forums or tutorial sites. 

The bootloader shows the Linux partition, but when I select this, it says "Missing Operating System". And that's the thing I can't solve.

During the install of Ubuntu, I chose (past tence of choose is chose?) to install the bootloader on sda4, where my Linux installation was. The swap area I installed on sda3, a separate partition of 1 Gb. 

I guess the location of the bootloader may not be the brightest of ideas. Should I install this on [COLOR=Red]sda[/COLOR] instead of [COLOR=Red]sda4[/COLOR]? Or will this break any other bootloaders and completely ruin my system? If it turns out not to work correctly, is there simple way to fix this?

Kind regards,
dracotux

---

### Post by dracotux on 2011-10-20
I fixed it myself! I read an article about the Master Boot Record, about supporting a max of 4 primary partitions. Swap was the fourth, Linux the fifth. So I repartitioned, installed again, making Linux the fourth partition. It doesn't boot from Refit (yet), but I need to hold down the alt/option key during startup.

Don't know if this makes any sense, or what I just have written above is a fact, I don't care. IT WORKS!!!! Ubuntu 11.04 on my Macbook Pro 8.1 early 2011!!!!

---

