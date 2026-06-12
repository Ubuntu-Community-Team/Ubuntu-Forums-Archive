---
title: "How to: 5 minutes to install Ubuntu"
date: 2008-12-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-12-14
I was getting tired of burning CDs every time I wanted to reinstall using latest daily build, so I decided to try using a USB Flash drive. It works perfectly and now I install Ubuntu in ~5 minutes and without needing to burn a CD and it's a lot easier to carry around than a CD.

Steps for doing this from Windows:

1. get a good USB Flash drive - they can vary enormously in performance so [do some research]("http://www.everythingusb.com/hardware/Storage/USB_Flash_Drives.htm")

2. format to FAT32 with [HP USB Disk Storage Format Tool]("http://files.extremeoverclocking.com/file.php?f=197")

3. burn ISO with [UNetbootin]("http://unetbootin.sourceforge.net/")

4. change HDD boot priority in BIOS so that USB is first (see your mobo manual for help on that)

5. reboot and install Ubuntu as usual - except it will be *much* faster than usual with a CD

Note: you can still store stuff on your bootable Ubuntu USB drive - just create extra folders as necessary.

---

### Post by plun on 2008-12-14
Yup... a USB Flash drive is just great !

gparted is a great tool for Linux and formats, also for FAT and FAT32

Packageinfo:
[http://packages.ubuntu.com/jaunty/gparted](http://packages.ubuntu.com/jaunty/gparted)

Screenshots with gparted in action:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Just be sure to be on right disk and partition...#-oO:)

---

### Post by Gina on 2008-12-14
I use gparted for all formatting and partitioning though I have been known to use the partitioner in the Ubuntu installer :lol:

I keep meaning to try USB installing. My AMD64 has USB boot opttion - other machines are too old.

---

### Post by ronacc on 2008-12-14
I used that to install ubuntu-eee to my eee after my usb dvd drive died . It is much faster , speed of install isn't really a concern to me though  since with Ubuntu you just answer a few questions and then wander off and do something else while the cd grinds away no constant interacting with the installer .

---

### Post by DavidONE on 2008-12-14
> **plun said:**
> 
gparted is a great tool for Linux and formats, also for FAT and FAT32

Just be sure to be on right disk and partition...#-oO:)

Thanks.  I should've mentioned that this is for anyone coming from Windows - I've updated the OP.

Heh - yes, I learnt the hard way to triple check you're about to wipe the correct drive.

---

### Post by DavidONE on 2008-12-14
ronacc,

I was as much concerned about wasting plastic for no good reason.  I occasionally left the Ubuntu install CDs I no longer needed around town - but don't know if they were used as install disk or frisbees. ;)

---

### Post by MaX on 2008-12-14
Why do I need to use HP USB Disk Storage Format Tool to format the USB drive? any particular reason?

---

### Post by plun on 2008-12-14
> **DavidONE said:**
> ronacc,

I was as much concerned about wasting plastic for no good reason.  I occasionally left the Ubuntu install CDs I no longer needed around town - but don't know if they were used as install disk or frisbees. ;)

Yup, So am I...  "Technotrash" :mad:

What do you want to do with your technotrash?
[http://www.greendisk.com/gdsite/Default.aspx](http://www.greendisk.com/gdsite/Default.aspx)

So burning CDs is something we must avoid, if possible...

USB-creator is another great tool.. "Made in Ubuntu"

---

### Post by DavidONE on 2008-12-14
MaX,

You may not. This was my first attempt at setting up a bootable Flash drive and I wasn't successful immediately.  One of the many articles I read suggested using the HP tool to format to FAT32.  I did and shortly after got everything working, although it may not have been necessary as my drive was already formated as FAT16.

---

### Post by DavidONE on 2008-12-14
> **plun said:**
> Yup, So am I...  "Technotrash" :mad:

What do you want to do with your technotrash?
[http://www.greendisk.com/gdsite/Default.aspx](http://www.greendisk.com/gdsite/Default.aspx)

So burning CDs is something we must avoid, if possible...

Absolutely.

We've got the [world's biggest rubbish dump]("http://www.independent.co.uk/environment/the-worlds-rubbish-dump-a-garbage-tip-that-stretches-from-hawaii-to-japan-778016.html") damaging the ecosystem. 

We're shipping off [mountains of toxic electronic waste]("http://en.epochtimes.com/n2/canada/recyclers-illegal-exporting-electrical-waste-7440.html") for [poor people to break down by hand]("http://news.bbc.co.uk/hi/english/static/in_depth/world/2002/disposable_planet/waste/chinese_workshop/").

Every little bit that we all do helps slow down the destruction.

---

### Post by philinux on 2008-12-15
I've been using cdrws for burning iso's. Only had one coaster in months. I think it must have been a manufacturing dud. And these are cheapo pc world own brand ones.

---

### Post by Gina on 2008-12-21
Just tried the USB stick.  Got the filesystem on there using UNetbootin - but it came up with a message saying it needed "z7zip-full" to be installed, which I did using Synaptic.  Then it worked.

Now to try installing on my AMD64 machine.

Later on AMD64...  No joy - doesn't work and the bios boot selection ssaid "No bootable device found"

Anyone have any suggestions please?

---

### Post by The Cokeaholics on 2008-12-21
What would be the minimal size requirement for installing to an SD card from another USB startup disk? I used a 2GB SD card in an EeePC but it failed enough writing space.

thanks, Robert

---

### Post by Gina on 2008-12-21
As I recall, Ubuntu needs about 3.5GB to install into.  Alternatively, you could install a CLI system and then add whatever apps you require.

---

### Post by Gina on 2008-12-21
> **Gina said:**
> Later on AMD64...  No joy - doesn't work and the bios boot selection said "No bootable device found"Found the reason for that.  Firstly I tried again with Intrepid and got the same result using F11 at startup to choose boot device and choosing "Removable" so I went to boot from hard drive.  I got the choice of my hard drive plus two USB devices - chose one of these and it booted (Intrepid Desktop version).  So with my AMD64 the USB memory stick is a ***hard drive*** not a ***removable drive*** :confused:

---

### Post by jfernyhough on 2008-12-21
I've been burning to a DVD+RW for a while now - 4x DVD burns in about two minutes with no formatting needed. It also reads much quicker than a CD-RW and I don't have to sacrifice my 8GB USB stick (for some reason I've ended up with three sticks: 128MB, 256MB and 8GB). :D

---

### Post by Gina on 2008-12-21
I think I'll be going back to DVD+RW - still having problems with the USB stick - can't get install to work.

I've got a 256MB and two 2GB ones - I'm using a 2GB one.

---

