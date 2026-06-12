---
title: "Installation problem, possibly sata dvd/hd problem"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by TLoockx on 2007-02-09
Hi everybody,

Yesterday I assembled a new PC, the problem now is that when i put in the Ubuntu 6.10 I can see the installation menu but when I proceed to the installation the system gives me an error that looks like this:

17179570.548000 PCI cannot ellocate resource region 0 of device
17179570.548000 PCI cannot ellocate resource region 1 of device
17179570.548000 PCI cannot ellocate resource region 2 of device
17179570.548000 PCI cannot ellocate resource region 3 of device
17179570.55200 PCI error while-updating region 000

my system contains:
MSI P965 NEO-F motherboard
Intel E6600 processor
1GB DDRII Ram
Sapphire Radeon X1950Pro video card
SATAII DVD-rom
SATAII HD

I also tried with Kubuntu 6.06 but the it hangs when loading the kernel and with ubuntu 5.04 it says that I don't have a correct CD-rom and asks me to select additional drivers.

I looked at specific boot parameters but none of them are applicable for my system.

Thanks in advance,
Thomas

---

### Post by blueglow on 2007-02-09
Hey Thomas.

I had a similar problem (though not with those error messages) when I ran/installed Edgy from the CD on my Vaio laptop with a SATA HDD.

You can see what I discovered and how I fixed it on this thread:
[Can't install or mount SATA NTFS hard disk (laptop)]("http://www.ubuntuforums.org/showthread.php?t=336315")

Not sure it's applicable, but it can't hurt to test. Also, if you look at Jussi's comments in the above thread he lists some commands that it would be beneficial to post the outputs of for more/better help.

Hope this helps mate,

Jim

---

### Post by logos34 on 2007-02-09
You might want to read through this:
> [https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28P965%29%7C%28MSI%29](https://wiki.ubuntu.com/Core_2_Duo_Support?highlight=%28P965%29%7C%28MSI%29)

---

### Post by TLoockx on 2007-02-09
Thanks everybody for the support,

I solved the problem by disabeling the USB keyboard support in the BIOS, Ubuntu 6.10 installed just fine.

---

