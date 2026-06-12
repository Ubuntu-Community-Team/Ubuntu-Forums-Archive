---
title: "Can't boot from USB"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by xXToYeDXx on 2013-01-10
I've searched for the last 12 or so hours trying to find a solution to my problem, but I can't find anything that fits my issue. Some have been close, but not close enough.

I'll try to be as detailed as possible with my issue. I'm fairly new to linux but I have installed and used it before. Just the basics but I have used it.

First, my system specs:

Chassis: Silverstone RV03 Raven 3
Mobo: Asus Rampage 3 Black
CPU: i7 960 OC to 4GHz Stable
CPU Cooling: Corsair H80
RAM: 6GB Mushkin Enhanced DDR3-2000 CL7
Sound card: Asus Xonar Xense
GPU: 2x Asus ENGTX580 DCII in SLI
PSU: Enermax SGalaxy EVO 1250W
SSD: Corsair Force 3 240GB
HDD: Western Digital 750GB for storage

I know it's overkill for Ubuntu but this rig was built for gaming and hence it's been running Windows primarily.

But with the release of Steam for Linux I finally have a reason to abandon winblows for good and go linux exclusively. Well, almost exclusively. I want to dual boot Llnux and Win7, with Ubuntu as my primary OS, and Win7 as a secondary on a 30 or 40 gig partition, just for Counterstrike Global Offensive and the SDK if running those in Wine present unmanageable issues. I can't have hitching or FPS drop in a competitive match.

Now on to the issues I'm having when trying to install.

When installing from USB (tried with 12.04, 32bit and 64bit, and Linux Mint Cinnamon 64bit):

Note: I've used Unetbootin, Universal USB Installer and LiLi. They all produce the same results. I've also tried 2 different USB sticks. 1 is a 16GB PNY formatted to Fat32. The other is a 2GB PC (President's Choice cheapo) formatted to Fat32.

What happens:

1) USB boots into loader
2) USB auto boots into default loader option
3) Black screen with blinking cursor for a few seconds
4) Verbose screen that scrolls really fast.
5) Purple Ubuntu splash screen with red and white dots.
6) Black screen with mouse cursor active.

I can move the mouse cursor without issue, but nothing else loads. No desktop, no wallpaper, no icons, nothing. just the mouse cursor. I've left it for over 20 minutes and still nothing but a mouse cursor.

Linux Mint gets a bit further. It actually boots into the desktop, but it freezes and none of the icons or menu items are responsive. Mouse cursor can be moved freely though.

---

### Post by dino99 on 2013-01-10
ok, so the title is wrong, as you boot but then are stuck on plymouth (dots on purple background) then black screen.

you might boot testing some boot options to bypass that issue:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

note: as you have not said if installation have already be made with the used usb sticks, sometimes, formatting the stick is not enough as they also have a borked table. So in that case, with gparted (or other formatting tool, but its good to use a compatible tool with linux), first rebuilt the table (look into the gparted menu to get it) then format in Fat32 etc.

---

