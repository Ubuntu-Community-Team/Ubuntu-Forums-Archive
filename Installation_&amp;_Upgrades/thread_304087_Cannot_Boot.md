---
title: "Cannot Boot"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by evri2 on 2006-11-21
I tried all types of ubuntu which is suitable for my laptop.
My hardware is;
Amd Turion 64 x2(64bit) 1.6ghz
1gb Ram
Nvidia 7200go 256mb
100gb hardisk
Broadcom 4310 Wireless driver
When i try to boot from cd to install,i get this error while trying edgy.

[[IMG]http://img218.imageshack.us/img218/9869/dsc00596qk4.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=dsc00596qk4.jpg)

I cannot install 6.10 with 32bit(i386) and AMD(64bit) cds.
I try to install 6.06.1 with 32bit and 64bit.After 6-7 boots i installed but i got some problems...and sometimes my system which i installed cannot boot.However Xp works fine...

In that "sometimes opens ubuntu 6.06.1" my wlan driver does not work either.But the great majority in here is cannot boot.What should i do?

On my friends laptop both of 32bit cds work fine.

---

### Post by parkash on 2006-11-26
Ok, that error should not keep you from booting.. 

When choosing what to boot (from the livecd) select F6 (I think it's that one, to pass options to the boot line), then just add "noapic" to the boot line and press enter...
Now it should boot alright.

I think that's a bug, since I have been struggling a while with the same problem :s...  But, anyway, with that option you should be able.  No matter whether 32 or 64 bit...

If that doesn't work... Try to passing acpi=off instead of noapic.

---

