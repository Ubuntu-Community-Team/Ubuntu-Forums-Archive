---
title: "legacy to uefi dual boot with win 10"
date: 2017-08-14
forum: Installation &amp; Upgrades
---

### Post by uvbhanot on 2017-08-14
i bought this laptop from a vendor and he installed the win 10 in the legacy bios mode . now i want to dual boot it with ubuntu ,but i dont know how to work the installation out in the legacy bios mode.
how to change legacy to uefi in existing win 10?
how to dual boot afterwards?

---

### Post by 9vaz on 2017-08-14
Well, first you need to get inside the BIOS settings in order to do that. Most of them appears the option as "Secure boot", then you can disable it. Better check out for the guide of your BIOS, how to get in the settings and all of that. There are threads here where you can check that too. Here is one. :)
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
Hope that works for you now.
If you have any more problems feel free to ask in the forums.

---

### Post by ajgreeny on 2017-08-14
There is no way to change from Windows in legacy mode to Windows in UEFI mode without reinstalling the OS, I'm afraid, so assuming you still want Windows, your most sensible way to proceed may be to continue and install Ubuntu in legacy mode as well.

How best to proceed with that will probably be totally dependent on the current partitioning system that the Windows OS is using as there are only 4 partitions possible in legacy mode though one of those 4 can be an extended partition containing many logical partitions.

Before moving any further and perhaps "killing" your Windows OS, show us a screenshot from gparted in the live Ubuntu system, From that we will be able to see a lot more detail of the partitions you have now and may be able to tell you the best way forward.

I would also recommend that you turn of secure boot if it's enabled, though I thought that was not possible to enable when using legacy mode; I'm showing my lack of Windows knowledge now as I've not used it since XP in 2005.

---

