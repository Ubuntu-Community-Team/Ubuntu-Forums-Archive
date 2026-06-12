---
title: "Wireless does not autostart in NetworkManager (Lucid) after Kernel Upgrade"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by kmrdeva on 2010-06-18
Hi all,

I've been searching for a solution for a number of weeks now without any success. If this has been discussed before, can someone help point the way for me?

Recently, I installed a fresh 64bit Lucid Lynx on my Lenovo B450 laptop (previously on Mint8 64bit, based on Karmic). It's been really nice and speedy except for one thing - USB transfers to thumb drives and external hard drives were really slow (just like in the older Ubuntu releases). I had found some forum discussions on a fix to this by way of a kernel upgrade so I decided to go for it.

Went ahead and downloaded the kernel DEBs from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/) and installed them. Voila! USB speed issue was fixed! Everything else seemed to work fine, except for some minor troubles with burning CDs and DVDs (I think I need to upgrade the drive's firmware - pretty bad situation as the update only runs on Windows).

However, the one 'bug' or 'annoyance' I noticed straight away was that my wireless wouldn't autostart after booting into the OS with the new 2.6.34-020634-generic (x86_64) kernel. I'd have to right-click on the NetworkManager icon on the notification tray and left-click '[ ] Enable Wireless' to flag the checkbox and my wireless would come right up and work ok (WPA2 at home, WEP at the office). Not a major problem, but this has been pretty irritating to say the least.

Any ideas, guys? Should I ditch NetworkManager and go with wicd instead? :(

---

### Post by jeebustrain on 2010-06-18
this might be a longshot, but does the wireless drivers use ndiswrapper? Check System -> Hardware drivers and see if it uses a proprietary driver. If it does, remove it and then re-add it. See if that fixes it.

Another issue could be along the lines of what I had with a Ralink wireless PCI card. The default OOB drivers would not automagically connect. I ended up using the info here to install the correct drivers. It might be worth checking to see if there are any similar issues with whatever wireless chipset your laptop uses
[http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)

---

### Post by kmrdeva on 2010-06-18
Thanks for the tips, jeebustrain.

I went to System / Administration / Hardware Drivers - nope, no proprietary drivers are in use on my system.

I think my Lenovo's wireless card is using an Atheros driver (built into the kernel, no?), I saw 'driver:ath5k' under Connection Information via the NetworkManager tray app.

---

