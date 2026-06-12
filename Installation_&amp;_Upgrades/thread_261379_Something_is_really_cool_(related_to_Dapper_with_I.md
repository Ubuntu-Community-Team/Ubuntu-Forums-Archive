---
title: "Something is really cool (related to Dapper with Intel 865G chipset)"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by ginyip on 2006-09-20
Today, I decide to install Ubuntu 6.06 amd64 on my system.
My system is the following:
Intel Pentium D 805 CPU
ASRock 775i65G Motherboard
1G Ram
video and sound I use the on board one
    they are known as 865G and ICH5 chipset

Now the funny thing beginning. I put in the live CD and start to install Ubuntu. Every thing was fine. woohoo. finish installing.
Now system reboot. It locked up. OK, I though it maybe something like Winxp installation; it doesn't restart. So I manunally restart it with the reset button (on my machine). Now everything boot up fine. woohoo Ubuntu x window are back again.

OK. so I try to reboot it again. it locked up. I reboot it manually again. I try to reboot to X with ctrl-alt-backspace, it locked up. So again, i reboot it manually. I tried shutdown the system now. It locked up again.

Defining Locked Up: X window's cool exit sound come up with black   screen. then nothing happen. It stay that way for 2 hours. I had tried.

So if system can boot up at the first time, why can't i reboot it UNLESS i reboot it manually. lol

Any clue?
I can tell ya, Fresh installation. nothing edited and updated.

---

### Post by ginyip on 2006-09-20
Hey guys, I found the problem.
If you are using the same Intel chipset motherboard, in specific, the 755i65G motherboard from ASrock. Try to start up the Live CD with [COLOR="Red"]safe graph mode[/COLOR]. This mean that you choose the second option on the bootup manual. and then it will also boot into Ubuntu X window system. Now install your system from there (you know, double click on the install drive on your desktop).
I don't know what's going on with this. But I guess that, once you try to run the normal installation, the system will use i810 device for your intel graphic. However, when you install it on safe graphic mode, the driver will become vesa. It might be the problem with i810 driver. I don't know. and I am willing to find it out. =)
[COLOR="Red"]Try to run installation on safe graphic mode. That's safe you more time[/COLOR]. Maybe you can try install on normal mode. Then rewrite your xorg.conf with vesa driver. I never try this one thou.
Have fun and Linux all the way =) :-({|= :-({|= :-({|= :-({|=

---

