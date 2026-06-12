---
title: "Installing and booting from SD card"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by maever on 2012-10-21
Hello folks!

So I have a little problem here, hoping some of you could help!

**The Story**

At home I run a small [Fit-PC2]("http://www.fit-pc.com/web/fit-pc/fit-pc2-specifications/") which I use as a basic webserver as well used as a centralized login location (with some host keys). In short nothing very I/O demanding, Now recently it's  2.5" harddisk broke, so it needs a new disk. It had a Mini-SD slot so I went ahead and got a 32GB micro SD and a micro-SD to Mini-SD converter, an SD card seemed like a way to go here.

My idea is to actually have this in as a permanent solution, so an ext4 filesystem would be favorable, however, the ubuntu installer does not detect the micro SD card as a disk.

The idea is to first see If I can even boot ubuntu from this SD card, So I went ahead and plugged the SD card into my windows 7 PC and used UnetBootin to prep a 12.04 Live CD on the SD card. (using a USB-converter).


**The Problem**

Now when I put in the SD card in the SD-slot of the fit-pc it DOES actually boot into the unetbootin screen after which i get the ubuntu 12.04 splash screen. Sadly, it does not go beyond the splash screen and the console displays:

```
stdin : error 0
unable to open '/dev/sda'

```

Where after it returns to initramfs
(unsure but perhaps the issue lies in the fact that de SD slot is called /dev/mmcblk0p1 whem USB-booting a live-CD)

Strange enough I can get the entire thing to boot just fine when I just use the same SD card and plug it in a USB-pen I have, I presume it's because the USB-pen has a small controller on it, Because the access times are also much slower (5 mb/s instead of  15 mb/s) then when using it as an SD card directly (tested this with hdparm).

**The Facts**

Now to lay down some facts to further assure that we're heading the right direction here.

[LIST]
[*]The Fit-PC2 bios supports SDHC and USB booting, as mentioned the initial boot works!
[*]I've tried multiple versions of Ubuntu, error 0 is always encountered
[*]System used to run Debian 6 without any additional drivers from its old harddrive
[*]The Fit-PC2 is connected to my home network using DHCP
[*]Fit-PC2 has 4 USB-2 ports, 1 miniSD slot, 1 HDMI connector and a 100mbit ethernet port.
[/LIST]

**The Question**

So basically I'm wondering if it is possible to have this installation running from the MiniSD slot?

Although finding a better USB-pen might offer the solution, it still feels like the "frankenstein solution" compared to using the nicely integrated SD card slot.

How would I best go about this?

---

### Post by offgridguy on 2012-10-21
I would get a new hard disk, external drives of any kind never seem to work as well as internal ones.

---

### Post by C.S.Cameron on 2012-10-21
Check the MD5SUM of your downloaded iso file.

---

### Post by darkod on 2012-10-21
In this situation I would also consider a Compact Flash card instead of SD/microSD card.

Actually there are SATA to CF and IDE to CF adapters with dimensions as 2.5" HDDs to make it simpler for you.

I don't know the flash memory details too deep, but I believe the CF card offers much more lifetime compared to SD. In small devices usually the CF is a HDD replacement.

---

### Post by maever on 2012-10-21
@offgridguy
I know a harddisk would be faster but seeing as this is a 24/7 machine, I'm interested in the cheapest solution

@C.S.Cameron
I think my first post pretty much rules this out 100%, tried multiple images + the fact that it WORKS when I use a USB-PEN SD card adapter.

@darkod
Already considered those, they are simply not an interesting solution price-wise + are based upon the IDE interface.
SSDs would make more sense in that case but are still a bit expensive and just don't even get close to the 15 euros I paid for this little SD card of 32GB (class 10+).
Also you can't tell me that running on SD cards isn't viable, there are [entire hardware concepts]("http://www.raspberrypi.org/") built upon SD cards as storage medium.

I would prefer a solution instead of a work-around.
Thanks for the reply though :)

---

### Post by Sylslay on 2012-10-21
Try get mini usb thumb like this:

Integral-16GB-Fusion-Flash-Drive

And please have a look here:

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

Install boot manager on any usb-thumb and try boot from SD - Partition.

PS. I have no better idea.

---

### Post by papiocinocephalus on 2012-11-23
Hi there

I have recently installed Ubuntu 12.04 on a SD Card 32Gigs Class 10 45Mb/sec (costs about EUR26 from Amazon) on a miniPC barebones. The previous SATA HD from which I was running the programme developed bad sectors as a result of overheating and I had to discard it.  The OS is running well from the SD card , have installed a number of plugins and some programmes and I still have 22Gigs. I plan to use an external HD to store bulky files, like pics and music. For my day to day documents I store on Dropbox.  Working like a charm and completely noiseless.  If you try to run the OS from a pendrive or external HD it tends to be slow and freezes repeatedly.

Hope this helps some

PC

---

