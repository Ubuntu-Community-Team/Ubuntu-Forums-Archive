---
title: "Kernel panic, timer doesn't work"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by angelboy on 2006-10-28
I tried to install ubuntu 6.10 x64. on my computer. When I insert the livecd and bootup, it almost immediately says something like:

kernel panic, io-apic, timer doesn't work. try the 'noapic' setting.

32-bit version does the same thing.

What does that mean? Is it something with bios or what? I can boot livecd fine, if I add the 'noapic' parameter to boot options. Is there side-effects not using apic? Is there anyway to solve this problem?

Thank you.

My pc:
AMD Athlon X2 3800+
Asus M2N-E (Nvidia chipset, latest bios)
512 MB DDR2 667Mhz
IDE hard disk

---

### Post by strelok89 on 2006-12-21
i got this problem too :( :( :( :(

on my pc
gigabyte m55s-s3
1gb dual chanel ddr2

---

### Post by sampan74 on 2007-01-07
You can still boot it by pressing <F6> in the boot menu and then you give the argument noapic as a boot option. 

That is: last in the line after the -- you type noapic. This should solve your problem, at least temporary. It worked for me on my Athlon X2 3800+ and Asus M2N 1394 mobo

---

