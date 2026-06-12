---
title: "How to install from a non bootable USB/CD drive"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by nigel_bowers on 2011-04-02
Hello. I have an old IBM Thinkpad 240 that I'd like to try to install Linux on (preferably Ubuntu as that is what I have on other machines).

The one USB port cannot be used to bot from as it does not appear in the BIOS as a bootable device (it's about 10yrs old!). The CD drive is run from a PCMCIA slot so although accessible under Windows or a bootable DOS diskette, it cannot be used to boot a Linux CD from.

Does anybody have any ideas how I could install Linux in this situation? I was toying with the idea of removing the hard drive and starting the install by fitting the drive to a later machine that can boot from CD/USB but unfortunately the drive is an IDE and my later machines are all SATA. 

Does WUBI.EXE run from within Windows 98 as that could be an answer (install '98 via DOS and then run Wubi.exe from the Ubuntu CD after install of Windows) or is WUBI.EXE only run in 32bit mode?

All help much appreciated! Thanks.

---

### Post by JOHNNYG713 on 2011-04-02
I have In the past used a boot floppy disk, to install from an external CD ROM, Google Linux boot floppy disk, If you have a Floppy drive, wubi should work as well,  in W/98 !

---

### Post by Joe of loath on 2011-04-02
[http://www.cubainforme.de/loadlin.html](http://www.cubainforme.de/loadlin.html)

May be of interest. Bear in mind that a 10 year old machine probably won't be able to run Ubuntu at all, and even Lubuntu might be too heavy for it.

---

### Post by mörgæs on 2011-04-02
This is a little dated, but maybe it will give some ideas:
[http://www.rickandpatty.com/tp240.html](http://www.rickandpatty.com/tp240.html)

According to the link above, the machine has 192 MB of memory. I have an old Compaq with the same amount, and it runs Lubuntu well (but not Ubuntu).

---

### Post by nigel_bowers on 2011-04-04
Thanks for the replies. I do have a floppy drive and have looked for bootable linux floppies (there are many to choose from!) and will try that route.

I have an IDE to USB converter cable so I could copy the contents of a linux disto onto the harddive (by connecting it to another machine). If I were to do that and say dump the contents into a temp directory, what would be the command line (from a booted floppy) to run the installation?

I would do this with one hand tied behind my back if it were a Windows install but am still on a learning curve with my Linux escapades!

Thanks.

---

### Post by JOHNNYG713 on 2011-04-08
A boot floppy will look for any external boot-able iso and at that point will load as usual ! 
as far as a command, I haven't had to do this, as the boot floppy has always worked for me ! good luck my friend! hope you get'er up and runn'n :D

---

### Post by THGIC on 2011-04-08
> **nigel_bowers said:**
> Hello. I have an old IBM Thinkpad 240 that I'd like to try to install Linux on (preferably Ubuntu as that is what I have on other machines).

The one USB port cannot be used to bot from as it does not appear in the BIOS as a bootable device (it's about 10yrs old!). The CD drive is run from a PCMCIA slot so although accessible under Windows or a bootable DOS diskette, it cannot be used to boot a Linux CD from.

Does anybody have any ideas how I could install Linux in this situation? I was toying with the idea of removing the hard drive and starting the install by fitting the drive to a later machine that can boot from CD/USB but unfortunately the drive is an IDE and my later machines are all SATA. 

Does WUBI.EXE run from within Windows 98 as that could be an answer (install '98 via DOS and then run Wubi.exe from the Ubuntu CD after install of Windows) or is WUBI.EXE only run in 32bit mode?

All help much appreciated! Thanks.

If you wish to remove your HDD, you could use a HDD enclosure -- Best Buy carries one that is a RocketFish Hard Drive Enclosure Kit for IDE/PATA 3.5". You could jerry-rig it that way and connect it to a new PC via USB. In the case that you do so, you could use any kind of software that will allow you to edit the drive from a non-boot windows perspective. I would highly recommThe one USB port cannot be used to bot from as it does not appear in the BIOS as a bootable device (it's about 10yrs old!)end something called "Arconis". It will allow you to; wipe your drive, recover lost and/or deleted partitions, and clone the whole HDD as an image (.iso) -- your partitions will still be intact and so will the rest of your data. 

I had one other thought/concern that you stated earlier in this text, "The one USB port cannot be used to bot from as it does not appear in the BIOS as a bootable device (it's about 10yrs old!)." If a USB port is not showing in the BIOS as a boot-able device, that could mean one thing (that I thought of at lease); your Motherboard may be nearing the end of its life -- just a thought though. 

You can test it and see if your Motherboard is truly bad by one simple test; although, taking apart those ThinkPads were nothing to joke around about. So, if you are up to it, give this a whirl:

*Warning* Please remove the battery, AC Adapter, and all other peripherals, before continuing.

Re-seat the RAM in your IBM. If there is a door to your RAM, that is easy enough; otherwise, you need to remove the whole back panel, just to get to the RAM. Once you have done so, hold down the Power Button for 20 seconds (this will power-cycle your laptop -- it clears power settings, CMOS settings, etc). Now, plug in your AC Adapter again and turn on your IBM. 

Note: Look at the Power Activity Light: Is the light flashing (in a sequence; generally 3x intervals)? Listen for POST beeps: Did it POST beep at all (the computer tells you that you are missing RAM this way)? 

If the unit did any one of these two, your Motherboard is still good; however, if it did not, your Motherboard has a defect and can lead to more errors. 

Please check this out and post with results.

---

### Post by C.S.Cameron on 2011-04-08
Plop boot manager will let you boot either CD's or flash drives easily.

---

