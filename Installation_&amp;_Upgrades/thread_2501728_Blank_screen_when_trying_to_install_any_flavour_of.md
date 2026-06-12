---
title: "Blank screen when trying to install any flavour of Ubuntu"
date: 2024-10-18
forum: Installation &amp; Upgrades
---

### Post by DirtyPC on 2024-10-18
I have a 2008 iMac A1225 (Core 2 Duo, 4GB, Nvidia 8800 GS) that I cannot get anywhere with.

I get to the boot menu but try/install and safe mode just give me a single static underscore when selected, and nothing happens regardless of how long I leave it. I have to hard reset to get out of it.

I have tried all releases back to 19.10, different usb drives, different disk creation programs and nothing seems to work.

There's plenty of videos online of iMacs around this time installing without issues.

Any help would be appreciated.

---

### Post by DirtyPC on 2024-10-19
tried running with nomodeset and it just hangs on 'booting a command list'

Really could use some help with this one.

---

### Post by yancek on 2024-10-19
Does the hardware work, the installed OS boot?  Is this an EFI install of the original OS?   You could try the suggestion at the link below.  If you see the boot menu, hit the e key on the keyboard so you can see the boot entry and make the change suggested.  Seeing an underscore generally means grub not correct.

 [https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot](https://askubuntu.com/questions/2622/blank-screen-blinking-cursor-on-boot)

---

### Post by DirtyPC on 2024-10-19
Solved..ish. the iMacs with a "super" drive (their terminology for a disk drive) are firmware locked for installing any OS via USB. Unfortunately the drive on the iMac isn't functional.. so I currently have a very pretty looking paperweight.

---

