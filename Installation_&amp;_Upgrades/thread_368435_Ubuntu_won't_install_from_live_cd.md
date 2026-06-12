---
title: "Ubuntu won't install from live cd"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by Mozork on 2007-02-23
Today I was trying to reinstall ubuntu from a live cd, I downloaded (and burned) just today. Booting from cd works just fine, but during the installation is just hangs up at a certain point. - After 23% or maybe a little preciser: shortly after it starts writing to the linux partition. I've tried this several times, and it's always the same, exact point where it stops. What i've noticed in addition is, that when I create the ext3-partion for the ubuntu and go back (imagine the GUI Installer) to the partition manager, everything seems fine, but when i go one step forward and one back again the same partition i just formatted is set to unknown, which is somewhat weird.
I've also tried to verify, that the live cd is ok, and that process hangs up after having checked about 85-90%.

I'm using a Dell Inspiron 6400 Laptop, with 2 GHz Core 2 Duo and 2 GB RAM.

---

### Post by Kateikyoushi on 2007-02-23
What speed did you use to burn the disc ? It is recommended to use maximum 4X, but that's also strange that the check hangs as well.

---

### Post by Mozork on 2007-02-23
It's quite likely I did burn the cd faster than 4x, so i will burn it again and give it another try.
But I mean, it booted, wouldn't I notice something there if the cd was not bruned right?

---

### Post by Kateikyoushi on 2007-02-23
If you do a serach about it on the forum will see it seems random effects might occur, so we can't be sure whether the disc is at fault or not.

You can try this as well because on such new hardware there might be other reason for it as well.
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false

---

### Post by slakkie on 2007-02-23
I once had a similair problem, I resolved it by using the alternate CD. You could use the server CD as well, and build your (edu|k)ubuntu-desktop from there.

---

### Post by Mozork on 2007-02-23
It actually was the cd^^
Everything works just fine now...
Thanks a lot. :D

---

