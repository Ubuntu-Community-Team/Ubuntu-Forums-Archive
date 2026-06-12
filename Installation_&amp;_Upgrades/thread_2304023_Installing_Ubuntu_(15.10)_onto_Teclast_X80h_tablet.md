---
title: "Installing Ubuntu (15.10) onto Teclast X80h tablet"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by gregor12 on 2015-11-23
I'm trying to install Ubuntu on this Teclast X80h
 tablet.
Main specs:
**CPU**: Intel Bay Trail, 1830 MHz, **Cores**: 4
**GPU**: Intel HD Graphics, 646 MHz
**RAM**: 2 GB, 1333 MHz
**Storage**: 32 GB
**Display**: 8 in, IPS, 1280 x 800 pixels, 24 bit
I run 64bit installation iso, as tablet comes with UEFI locked.
On this installation disk I added "bootia32.efi" to boot into 32 bit UEFI.
Anyway bootloader appears, I select Ubuntu live and slowly after that image dissapears. On various forums, describing similar problems with Teclast, Onda, Chuwi and other cheap Chinese Baytrail based tablets I read, that I should check, what happens on HDMI port.
When I plug HDMI display into tablet port, picture on it appears.
However...
It appears, that this picture is treated as extended desktop, while primary desktop (tablet's display) remains blank.
Touchscreen mouse, keyboard work, however I would like Ubuntu to show also primary screen, so I can continue with installation.
Most probably this problem is easily solvable by experts, which I am not.

I really suggest that you try supporting installation on these cheap Chinese baytrail tablets, as they are becoming very popular (best price/performance) and many people on various forums (reddit,xda) are trying to install Linux onto them.

Thank you in advance for your help. I believe solving this problem and posting it on various forums (I'll try to spread the word) will increase Linux popularity significantly.

---

### Post by gregor12 on 2015-11-24
I managed to run xrandr command, which outputs:
DSI1 connected primary 800x1280+0+0 (normal left inverted right x axis y axis) 0mm x 0mm   800x1280      60.00*+
Can someone pls advise, how to modify kernel boot options.

---

