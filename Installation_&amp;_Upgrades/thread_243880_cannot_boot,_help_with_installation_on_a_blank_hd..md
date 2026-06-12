---
title: "cannot boot, help with installation on a blank hd."
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by fuxord22 on 2006-08-25
Hello,
This is my first time installing a linux distro so I will need some help. I read the guides but I am still having trouble. I have an old hp running at 850mhz and 369 mb ram with a totally blank hd, no OS or anything. First thing I do is insert the cd which came in the mail and restart. Nothing happens, just some text with "No operation system found". I checked my bios and everything was in order, cd was first. So I guess I need a boot cd, right? Ok, here is where I get slightly confused. 

I visit this forum: [http://www.linuxforums.org/](http://www.linuxforums.org/) and find this little program. [http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm).  I cut and paste the file into a floppy, insert, restart, nothing happens, so i did something wrong. So I am absolutely lost. I have no clue where to go from here; can someone please explain it to me in the simplest way possible? Thanks.

---

### Post by VirtuAlex on 2006-08-25
Either something wrong with your bios or with your cd. If you have some other bootable cd try to boot from it. If you have another computer, try to boot it from ubuntu cd...

---

### Post by adds2one on 2006-08-25
I agree, sounds like the problem is with your BIOS, your CD drive or your Ubuntu CD.

The Ubuntu CD is all you need. When you put the CD in your drive and reboot your computer should come up to a screen that gives you the option to load Ubuntu. 

Then Ubuntu should load and you can try it out. If you like it you just have to click on the Install icon on the desktop. 

Then you will be asked a few questions like your timezone. You can also cutomize the partitions on your drive if you like.

I reccomend 5 to 10 GB for your / partition, twice the amount of RAM you have for your swap partition and use the rest of your space for /home.

---

### Post by cleentrax on 2006-08-25
I would double-check your bios -- make sure you have selected CD/DVD 0, or whatever the first one is, as opposed to CD/DVD 2, or USB CD/DVD, etc.

If you have access to another computer, try booting the CD in that one to double-check that you have a working CD.

---

### Post by fuxord22 on 2006-08-25
cd is fine, checked on another pc. here is what my bios looks like...

Boot-time diagnostic screen [disable]

Quick boot mode [enable]


ATAPI CD-ROM
+Removable Device
	Legacy floopy drive
+Hard drive
	Bootable add-in cards
Network Boot


thats in correct booting order right? well if something is wrong with my bios, what can i do :-?

---

### Post by VirtuAlex on 2006-08-25
make sure you have latest bios
check with hp website

---

### Post by fuxord22 on 2006-08-25
i have an HP 8756C and i found an update for the bios at
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=us&dlc=en&os=54&product=58195&lang=en&softwareitem=pv502en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&cc=us&dlc=en&os=54&product=58195&lang=en&softwareitem=pv502en)

but how can i instal it if i dont have an os?

---

### Post by confused57 on 2006-08-25
Here's the wiki link for smart boot manager:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

You have to use rawrite to burn the sbootmgr.dsk as an "image" to the floppy disk.  You can't just copy the sbm file directly to the floppy.

You'd probably need another pc running Windows to copy the bios update to floppy in order to flash your bios on your old computer.  I don't think you'd need an OS in order to do this...maybe sbm will be all that you need to get the CD to boot.

---

### Post by randell6564 on 2006-08-25
The ubuntu cd is all that you need to boot, and install!

Something is wrong with your hardware if indeed you are setup to boot from CD first.

---

### Post by adds2one on 2006-08-25
> **fuxord22 said:**
> 

ATAPI CD-ROM
+Removable Device
	Legacy floopy drive
+Hard drive
	Bootable add-in cards
Network Boot




Looks to me like your boot order is wrong. If I interpret the '+' signs as the ones to boot from it looks like your CD-ROM is not included. Recheck your bios.

---

### Post by fuxord22 on 2006-08-26
OK, i got it, used a boot floppy..i actually wrote the image on a disk :) thanks for the help all of you

---

