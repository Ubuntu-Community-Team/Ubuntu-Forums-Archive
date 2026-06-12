---
title: "I have both nvidia and intel drivers...but system is recognising only intel"
date: 2017-10-09
forum: Installation &amp; Upgrades
---

### Post by alex4126 on 2017-10-09
I am new to linux and i wanted to switch between intel and nvidia graphics driver(for cuda programming), and there was this command
[B][U]lspci -k | grep -A 2 -i "VGA"

[/U][/B]which checks what graphics drivers i have got.
After typing this command on the terminal i saw only intel driver and not the nvidia one.How can i change my driver to nvidia permanently.Plz help!

P.S.The link to the tutorial which i saw is given below:
[https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu](https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu)

---

### Post by oldfred on 2017-10-10
Did you see comment?
lspci -k | grep -E -A2 -i 'VGA|3D'

But my system only shows nVidia and is the same with either command.
I have not checked for a couple of years but my UEFI has a setting for one or both video systems, so I assume I only have the PCIe device enabled for video.

 ```
lspci -k | grep -E -A2 -i 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. GF108 [GeForce GT 620]
    Kernel driver in use: nouveau
fred@Asusz97:~$ lspci -k | grep -E -A2 -i 'VGA'
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. GF108 [GeForce GT 620]
    Kernel driver in use: nouveau

```

---

