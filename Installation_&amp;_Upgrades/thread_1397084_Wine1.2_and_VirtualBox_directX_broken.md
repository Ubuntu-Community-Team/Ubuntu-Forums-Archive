---
title: "Wine1.2 and VirtualBox directX broken"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Generale on 2010-02-02
Ubuntu9.10. x64 nVidia chipset and drivers.

Wine1.2 and VirtualBox don't seem to be able to use hardware acceleration.

VirtualBox when running Win2k reports DX and / or D3D errors and said apps don't run. I have installed the guest utilities and WineD3D drivers.

Wine 3D performance is pathetic. Using SimCity4 and unreal Tournament as simple benchmarks.

SC4 just spits out lumps of frames  roughly once a second with a pause in between.
UT speed is unsteady and bogs.

I have an old bootable install of 9.04 on the computer on the old hard disk too. I tried SC4 and UT on Wine on it. SC4 worked fine. No bogging. UT didn't work.
I then upgraded Wine to the Karmic version of Wine1.2 and tried them again. Both worked fine.

On my Acer netbook with 9.10(32 bit) I tried both games in Wine1.2. Both work fine.

Back to the 9.10 install on the PC...

All the glx stuff seems to be reporting all the right stuff. Native glx apps work fine.

I tried updating to the winehq repository version. No difference.

In the System32 directory I found dxdiag.exe which means some naughty app installed dx. So system32 got put aside and a copy of the 9.4 version was put in its place as the wine install is known good.
No difference.
Did the same thing with the three .reg files
No difference.

I feel the VirtualBox and Wine issues are connected, but how? What's going on here? I don't want to do a reinstall but it's starting to look like I have to.

---

