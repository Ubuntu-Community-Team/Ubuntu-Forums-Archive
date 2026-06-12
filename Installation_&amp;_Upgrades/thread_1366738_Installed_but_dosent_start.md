---
title: "Installed but dosent start"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by Urhungry on 2009-12-28
So I managed to get xubuntu installed, but when I start, it gives me an error. I don't know what to type to solve this problem. Here's the code that appears:
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/4c0c1fad-bd9a-45ff-9493-cd797364e184 does not exist. Dr
opping to a shell!

Busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

I'm using xubuntu version 8.04. Thanks!

---

### Post by presence1960 on 2009-12-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Urhungry on 2009-12-28
I can't boot at all, I just shows this when I try. Sorry if I'm getting something wrong here, I'm new to all this.

---

### Post by Urhungry on 2009-12-28
Oh wait I think that I get what your saying. I'll try it right now.

---

### Post by Urhungry on 2009-12-28
It just freezes up when I try to boot from cd. I get as far as selection. I only managed to install because I seleced an option on the program that launches on the windows desktop.

---

### Post by presence1960 on 2009-12-28
what are the specs of your machine? what video card do you have?

---

### Post by Urhungry on 2009-12-28
It's a Dell latitude c600, I don't know how to find the video card, as it no longer has windows, and can't boot into xubuntu. Sorry for not knowing anything, I'm very new to this.

---

### Post by presence1960 on 2009-12-28
> **Urhungry said:**
> It's a Dell latitude c600, I don't know how to find the video card, as it no longer has windows, and can't boot into xubuntu. Sorry for not knowing anything, I'm very new to this.

Dell Latitude C600
PC WorldBench 2000 score of 164, Pentium III-750/600 CPU, **_128MB of SDRAM_**, 256KB L2 cache, Windows 2000 Professional, 14.1-inch active-matrix screen, **_ATI Rage Mobility 128 graphics chip with 8MB of SGRAM_**, 10GB hard drive, 10X-24X CD-ROM drive, combination V.90 modem and ethernet PC Card, built-in network adapter, touchpad and eraserhead pointing devices, 7.8 pounds (including AC adapter and external floppy drive and cable). Three-year parts and labor warranty; free, unlimited 24-hour toll-free tech support.

You don't have enough RAM to run the Live CD. You want to use the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

See here though: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Even if the alternate text based installer successfully installs Xubuntu it may not run well as the bare minimum recommended RAM is 192 GB.

You may want to look into alternative lightweight distros.

---

### Post by Urhungry on 2009-12-29
It's been modified a bit, so that it has 255 megabytes of ram. The installer says that it need 256, but I don't know if 1 megabyte of ram really make a difference.

---

### Post by presence1960 on 2009-12-29
> **Urhungry said:**
> It's been modified a bit, so that it has 255 megabytes of ram. The installer says that it need 256, but I don't know if 1 megabyte of ram really make a difference.

I would try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

I think it will make a difference because your video card only has 8 MB of it's own RAM, so some of that 255 MB is being allocated to video resources. That will leave you with less than 255 MB.

---

### Post by peyre on 2009-12-29
The alternate install CD is worth a try, but I don't know if it'll make a difference.  I'm having similar trouble with an old laptop myself (an HP Pavilion ze4125).  I tried the alternate install CD last night and it worked no better than the regular install CD.  I suspect there's an issue with the video card (I think mine is also an ATI).

---

### Post by presence1960 on 2009-12-29
> **peyre said:**
> The alternate install CD is worth a try, but I don't know if it'll make a difference.  I'm having similar trouble with an old laptop myself (an HP Pavilion ze4125).  I tried the alternate install CD last night and it worked no better than the regular install CD.  I suspect there's an issue with the video card (I think mine is also an ATI).

If you have reason to believe the vid card is the issue with installing and you have at least 384 MB RAM boot the Live Cd and at the menu hit F4 and choose safe graphics mode.

For more info on this and other Boot Options see [here]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Urhungry on 2009-12-29
Oh, sorry, I have never changed an os before, so I don't know this sort of thing. Is there anything I need to know, code wise, to complete the text based installation? 
Edit: I didn't see the last three posts, how would safe graphics mode help?

---

### Post by peyre on 2009-12-29
> **Urhungry said:**
> I didn't see the last three posts, how would safe graphics mode help?
Safe graphics mode uses very basic, generic graphics, if I understand right.  Basically it doesn't do anything fancy and doesn't try to take advantage of the full features of your graphics card--it only uses enough to get a bare-bones, no-nonsense session of X running.  Windows has an equivalent.

---

### Post by Urhungry on 2009-12-29
Oh, ok, I should probably try that then.

---

### Post by Urhungry on 2009-12-29
I tried reinstalling it with safe graphics mode on, and it installed and booted, so I guess my problem is solved. The only remaining issue is that it won't recognize my eathernet plug when I plug it in. Any help here? Thanks.

---

### Post by peyre on 2009-12-29
I assume it's a built-in network card?  Have you tried starting the computer with the cable plugged in?  That might make a difference.

---

### Post by Urhungry on 2009-12-29
Ok I will.

---

### Post by Urhungry on 2009-12-29
Nope, still dosent work. Do you know if a wireless card would work, and if so, where to get one? Mine broke about a year ago.

---

### Post by peyre on 2009-12-29
You can get WiFi cards, sure.  They come in PC-Card, PC-Express, and USB form factors.  I have one myself, for my laptop.  The tricky part with those is to make sure it'll work in Linux, though, in my experience.  That experience is very limited, but I found that while everything else on my old laptop worked in Xubuntu, the WiFi card didn't install.

If you're looking to get your hands on one, though, you should be able to pick one up fairly inexpensively on Craigslist or eBay.  Failing that, you should be able to get one on Amazon or any other online retailer.  And if all else fails getting it to install with Linux drivers, you can always try to use the Windows drivers:

[http://www.bauer-power.net/2007/09/using-windows-drivers-in-linux.html]("http://www.bauer-power.net/2007/09/using-windows-drivers-in-linux.html")

---

### Post by presence1960 on 2009-12-29
> **Urhungry said:**
> Nope, still dosent work. Do you know if a wireless card would work, and if so, where to get one? Mine broke about a year ago.

check [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") before you buy. You may want to get one that you know for sure will work with ubuntu

---

### Post by Urhungry on 2009-12-30
Ok, thanks. Does any chip fit in any computer? I normallly use a desktop with a built in wifi card, so I don't know this stuff.

---

