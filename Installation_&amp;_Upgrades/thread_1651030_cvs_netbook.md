---
title: "cvs netbook"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by stinkster on 2010-12-22
I acquired one of these low priced arm8505 netbooks from cvs. figured ok lets put linux on the sd card and spent a few days looking into what distro, methods to do it and so on.
Not to many arm ported distros out there, found ubuntu and said ok, now we are cooking!

Ran into a few items trying to get it done and finally decided I better ask for some pointers.

Questions

Is the armel titled distros for arm8505 support? example ubuntu-netbook-10.10-netbook-armel+dove.img ?
This is the image I am trying to work with. I noticed the arm project seems to have gone threw a name change of sorts, has the naming of the releases also? 9.04 I think it was had arm in the image name. I am hoping to use the most current version is all.

I tried using the win32 diskimager tool described here hxxps://help.ubuntu.com/community/Installation/FromImgFiles to extract my downloaded image mentioned above to a 4 gig sd card. Placed the finished sd card into the netbook but it doesnt appear see it. I am figuring its one of three things. 1. not bootable, 2. wrong image, 3. something I did wrong, which could be a lot of things lol.

What I am hoping to do is get away from wince. Hoping to boot a live distro via sd card, try it out and if happy go onto formatting if need be the internal memory and do a full install.

Have seen several posts implying this netbook will work, mine seems to ignore the sd card and boot right into its pre loaded os. posting the basic specs below, cp from another site. have seen several vids on utube of it booting andriod etc, but I would rather have ubuntu knowing the background of its development.

Thanks for any input

**Common Colors:** Black, White, Green, Pink, Red
**Common CPU / Processor names: **VT8505, WM8505, VIA 8505, VIA ARM 8505
**MHZ:** 300MHZ
**RAM:** 128MB
**Storage:** 2GB NAND Flash
**Display:** 7.2" TFT
**Max Resolution:** 800x480
**SD Card:** All in one reader
**USB:** 3 x USB 2.0
**Audio:** Integrated Quadraphonic Speakers, Headphone/Line-Out 1/8" (3.5mm), Microphone/Line-In 1/8" (3.5mm)
**Networking:** Ethernet IEEE 802.11b,IEEE 802.11g / Wifi 802.11 b/g
**Power:** 110V Input, 9V DC Output, 2A
**Battery:** 1800mAH smart lithium-ion batteries
**Dimensions:** Length: 255mm x Width: 167mm x Depth: 38mm /  Length: 8.5" x Width: 5.75" x Depth: 1.25"

---

### Post by stinkster on 2010-12-23
bit of an update. I was finally able to get this thing to boot from the sd card. I reloaded a backup from online. seems the sd card must contain a folder named script. within that there is a autorun exe. That then execs a few other things and does the restore. nothing else will boot that I have tried. I am now wondering if the boot setup must see that folder and the autorun.exe.
If that is true,,, hmmmm.
maybe put grub in a folder named script, then a symlink from autorun to grub. dunno but I havent gave up yet.
 
one nice thing, the restore I did of wince is actually much nicer then the out of the box version lol, if thts even possible

---

### Post by ArcticChicken on 2010-12-23
Can you recount exactly how you set up your bootable SD card, and using which exact image?  I noticed the same netbook and had wondered if it'd run a Linux distribution of some sort, so I'd really be grateful if you can provide the details as to how you made it work!

---

### Post by stinkster on 2010-12-23
> **ArcticChicken said:**
> Can you recount exactly how you set up your bootable SD card, and using which exact image?  I noticed the same netbook and had wondered if it'd run a Linux distribution of some sort, so I'd really be grateful if you can provide the details as to how you made it work!

I can pm you a link to the files I used. basically its a winrar archive in a folder named script. weird part is, I had to do nothing to prep the sd card to make it bootable. I simply copied the unzipped archive to the sd card. when looking at the card it simply has 1 folder named script, with all the folders and files inside of that. I rebooted and it reflashed the rom.
I am thinking the bios or whatever boot device this thing is using is set to look for that folder and if it finds it execs the autorun.exe.
I checked the sd card, it is not set active. it simply has that folder on it, it is also fat format

---

### Post by ArcticChicken on 2010-12-24
What you found makes sense.  Take a look at the first 2 minutes of this video:

[http://armdevices.net/2010/07/05/canonical-explains-the-status-of-ubuntu-on-arm-powered-laptops/](http://armdevices.net/2010/07/05/canonical-explains-the-status-of-ubuntu-on-arm-powered-laptops/)

Jerone Young (Engineer at Canonical) makes the key point from between about 0:30 and 1:00.  In short, it's a big deal that you've verified the netbook you're using is checking -- by default -- for an SD card on startup, a FAT32 partition, and then a specific folder for bootable code.  ARM-based systems are not like x86 systems.  They're set at the factory to boot a certain way, and that's that.  There's typically no user-friendly, BIOS-like method for doing something as configurable as selecting an alternate boot sequence.

---

### Post by ArcticChicken on 2010-12-24
Have you taken a look through the following site?

[http://bento-linux.org/wiki](http://bento-linux.org/wiki)

Apparently it's seeded with information drawn primarily from this discussion:

[http://ubuntuforums.org/showthread.php?t=1349626&page=1](http://ubuntuforums.org/showthread.php?t=1349626&page=1)

---

### Post by stinkster on 2010-12-24
yes I had looked at that site, thats where I posted my specs from. They call it a bento book,,,, hxxp://bento-linux.org/wiki/wm8505-bento-linux/netbooks/bento-book-no-name
They also talked about booting a sd with a usb stick, I am assuming they are booting the sd to take advantage of the script folder then running the rest from the usb.
I also in several other sites found several people talking about how the hi/low leg on the sd slot has a resistor holding it low, as a result during boot the sd slot is read only. that if true would only need the resistor removed (I am not so sure I am sold on this being an issue).
Thanks for the info, seems we have both gone down some of the same paths in doing research. Now that I can restore the thing to wince I am thinking of using the internal flash. The restore files can be found for wince hxxp://forums.buyelectronicstore.com/forum-10-1.html in any thread related to restoring netbook.
If you get one of these units I would (I know its silly) download both the restore files they list in the forum above. It actually wasnt easy to find and who knows how much longer they will have the files posted being they are copyrighted by ms. cvs currently far as I know offers 0 support if you crash the unit, no downloads etc to restore.
I am still hoping to sym link or something out of the script folder to linux. Might even need a smal fat partition to start the boot.

---

### Post by stinkster on 2010-12-25
just found this site has a lot of info related. think this is the best info I have found so far on the unit. ps the wondermedia is the same unit as the cvs unit. arm8505 based  hxxp://devio.us/~nextvolume/via_arm/index.php

---

