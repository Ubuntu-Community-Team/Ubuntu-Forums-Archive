---
title: "noob help w/ bios update - Shuttle X50V2 Plus"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by spudchick on 2011-10-01
Hey all, 

I have some but not much experience with Ubuntu (much more with Win installation/upgrades). I've never had a hardware issue the couple of times I've installed Ubuntu (mostly on rehabbed systems I've tested and then given away). 

Have a Shuttle X50V2 Plus, a touchscreen all-in-one with  no optical drive. (It's going to get Eldy, for my mother-in-law.) Used Netbootin to install ubuntu-11.04-desktop-i386.iso, went fine, but got the "wireless is disabled by hardware switch" issue when I tried to connect. Just trying to update the bios right now, as by some reports it may help fix the wireless. 

So, I unzip the Shuttle bios update, and it's got two folders, DOS and WIN. No download option for an ISO or instructions on making one on the Shuttle site. I'm guessing I need to use the bios file in the DOS folder, but how? 

Contents of DOS folder:

AFUDOS.exe
FLASH.BAT
X50V3000.105

Thanks in advance,

spud

---

### Post by Frogs Hair on 2011-10-01
I have an Asus board that I just updated and they use three methods that I know of depending on the board . AFUDOS , Easy Flash , and another Windows software based updater . My board uses Easy Flash and I know that from the manual .

In my case I downloaded and extracted the bios , saved it to my external floppy which I plugged in prior to boot . I entered the bios screen at boot and followed the instructions in my manual . You could probably do something similar with a USB but you really need specific instructions for your computer .

---

### Post by spudchick on 2011-10-01
Thanks Frogs Hair.  

Lack of documentation has been a real problem with this model. This is a X50V2 Plus, which is different from an X50V2, but the mfr tag says just X50V2... and the two models take different ram (ddr3 204-pin for the plus, ddr2 200-pin for "non-plussed", which I found out the hard way).  And they advertise it as Windows or Linux compatible but they don't offer any Linux drivers/downloads. Still... it's a really sexy little unit and I can't wait to get it working. 

Wondered if I could uninstall Ubuntu, see if I can figure out how to install DOS just long enough to update the bios, and then reinstall Ubuntu.  Kind of a PIA but Shuttle doesn't have weekend support and I kinda want to get this rolling.

---

### Post by Frogs Hair on 2011-10-01
I would wait until Monday because bios updates can be a bit of a crap-shoot anyway . When I down loaded my bios it included the files required for the different types update procedures , but only uses file that is correct for the update method used .

---

### Post by spudchick on 2011-10-01
Well, as much as I had hoped Windows would never touch this little beauty, I had a Vista disc and installed that so I could update the bios, changed the wireless to always on (new option in the bios update) and reinstalled Natty.  Wireless installed and enabled fine second time around. 

Now I've got to figure out how to get Eldy installed and then hopefully get a good on-screen keyboard worked out. 

Thanks for answering this thread, even though I was too impatient to wait for a better answer.  I may still submit this Q to Shuttle to see what they say, since it would be nice to help others find a better way to do it.

---

