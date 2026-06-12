---
title: "Black screen and missing packages"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Tijmens on 2011-07-09
I installed Ubuntu 11.04 today from an USB stick with the alternate install. The installation went fine, but when I rebooted the screen remain black. I found this [topic]("http://ubuntuforums.org/showthread.php?t=1743535") about it. The kernel boots fine, this "nosplash --verbose text" works.

But I seem to miss some packages mentioned in that post, and my internet connection doesnt work, I'm a bit stuck on what to fix first, and how.

This command for example "sudo service gdm start" tells me "gdm unrecognized service. Also the option "quiet splash nomodeset" does boot, I get a purple screen but then it continues to boot into the command line interface, not the graphic one. After some searching on Google startx and xinit should start one. But the same thing xxxx is currently not installed.

I would guess all these files are on the usb drive on which I placed the ISO. There comes the next thing. If I type in "sudo fdisk -l" I get a long list, no way I can see which device is my usb stick.

Would these missing files for a GUI be included in the ISO, and in that case be on the usb drive? Or should I figure out how to get my lan working?

I found I have a realtek 8188ce wifi card. I also saw there is a tool called iwconfig that you needed to change some settings, but suprisingly this package is also missing.

So for every "possible" solution I think I find, there is a missing package, and no lan connection to download them :(

Any advice on what to fix first, and how? :)

---

