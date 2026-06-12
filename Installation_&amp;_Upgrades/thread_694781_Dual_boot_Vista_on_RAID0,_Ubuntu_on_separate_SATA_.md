---
title: "Dual boot: Vista on RAID0, Ubuntu on separate SATA (mostly works)"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by rolandus on 2008-02-12
Hi All,

I have three HDDs on my system. Two are in a RAID0 volume with Vista installed ON THE ENTIRE VOLUME. The third HDD is a single SATA drive installed with Ubuntu Fiesty Fawn (64 bit).

I am currently using the Vista bootloader to boot into either operating system. This part works fine! (I got the dual booting to work by using EasyBCD and some minor contortions. Basically, I had to install GRUB to the *boot partition* on the 3rd HDD instead of the MBR as would usually be the case.)

Unfortunately, every time I restart the computer after having booted into Linux (from the Vista bootlaoder), my BIOS thinks that my RAID volume is "damaged" and I have to "repair" it before I can choose it as a boot device in the BIOS settings. Ultimately, this means that I still have to enter the BIOS every time I want to boot into Vista after Linux. (but not the other way around)

So, I *think* Linux is somehow fragging the BIOS settings every time it starts up, but I'm not really sure. It's also possible that this is just a MB issue and that the BIOS is wacky (which would be depressing).

Does this ring any bells with anyone?

---

