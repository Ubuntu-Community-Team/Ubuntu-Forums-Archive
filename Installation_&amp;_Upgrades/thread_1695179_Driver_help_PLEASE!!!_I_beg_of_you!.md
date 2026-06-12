---
title: "Driver help PLEASE!!! I beg of you!"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Werewolf486 on 2011-02-25
Need help and advice on Ubuntu intstall. I need to install 10.04 64 bit on a fresh build. I checked the manufacturer website support for the board and no drivers for Linux. So what to do?

MB:                 GA-X58A-UD5 Gigabyte
Memory: 6GB (3x2048MB) T/C Kit PN - OCZ3G1600LV6GK
PSU: Corsair 750Tx
GPU: ASUS 8400gs
HDD: WD 320gb Blue
HDD: WD 1TB Blue

This machine will be used in a studio for music editing and recording not for game play, but it has to be idiot proof on the OS side of things to minimize issues. If you can hook me up with locations of drivers and what not I would REALLY Appreciate it and so would the builder.

Thanks all!
:guitar:

---

### Post by oldos2er on 2011-02-25
Have you tried booting from a LiveCD to see how things work?

---

### Post by Joe of loath on 2011-02-25
99% of Ubuntu's drivers are built into the kernel. You only need a downloaded driver in exceptional circumstances.

Ubuntu is not Windows. Ubuntu actually has driver support ;)

---

### Post by oldsoundguy on 2011-02-25
I have built 8 Ubuntu boxes in the past 2 months .. differing mother boards and hardware configurations.  The ONLY drivers I have had to install are the restricted NVida video drivers, and sometime even those were not needed as the non restricted driver worked BETTER.

Unlike Windows, you do not have to go all over the web to find the latest updated drivers for the majority of desktop hardware.

Laptops, on the other hand, because of the highly proprietary nature of their construction .. DO need some searching sometimes.

---

### Post by Werewolf486 on 2011-02-25
Sweet....makes life so much easier! Thanks everyone!

---

### Post by walt.smith1960 on 2011-02-25
There is one area that can be a PITA--wireless networking. You may not have to worry about that given your intended use.  If you do need to buy peripherals, a few minutes spent researching what hardware installs and functions painlessly can be time well spent. I'm thinking of things like video capture boards.  Don't assume every device from every vendor intended for less common tasks will be plug & play.  I've built a few machines using Gigabyte boards; they've been plug & play.

---

### Post by Werewolf486 on 2011-02-25
Well this is probably the biggest issue I have right now....no internet on a Gigabyte GA-X58A-UD5 with dual RTL8111D chip (10/100/1000 Mbit) Please give me some ideas here. Is this a common issue?

---

### Post by oldsoundguy on 2011-02-26
A publicized trick on installing on a desktop is to do so with the WIRED eithernet/internet plugged in and after the install, unplug the hard wire re-boot  and set up the wireless .. should be an icon in the top bar.  The only thing I have had to do was fill in the network password. BUT there have been some issues with Broadcom (getting better), so I use d-link and it always installs.

---

### Post by walt.smith1960 on 2011-02-26
> **Werewolf486 said:**
> Well this is probably the biggest issue I have right now....no internet on a Gigabyte GA-X58A-UD5 with dual RTL8111D chip (10/100/1000 Mbit) Please give me some ideas here. Is this a common issue?

Not common but RTL8111D seems to have an issue.  I found this thread:

[http://ubuntuforums.org/showthread.php?t=1548422&highlight=rtl8111d&page=2](http://ubuntuforums.org/showthread.php?t=1548422&highlight=rtl8111d&page=2)

If you can do so easily, you might try a live CD of Mint10, which is based on Ubuntu but has more restricted drivers and such enabled by default.  You could also try the alpha2 build of natty (11.04)  Natty seems to have improved support for newer WiFi adapters, it might have support for your ethernet chips too.  Natty won't be released 'til somtime in April but if it doesn't take you too long, running it as a liveCD might give you an idea if support will be forthcoming.  You could try enabling backports but you'll need some sort of internet connection in order to do that afaik.  You don't have an old USB wireless network adapter (or old ethernet card) you could plug in to see if it's recognized out of the box, do you?  
If you could establish *some* sort of internet connection, You could check for restricted drivers, backports etc.  I keep a  cheap wireless G adapter for just such occasions.  It's kinda slow but it's recognized by all Linux kernels as soon as it's plugged in.

---

### Post by Werewolf486 on 2011-02-26
Alright I have the issue fixed it seems. I removed the old unsupported D-link wireless card from the 90's he had in it and installed my old Netgear GA311 Ethernet card. At this point I'm thinking getting connected to the internet with the card might let an update happen and it may cure the issue with the on-board Ethernet ports.  When I rebooted Ubuntu had the drivers to run internet through the Netgear. Once I updated Ubuntu the on-board Ports started working. So I guess it does pay to keep old crap parts.

I do have a few questions about Ubuntu and this board format since I can't test every aspect of it. The MB has USB 3.0 and Esata/USB ports so does Ubuntu support these?

Again thanks people!

---

