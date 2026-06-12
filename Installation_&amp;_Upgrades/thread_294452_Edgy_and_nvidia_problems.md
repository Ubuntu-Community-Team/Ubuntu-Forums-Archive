---
title: "Edgy and nvidia problems"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by simonn on 2006-11-06
I have been playing with Edgy (Kubuntu) and I had problems installing the nvidia binary driver. Searched around and it seems like lots of people had similar problems.

I then kicked myself because it was the same problem I had with breezy and documented here [http://www.ubuntuforums.org/showpost.php?p=1352092&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1352092&postcount=6)! Doh!

A way to test if this is the same problem is to add the option "NvAGP" "0" to your video card's "Device" section. This turns off agpgart (all the fast agp 3D stuff), but makes it less likely that X will hang. For example, in xorg.conf:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NvAGP" "0"
EndSection

```

If X starts properly now, then have a look at the link above on how I got agpgart working with breezy.

I hope this helps someone.

---

