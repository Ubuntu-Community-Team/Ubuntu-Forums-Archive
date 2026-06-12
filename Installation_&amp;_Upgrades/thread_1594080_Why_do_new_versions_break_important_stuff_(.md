---
title: "Why do new versions break important stuff? :("
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Quaxo76 on 2010-10-12
I just tried to install the new 10.10 on my laptop. Luckily I always try new installs on spare partitions first, so I can keep using the old system if something happens.
I had had some problems with 10.04 too - when booting the livecd, the screen was totally covered with horizontal stripes, and there were other artifacts too, making the system just barely usable to install on the HD. (I have a GeForce 7150M video chipset). It worked perfectly on 9.10. Another problem: I have a USB mobile broadband modem, which worked perfectly on 9.10. On 10.04, I have to plug it in AFTER booting, otherwise it's not detected at all.
So, enter 10.10. I download the final ISO, try to make a bootable USB pendrive like I always did for previous versions: now it doesn't work. I had to use a specially made version of unetbootin.
After successfully making the live-USB, it boots, but still has the horrible horizontal stripes. It must be something with the open nvidia driver, because it goes away when I install proprietary drivers; but WHY did it break, since it was working on 9.10?

After installing 10.10 on hard disk, and activating the restricted drivers for video card and wifi, the video is OK, but the wifi is totally inoperative. The Broadcom driver is enabled, but the wifi card's led won't light up, and no wifi network is found. Again, everything was working perfectly on previous versions, out of the box.
I also noticed a very ugly boot splash screen (text only), and weird text scrolling, with weird formatting, during bootup and shutdown. It's nothing important, but it wasn't happening before.
Any suggestion? Should I just wait for a fix (especially for wifi), skip this version altogether, or what else? :)

I've been using Ubuntu since 7.04 on 5 different computers. I had these problems on a HP Pavilion dv2736us laptop.

Thanks in advance,
Cristian

---

### Post by mörgæs on 2010-10-12
I didn't quite understand if you managed to get 10.04 work well on your computer, but if so then I would stick to this one. 

In general I would recommend only installing every other release of Ubuntu. 10.10 is not a revolution compared to 10.04.

---

### Post by Quaxo76 on 2010-10-12
Hi, Yes, 10.04 was very usable - at least wifi worked ok. The open nVidia driver has that horrible horizontal stripes problem, but after the actual installation I never used it anymore.
I wanted to install 10.10 because I like to have the latest versions of all the software applications, but of course if it's as unusable as it is now, I'll stick with 10.04, which I luckily preserved.

---

### Post by Quaxo76 on 2010-10-13
I just noticed that on 10.10 I can leave the USB modem plugged in at boot, and it is detected, as it was in 09.10. At least this regression has been fixed.
Today 10.10 updated the kernel, I hoped that would fix the Wifi problem, but no luck. :(

---

