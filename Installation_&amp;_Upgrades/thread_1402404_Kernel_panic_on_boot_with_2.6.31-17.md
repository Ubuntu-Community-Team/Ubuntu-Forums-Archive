---
title: "Kernel panic on boot with 2.6.31-17"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by ioliver on 2010-02-09
I installed mythbuntu from a live CD on an old machine with an IDE hard disk just to play with it. It worked a treat, so I bought an Acer Aspire Revo R3610 and used dd to copy the old HD contents to the new one, and then gparted to resize the ext4 partition.

On boot I got -
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

I checked every grub2 command and it all looked fine. I then tried booting the original kernel that the live CD installed (2.6.31-14) and it booted! I tried 2/6/31-17 again, and got the panic.

After much googling, I found a suggestion to do -
sudo update-initramfs -k all -c -v
and this worked.

Is this expected behaviour? One of the delights of Linux is that installs move smoothly between machines, but this one didn't. Was this due to the old machine using IDE and the new one AHCI SATA? How do I get an initramfs that's flexible and will boot smoothly on any given hardware?

Thanks

Ian

---

### Post by mushwars on 2010-02-09
I will have to add that command to my list of things to remember. Thanks for sharing.

It seems lately a lot of people are having kernel trouble, Thanks for finding a solution, luckily not very often do we upgrade our kernels ( we being you guys )

---

