---
title: "Moan of the day - The ibex promise and new theme"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-10-01
I have spent the last few weeks thinking about ibex's aims, all about pervasive internet access. If the developers hit the nail on the head my 3G modem should plug & go, my wireless card should function without ndiswrapper and the world should be a happy place.

Firstly, both I and a friend have 3G modems with different providors. I currently don't know how mine works because 3 have a hobby of cutting me off because I've overspent (apparently). This month I've spent £0.00 and been cut off for overspending again!!! However it does appear to connect then do nothing. Previously I had several profiles stored in wvdial.conf which provided the init strings for the modem and the password, access number etc for the service. Does anyone know how all this is determined if it's all plug & go? should I remove/rewrite my wvdial.conf? My friend's modem connects but pages won't load so I suspect all is not well.

Something which is driving me mad is that after spending a small fortune on a new laptop I still cannot access my wireless natively, as a result ndiswrapper cripples the card (no advanced featured) so I have to keep my old laptop around too. One of the things I love about linux is the fact that you know any bug or incompatability found will be plugged in due course, usually sooner rather than later, however this rather common device remains unsupported! My wireless is the Broadcom BCM4328, does anyone know of any plans for ibex to support it, or perhaps future plans to sort this issue out?

Finally, I'm not 100% sure of my thoughts on the new themes, after the Heron wallpaper which I loved I was rather expecting something equally eyecatching. Wallpaper aside the overall look remains very 'samey', when we were told it was getting a makeover I had hoped we'd see a more radical overhaul. I do wonder if one of the decoration managers for compiz could be made available 'out of the box' so that taking your 90's looking ubuntu desktop and turning it into a 2009 all singing, all dancing mac/vista busting work of art takes only a click instead of install this, configure that, etc.

All that said the only 'actual' problem with the new themes I have noticed is that in new wave if you take one of the taskbars and put them along the side of the screen, rather than top or bottom they look odd because the colour gradient remains upright, resulting in a tiled effect all down the bar.

Just some food for thought guys

---

### Post by Vaun on 2008-10-01
The BCM4328 works fine on Intrepid, just not as easily as it does on Hardy.  I had to blacklist the ssb module for it to pick up the wl driver.  Make sure you purge any installation of ndiswrapper first.

Try this first:

```
sudo rmmod ssb wl
```

```
sudo modprobe wl
```

If that works, add the following to make it permanent where you do not have to remove the ssb module everytime.

```
sudo gedit /etc/modprobe.d/blacklist
```

Add at the end:

```
blacklist ssb
```

```
sudo modprobe wl
```

You'll have to enter your wireless passcode upon each reboot, which is a presently reported bug.

---

### Post by macroshaft on 2008-10-01
A lifesaver!! I think I'm in love!

---

### Post by Vaun on 2008-10-01
As far as themes, there are many options out there. I agree the new wallpaper on Ibex is less then appealing. 

This is better (Dust w/Thorwil's background) than anything I've seen on OSX or Vista.

---

### Post by macroshaft on 2008-10-01
Now I'm intrigued, sure enough wireless is working but not 100% I read somewhere that ndiswrapper does not support all the features of a wireless card and as such aircrack will not run on it.

To be sure I've installed aircrack and it appears to enable the correct mode on the card but refuses to load, displaying an error.

> gareth@gareth-laptop:~$ sudo airmon-ng stop eth2
Could not locate any suitable fingerprints matched with available hardware.
[sudo] password for gareth: 



Interface	Chipset		Driver

eth2		UNKNOWN		wl (monitor mode disabled)

gareth@gareth-laptop:~$ sudo airmon-ng start eth2



Interface	Chipset		Driver

eth2		UNKNOWN		wl (monitor mode enabled)

gareth@gareth-laptop:~$ sudo airodump-ng eth2

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
Sysfs injection support was not found either.

I've looked at the pages for aircrack and they state this card is supported under the bcm43xx driver but this wl driver isn't mentioned on their site anywhere, any ideas?

---

### Post by Nico0020 on 2008-10-01
Can you give me a link to this theme, iconset and wallpaper. I am quite intrigued by this one.  Much more than new human.  I normally don't like dark themes, but this one looks interesting. 


> **Vaun said:**
> As far as themes, there are many options out there. I agree the new wallpaper on Ibex is less then appealing. 

This is better (Dust w/Thorwil's backgroud) than anything I've seen on OSX or Vista.

---

### Post by shafin on 2008-10-01
Here is the Link to the Theme:
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme)
And here is the link plus some more community themes, as a deb package:
[https://launchpad.net/ubuntu/intrepid/+source/community-themes/0.10](https://launchpad.net/ubuntu/intrepid/+source/community-themes/0.10)

I strongly suggest taking a look at the second link, as that contain two other fantastic themes also

---

### Post by aamukahvi on 2008-10-01
> **shafin said:**
> Here is the Link to the Theme:
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/DustTheme)
And here is the link plus some more community themes, as a deb package:
[https://launchpad.net/ubuntu/intrepid/+source/community-themes/0.10](https://launchpad.net/ubuntu/intrepid/+source/community-themes/0.10)

I strongly suggest taking a look at the second link, as that contain two other fantastic themes also

Or just install with synaptic
[apt://community-themes]("apt://community-themes")

---

### Post by gmclachl on 2008-10-01
> **Vaun said:**
> As far as themes, there are many options out there. I agree the new wallpaper on Ibex is less then appealing. 

This is better (Dust w/Thorwil's backgroud) than anything I've seen on OSX or Vista.


That is a really nice icon set. Which one is it?

---

### Post by Therion on 2008-10-01
> **Vaun said:**
> This is better (Dust w/Thorwil's backgroud)... 
Smashing theme!  Downloading that as I type this...

---

### Post by Ub1476 on 2008-10-01
Maybe you should complain to Broadcom. I think they are the only big wifi provider which yet hasn't open (or even released) native Linux drivers.

Put in some examples, like atheros which rencently released their drivers under a free license which means they can be included in the Linux kernel, and work out of the box for atheros users.

---

### Post by PRGUY85 on 2008-10-01
> **gmclachl said:**
> That is a really nice icon set. Which one is it?

As far as I'm concerned, Dust and New Wave both use the regular Human icon theme.  That iconset the user has looks like a modded version of Elementary.

---

### Post by macroshaft on 2008-10-01
> **Ub1476 said:**
> Maybe you should complain to Broadcom. I think they are the only big wifi provider which yet hasn't open (or even released) native Linux drivers.

Put in some examples, like atheros which rencently released their drivers under a free license which means they can be included in the Linux kernel, and work out of the box for atheros users.

Good idea, I think I'll just do that. The trouble is that I've bought three laptops in the past year and none of them has been any good, it would be nice to see some kind of 'linux certification' to say a product contains only/mainly linux compatable hardware, that would make shopping a LOT easier!

---

### Post by Vaun on 2008-10-01
The iconset is Elementary for New Wave pulled from bzr.  Although, I don't think it has been updated in sometime.  

```
bzr branch lp:~ubuntu-new-wave/anton/devel.icons
```

The background is from thorwil with rsc's ibex.  

```
bzr branch lp:~t-w-/ubuntu-artwork/thorwils_backgrounds
```

Dust version.

```
bzr branch lp:dusttheme/0.2
```

---

### Post by Sophont on 2008-10-01
Just do a bit of research before you buy hardware and buy only stuff that others have already used successfully.

I had wifi and Compiz working fine and mostly out-of-the box on my Laptop > 2 years ago. I just verified before I bought my Laptop if others had Ubuntu running on it. If there are problems I can make a decision whether they affect me or how quick I believe they will get fixed and base my decision what to buy on that.

Some helpful links (you can easily find more via your facourite seach engine):
[http://www.linux-laptop.net/]("http://www.linux-laptop.net/")
[https://wiki.ubuntu.com/HardwareSupport/]("https://wiki.ubuntu.com/HardwareSupport/")

Never buy hardware that is not supported on Linux one way or another.
If a gfew percent of the market do this then gradually hardware manufacturers will ever be more motivated to provide docs or even drivers for Linux.

---

### Post by adult swim on 2008-10-02
is there any advantage of using wl over ndiswrapper other than wl may take less work?

---

### Post by macroshaft on 2008-10-02
> **adult swim said:**
> is there any advantage of using wl over ndiswrapper other than wl may take less work?

I have no idea, but I just want my network card to work properly, with all it's features.

---

### Post by Ub1476 on 2008-10-02
> **macroshaft said:**
> Good idea, I think I'll just do that. The trouble is that I've bought three laptops in the past year and none of them has been any good, it would be nice to see some kind of 'linux certification' to say a product contains only/mainly linux compatable hardware, that would make shopping a LOT easier!

Well, I think almost everything works now except for Broadcom these days. I usually stick to intel though, which release open-source drivers so everything works out of the box. :D

---

### Post by gmclachl on 2008-10-02
> **Vaun said:**
> The iconset is Elementary for New Wave pulled from bzr.  Although, I don't think it has been updated in sometime.  

```
bzr branch lp:~ubuntu-new-wave/anton/devel.icons
```

The background is from thorwil with rsc's ibex.  

```
bzr branch lp:~t-w-/ubuntu-artwork/thorwils_backgrounds
```

Dust version.

```
bzr branch lp:dusttheme/0.2
```

Thanks everyone

---

### Post by Changturkey on 2008-10-02
So there is no new desktop?

---

### Post by macroshaft on 2008-10-02
> **Ub1476 said:**
> Maybe you should complain to Broadcom. I think they are the only big wifi provider which yet hasn't open (or even released) native Linux drivers.

Put in some examples, like atheros which rencently released their drivers under a free license which means they can be included in the Linux kernel, and work out of the box for atheros users.

I thought I'd share the wonderful response I received (instantly) from Broadcom...

> Broadcom is currently evaluating our support strategy for Linux users. As the chipset supplier, Broadcom provides Linux support to our customers - the manufacturers of wireless devices - that ultimately provide products to end customers, such as wireless LAN vendors, cable modem vendors, and notebook providers. It is up to these manufacturers to provide Linux client support to their end customers. Broadcom does not make a Linux client version available for end users at this time, however this may change in the future. In the meantime, please contact the manufacturer of your wireless device for Linux drivers. Linux support for certain products may also be available from Linuxant, and third party provider at [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

The link appears to be some sort of ndiswrapper style thingie!?

---

### Post by CarpKing on 2008-10-02
Linux Broadcom Drivers
[http://ubuntuforums.org/showthread.php?t=936341](http://ubuntuforums.org/showthread.php?t=936341)

---

### Post by macroshaft on 2008-10-02
> **CarpKing said:**
> Linux Broadcom Drivers
[http://ubuntuforums.org/showthread.php?t=936341](http://ubuntuforums.org/showthread.php?t=936341)

So why the hell would they develop drivers and hide them from the world?? That automated reply from Broadcom definitely suggests they don't have any!

Those drivers only mention 4 model numbers, mine is the 4328 but this only shows 4321 and 4322 in that range, do you think it'll work?

---

### Post by macroshaft on 2008-10-02
> **CarpKing said:**
> Linux Broadcom Drivers
[http://ubuntuforums.org/showthread.php?t=936341](http://ubuntuforums.org/showthread.php?t=936341)

Ok, scrap that, I found this in the readme for the drivers

> 3.  Insert the Broadcom wl module:                 insmod <path>/wl.ko

It's the wl driver I'm already using and it does not fully work. When loading aircrack this is displayed

> gareth@gareth-laptop:~$ sudo airmon-ng stop eth2
Could not locate any suitable fingerprints matched with available hardware.
[sudo] password for gareth: 



Interface	Chipset		Driver

eth2		UNKNOWN		wl (monitor mode disabled)

gareth@gareth-laptop:~$ sudo airmon-ng start eth2



Interface	Chipset		Driver

eth2		UNKNOWN		wl (monitor mode enabled)

gareth@gareth-laptop:~$ sudo airodump-ng eth2

ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth2 <#>'
Sysfs injection support was not found either.

---

