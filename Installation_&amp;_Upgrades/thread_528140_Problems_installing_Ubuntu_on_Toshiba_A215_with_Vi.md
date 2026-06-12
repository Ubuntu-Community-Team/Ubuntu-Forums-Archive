---
title: "Problems installing Ubuntu on Toshiba A215 with Vista"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by geekGrrl on 2007-08-17
Hello,

I have been working on this problem for 3 days, and can't figure it out:

I created an Ubuntu boot disk (actually two after a while), did the checksums (everything matched), then tried to convince this machine to boot off CD.  No matter what I have tried, it does not recognize that I have a lovely little Ubuntu disk sitting in my D drive.  

I have tried disabling user accounts, limiting the security features, changing the setup on boot, going to select boot method on boot, various curses and incantations, all to no avail.  I have already shrunk the Vista drive to about 80 gig and have 78 gig available for Vista.

My machine is a Toshiba Satellite A215 with an AMD 64x2 processor, and it came pre-installed with the beast currently known as Vista.

Please help!  Vista is killing me slowly.

---

### Post by Pumalite on 2007-08-17
Make sure you burn iso as 'Image'.

---

### Post by merlinus on 2007-08-17
Have you tried booting from the ubuntu cds on another machine?

Asking this because if you have set up the BIOS to boot first from the cd drive, then perhaps for some reason the cds are not bootable.

And as Pumalite said, be sure you have burned the .iso files as disk images, not as data disks, and at no more than 4x.

-merlin

---

### Post by Pumalite on 2007-08-17
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by geekGrrl on 2007-08-17
Yes, I have an image disk.  I have two (32 bit and AMD), actually, neither of which work on my Vista machine.

The 32 bit runs on my old XP machine.  However, that one has an Intel processor, and I think that is the reason it will not run my AMD disk.  It does recognize there are Ubuntu files on it.  Vista seems to ignore the presence of any boot disks.

And thank you so much for your help!   This has been driving me nuts. =)

---

### Post by dabl on 2007-08-17
> **geekGrrl said:**
> 

 Vista seems to ignore the presence of any boot disks.



I think the vendor of your Toshiba carefully went in and set the BIOS so it won't boot anything from your CD ROM drive.  So you'll have to go in and change it back.  You may need to Google that model number to learn more about how to get into the BIOS/Setup.  Usually within a couple of seconds after initial power-up you see some kind of splash screen with a little message along the bottom like "Press F2 for Settings".  That's what you have to do, and you have to do it FAST, when the message is presented.

Then, once you're in BIOS, you are looking for the "boot device sequence", and you want to set it so the CD ROM drive is first in the sequence, and the hard drive is second.  Save the new BIOS setting, exit, and restart with the Ubuntu bootable CD in the drive, and you should be on your way.  :popcorn:

---

### Post by geekGrrl on 2007-08-17
Thank you so much.  I had actually done that as well, but wanted to check to make sure that I had before responding with that info.  When I did, I noticed that the CD/DVD listing had an exclamation point next to it.  D'oh!!!  Sure enough, when I just finally found a Windows 2000 boot disk and tried to boot from that, it did not recognize it either (so it's not some evil Toshiba-Microsoft conspiracy :) )

Thank you all so much for your help.  It would probably have been several more days before I popped back in there.

I'm going to go driver hunting, and hopefully installing the proper one will fix this problem.  

Thanks again!!!

---

### Post by dabl on 2007-08-17
It also would be worth the time to check whether there is a new BIOS firmware version for your chipset.  It should be on Toshiba's website, or at least a link to it should be there.  :)

---

### Post by kjg1981 on 2007-08-18
I just bought the toshiba satellite A215-S4807.  I was having the same problem.  A simple fix is to press F12 at boot up when you see the prompt at the bottom of the screen.  You can then choose to boot off the cd or the hd.   

I'm still having problems getting 7.04 running on my new machine though.  I had to install it with the alternate cd in text mode then update my x driver.  now unbuntu goes through all the loading process but  instead of loading the desktop i just get a black screen.    I think I might have selected the wrong resolution during the install.... Any help would be greatly appreciated

---

### Post by Pumalite on 2007-08-18
Ctrl+Alt+F1, or Alt+F1. At the command line: sudo dpkg-reconfigure xserver-xorg
At the end: startx

---

### Post by merlinus on 2007-08-18
Boot info Recovery Mode.

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

