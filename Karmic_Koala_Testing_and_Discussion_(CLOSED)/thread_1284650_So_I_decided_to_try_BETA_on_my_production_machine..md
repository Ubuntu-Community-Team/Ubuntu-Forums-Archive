---
title: "So I decided to try BETA on my production machine."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by coldReactive on 2009-10-06
Well, guess what, I ran into problems right off the bat!

1. After installing, and quitting the installer, xsplash/whatever wouldn't show. After a green screen appeared, the screen went blank, then after a few seconds, my CD-Tray ejected. Still, nothing on screen. So I took out the CD and decided to hit Enter, nothing happened; and my keyboard numlock flashed its light every now and then. So I hit my trusty restart button on the front of my computer, at least that worked.

2. So, I finally booted into Ubuntu. Xsplash looked wonderful, but flicked every now and then for a few seconds before GDM/etc. came up.

3. After getting to the desktop, I decided to play an OGG. I forgot to turn off visualizations as per normal, so I went to do that while it was playing. I unchecked the display visualizations, and it stopped showing visualizations promptly. But, I couldn't close the settings window, and my music continued to play. So I had to force quit totem. Then, I opened totem again to play the same music, and needless to say, when I tried to close totem while it was playing, it had to force quit again.

So, now I'm waiting for apport to collect information. But it's been doing so for 25+ minutes. So now, I'm going to close that too :|

---

### Post by Regenweald on 2009-10-06
I have been using the entire testing cycle on my production machine. Had two showstoppers that needed live cd intervention, one understandably with the nouveau driver but it has been a good cycle all in all.

---

### Post by joshuapbell on 2009-10-06
> **coldReactive said:**
> Well, guess what, I ran into problems right off the bat!

1. After installing, and quitting the installer, xsplash/whatever wouldn't show. After a green screen appeared, the screen went blank, then after a few seconds, my CD-Tray ejected. Still, nothing on screen. So I took out the CD and decided to hit Enter, nothing happened; and my keyboard numlock flashed its light every now and then. So I hit my trusty restart button on the front of my computer, at least that worked.

2. So, I finally booted into Ubuntu. Xsplash looked wonderful, but flicked every now and then for a few seconds before GDM/etc. came up.

3. After getting to the desktop, I decided to play an OGG. I forgot to turn off visualizations as per normal, so I went to do that while it was playing. I unchecked the display visualizations, and it stopped showing visualizations promptly. But, I couldn't close the settings window, and my music continued to play. So I had to force quit totem. Then, I opened totem again to play the same music, and needless to say, when I tried to close totem while it was playing, it had to force quit again.

So, now I'm waiting for apport to collect information. But it's been doing so for 25+ minutes. So now, I'm going to close that too :|

umm... i suspect that it is these kinda of things that they tell you not to install beta software on production machines for...

---

### Post by coldReactive on 2009-10-06
> **joshuapbell said:**
> umm... i suspect that it is these kinda of things that they tell you not to install beta software on production machines for...

Hey, what if we like the thrill of something not going well? Sure, it may be frustrating, but bring it on :D

---

### Post by nhasian on 2009-10-06
maybe I'm misunderstanding.  did you say that you quit the installer before it completed?  Or did you allow the installation to complete?  also did you run the update-manager to get the latest updates?

finally, please post your system specs.

> **coldReactive said:**
> 1. After installing, and quitting the installer, xsplash/whatever wouldn't show.

---

### Post by coldReactive on 2009-10-06
> **nhasian said:**
> maybe I'm misunderstanding.  did you say that you quit the installer before it completed?  Or did you allow the installation to complete?  also did you run the update-manager to get the latest updates?

finally, please post your system specs.

No, it completed, and I ran update-manager after I was able to boot. I'll give you my system specs:

```
-Computer-
Processor		: 2x Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
Memory		: 6125MB (501MB used)
Operating System		: Ubuntu karmic (development branch)
User Name		: ian (ian)
Date/Time		: Tue 06 Oct 2009 09:10:57 PM CDT
-Display-
Resolution		: 1440x900 pixels
OpenGL Renderer		: GeForce GTS 250/PCI/SSE2
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA Intel
Audio Adapter		: USB-Audio - USB Device 0x2040
-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 HID 04d9:0461
 USB-compliant keyboard
 USB-compliant keyboard
 HDA Digital PCBeep
-Printers-
No printers found
-SCSI Disks-
ATA ST3500418AS
HL-DT-ST DVDRAM GH22LS50
SanDisk Cruzer
```

xsplash no longer flickers after installing the nvidia propietary drivers.

---

### Post by coldReactive on 2009-10-06
Also, Me TV will spit out this error when importing a channels.conf made by w-scan's new karmic version:

```
Failed to find a value for 'VSB_8'
```

gxine playlist icon is non-existant, and gxine will crash when using the same channels.conf. Run the following command to get a similar channels conf:

```
w_scan -c US -fa -X >> channels.conf
```

---

### Post by alexmurray on 2009-10-06
The totem hanging on exit (and needing to be force-quitted) is a known bug which should already be fixed with the latest update [https://launchpad.net/ubuntu/karmic/+source/totem/2.28.0-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/totem/2.28.0-0ubuntu2)

---

### Post by coldReactive on 2009-10-06
gxine gets stuck on this:

```
input_dvb: continuing in get_instance

```

when getting the channel from channels.conf.

Also, after,

```
sudo apt-get install totem-xine
```

running totem-xine from the run dialog or terminal gives a command/file not found error.

---

### Post by renkinjutsu on 2009-10-06
you can try ```
dpkg --listfiles totem-xine
``` to see what files were included with that deb.. and if it came with a /usr/bin/whatever

---

### Post by coldReactive on 2009-10-06
> **renkinjutsu said:**
> you can try ```
dpkg --listfiles totem-xine
``` to see what files were included with that deb.. and if it came with a /usr/bin/whatever

All that lists is the following:

```
/usr
/usr/share
/usr/share/doc
/usr/share/doc/totem-xine
/usr/share/doc/totem-xine/README
/usr/share/doc/totem-xine/TODO
/usr/share/doc/totem-xine/AUTHORS
/usr/share/doc/totem-xine/copyright
/usr/share/doc/totem-xine/NEWS.gz
/usr/share/doc/totem-xine/changelog.Debian.gz

```

Guess I'll be going back to Ubuntu 9.04.

---

### Post by coldReactive on 2009-10-07
Decided to test some more. See this empathy issue on the clean theme, time doesn't show if the name is too long (see attachment.)

Also, Empathy flashes/pulses a window on the window list on the current workspace rather than leaving it in its own workspace (Like pidgin), I wish there was a way to turn that off.

Also, Chat > Quit doesn't quit Empathy, it just minimizes the buddy list and whatnot.

---

### Post by Seventh Reign on 2009-10-07
If you want to install an Alpha/Beta system on a production machine, then you deserve all the bugs and crashes you get.  Period.

With extra HDD's being so cheap now (Less than $70 for 1 Terabyte!), its just easier to install an extra HDD and use that to test with.

---

### Post by coldReactive on 2009-10-07
> **Seventh Reign said:**
> If you want to install an Alpha/Beta system on a production machine, then you deserve all the bugs and crashes you get.  Period.

With extra HDD's being so cheap now (Less than $70 for 1 Terabyte!), its just easier to install an extra HDD and use that to test with.

Can you get a 70 USD one terabyte internal drive in a store rather than online? (IE: Best Buy)

Also, I'd have to spend more money on a new power supply too, which about 100+ USD for a 1000 Watt.

Another thing is that when I try to remove compiz, it wants to remove gnome-session. But I can't use compiz if I want to try gnome-shell.

---

### Post by Longinus00 on 2009-10-07
> **coldReactive said:**
> Can you get a 70 USD one terabyte internal drive in a store rather than online? (IE: Best Buy)

Also, I'd have to spend more money on a new power supply too, which about 100+ USD for a 1000 Watt.

Another thing is that when I try to remove compiz, it wants to remove gnome-session. But I can't use compiz if I want to try gnome-shell.

1. You'll not have much look getting a terabyte drive for 70 dollars at best buy.

2. Why in the world would you need a 1000 Watt power supply. The only reason computers require such crazy power supplies is if they are sporting crazy dual/triple graphics cards.

3. Use gnome-shell --replace or whatever. You shouldn't need to uninstall compiz.

Also, what does any of that do with installing beta software on a production machine? And now you want to test gnome-shell? That's even more beta than karmic.

---

### Post by coldReactive on 2009-10-07
> **Longinus00 said:**
> 2. Why in the world would you need a 1000 Watt power supply. The only reason computers require such crazy power supplies is if they are sporting crazy dual/triple graphics cards.

1. My 550 Watt AGI Power Supply isn't good enough to power an extra slot of RAM, as my GTS 250 nvidia card is being a monster, taking up most of the power.

2. If I want to upgrade my processor (max. Core 2 Quad 3.xx GHz, see point 3 below), I need to update my power supply to a bigger amount as well. My computer also has about 16 USB Slots, one of which is a TV Tuner USB Card, which takes a lot of power at times too.

3. If I want to upgrade to a core i7, I'll need to upgrade my whole motherboard, which may not have enough power with my 550 watt power supply.

---

### Post by ranch hand on 2009-10-07
You could do a lot of testing on a lot less than a Tb.

You should have plenty of power for another drive.

I would look for some thing in the 100Gb line, internal/external (doesn't matter) go cheap.

9.10 is not ready for production.  Kernal freeze is still a week out.  Final freeze at same time.

Should be quite a bit of updating going on untill then.  Then, after that rush, a whole week to work out bugs so that the RC is mostly good.

I am running on 475W power on this box (see sig) and am running four 320Gb drives.  Right now I am on Jaunty and running boinc that cranks all four cpus to 99 to 100% and it doesn't even slow it down much.

You really need to keep test crap off your main drive.  I turn mine off in bios when working on the testing stuff.

---

### Post by Longinus00 on 2009-10-08
> **coldReactive said:**
> 1. My 550 Watt AGI Power Supply isn't good enough to power an extra slot of RAM, as my GTS 250 nvidia card is being a monster, taking up most of the power.

2. If I want to upgrade my processor (max. Core 2 Quad 3.xx GHz, see point 3 below), I need to update my power supply to a bigger amount as well. My computer also has about 16 USB Slots, one of which is a TV Tuner USB Card, which takes a lot of power at times too.

3. If I want to upgrade to a core i7, I'll need to upgrade my whole motherboard, which may not have enough power with my 550 watt power supply.

1. 2. Don't be ridiculous, a stick of ram eats a watt or two of power at most. A GTS 250 doesn't eat very much power either. Hothardware's system with the following specs used ~150 Watts at idle and ~270 watts (measured at the wall so the computer uses less on the power supply side) under full GPU&CPU load.
> 
Core 2 Extreme QX9770 (3.2GHz)

Asus Striker II Extreme
(nForce 790i SLI Ultra chipset)

EVGA GeForce GTS 250 Superclocked

4096MB Corsair DDR3-1333 C7
(4 X 1GB)

Integrated Audio
Integrated Network

Western Digital "Raptor" 150GB

[http://hothardware.com/Articles/NVIDIA-GeForce-GTS-250-Mainstream-GPU/?page=3](http://hothardware.com/Articles/NVIDIA-GeForce-GTS-250-Mainstream-GPU/?page=3)
[http://hothardware.com/Articles/NVIDIA-GeForce-GTS-250-Mainstream-GPU/?page=8](http://hothardware.com/Articles/NVIDIA-GeForce-GTS-250-Mainstream-GPU/?page=8)

3. You definitely don't need more than 550W just to run a core only i7. You only need crazy power supplies if you're massively overclocking (as this reduces the power efficiency of the processor) and/or running crazy graphics cards. Anandtech's benchmark with a i7 975 used ~115W at idle and ~220W at full CPU load.

> 
Intel DX58SO (Intel X58)

Intel X25-M SSD (80GB)

Corsair DDR3-1333 4 x 1GB (7-7-7-20)

eVGA GeForce GTX 280

[http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3574&p=2](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3574&p=2)
[http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3574&p=8](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3574&p=8)

I want to add that putting too large a power supply is going to hurt the efficiency of your system. Power supplies aren't perfect and are most efficient across a range of efficiencies centered around 50% usage. In the previous hardware scenarios, hooking up a 1000W power supply would be a complete waste of money and would cost you more in electricity than a properly sized 400W-500W power supply.

Here is an example of the efficiency curve of a high quality 900W power supply that hits 89% efficiency. You'll note that it hits its stride only after 20% usage and 50% usage is where it is most efficient. The article is old and the hardware is perhaps out of date but the general concepts don't change.
[http://www.anandtech.com/casecoolingpsus/showdoc.aspx?i=3413&p=3](http://www.anandtech.com/casecoolingpsus/showdoc.aspx?i=3413&p=3)

---

### Post by bwallum on 2009-10-08
I use a 320GB usb external hard drive for testing, plugged in to my production machine. Installed the alpha on the usb drive and make it bootable. I then use the bios boot menu to select the drive to boot. My boot menu is accessed by pressing the F11 key, I've also seen other pcs use the F9 and F12 keys - and sometimes this isn't shown in either cmos or POST.

I have my home folder on its own internal drive.

This allows me to test on my hardware but keep a stable os for when I need to get some work done. You can also learn a lot playing with the alpha/beta and for me thats fun.

The usb hard drive takes 1 amp. 320GB cost me £50 delivered from [http://stores.shop.ebay.co.uk/HSUUK__W0QQ_armrsZ1](http://stores.shop.ebay.co.uk/HSUUK__W0QQ_armrsZ1) 
Get a bid on and you may get it cheaper.

---

### Post by tghe-retford on 2009-10-08
If you really want to keep your data, I would recommend a physically separate machine to test on which cannot get to your production machine and valued data.

It only takes one bug which wipes data from adjoining partitions/drives to make you appreciate the warnings you are given on not testing on a machine you rely on. Luckily I backed-up even though one or two recent bits were lost (not too important though), and could not be recovered.

I learned that lesson the hard way on Jaunty. :(

Here we go - at first the consensus was a potential hard disk failure, but I still am using the same drive now without any other problems: [http://ubuntuforums.org/showthread.php?t=1038371](http://ubuntuforums.org/showthread.php?t=1038371)

---

### Post by bwallum on 2009-10-09
I guess a completely seperate machine for testing is most secure and that if you disconnect it from any network it is more secure again. But you lose the full environment for testing. I don't mount my production system hard drive and I don't mount my home hard drive when I test. So what I get is a test environment on the hardware that I run fully exposed to networks.

A compromise I agree but more 'real' than an isolated test bench.

---

### Post by ranch hand on 2009-10-09
> **bwallum said:**
> I guess a completely seperate machine for testing is most secure and that if you disconnect it from any network it is more secure again. But you lose the full environment for testing. I don't mount my production system hard drive and I don't mount my home hard drive when I test. So what I get is a test environment on the hardware that I run fully exposed to networks.

A compromise I agree but more 'real' than an isolated test bench.
That is what I am doing.  I think that with Ubuntu it is safe.

When I am proven wrong I know who to blame too.   I really am the biggest security threat to my box.

---

### Post by bwallum on 2009-10-09
> **ranch hand said:**
> That is what I am doing.  I think that with Ubuntu it is safe.

When I am proven wrong I know who to blame too.   I really am the biggest security threat to my box.:) ditto but it's really good fun riding the %$*ger!

---

### Post by ranch hand on 2009-10-09
> **bwallum said:**
> :) ditto but it's really good fun riding the %$*ger!
Yup, although I think of it as riding rough stock in rough country.  Exciting, probably not to bright, FUN.

---

### Post by bwallum on 2009-10-09
> **ranch hand said:**
> Yup, although I think of it as riding rough stock in rough country.  Exciting, probably not to bright, FUN.

:lol:

---

