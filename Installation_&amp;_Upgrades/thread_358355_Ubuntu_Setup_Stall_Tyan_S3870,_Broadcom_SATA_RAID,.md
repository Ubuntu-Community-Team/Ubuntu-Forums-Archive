---
title: "Ubuntu Setup Stall: Tyan S3870, Broadcom SATA RAID, Serverworks HT1000"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by RockstarChampion on 2007-02-10
Hey all,

Trying to get a FRESH install of Ubuntu onto my new server, (Dual 2.4Ghz AMD64, 2Gb, (2) 400Gb Hard Drives, SATA II, Broadcom RAID) and i am able to get all the way through the installation until the most important part, COPYING the files to the drives.  I have no floppy drive in this box, just a CDROM.  I have done some research and found that using a hardware RAID configuration 'was' limited by the drivers for that specific RAID Controller.  

I am a newbie to Ubuntu and have limited knowledge on adapting to this issue.  I have found that there is a driver out there for the broadcom that some have used but after trying to get this through the Broadcom website, they send me to a page NOT FOUND, how convenient.

So my question is, is it possible YET to use the hardware RAID controller when doing an install of Ubuntu if i have the correct driver?

Here they have drivers for other Distros for my chipset: [[COLOR="Blue"]**TYAN LINUX DRIVERS**[/COLOR] ]("http://ftp.tyan.com/support/html/drivers_linux.html")

Second, if i have this correct driver and placed it on the boot CDROM where do i need to put it for it to be found in the "Detect Disks" setup screen so i can choose it?  I see that there are other SATA controller drivers there but don't see anything related to Broadcom.  Is it possible for me to run a command before i run the Ubuntu install to get the drivers loaded, if so, where, how.

Really, this is quite rediculous to have TWO large company sites whos links you find in Google that have Page not found Tyan and Broadcom

Serial ATA Driver update: [[COLOR="Blue"]**http://linux-ata.org/driver-status.html#frodo**[/COLOR]]("http://linux-ata.org/driver-status.html#frodo")

My Serverworks Broadcom RAID CONTROLLER: [[COLOR="Blue"]**MY BROADCOM RAID CONTROLLER**[/COLOR]]("http://www.broadcom.com/products/Enterprise-Networking/SystemI-O-Products/BCM5770R")


Broadcoms Invalid RAID DRIVER PAGE
[[COLOR="Blue"]**http://www.broadcom.com/products/raid_driver_download.php**[/COLOR]]("http://www.broadcom.com/products/raid_driver_download.php")


Tyan Invalid Linux Drivers PAGE
[[COLOR="Blue"]**http://www.tyan.com/support/html/drivers_linux.html**[/COLOR]]("http://www.tyan.com/support/html/drivers_linux.html")


So is it possible to use a driver for another Distro?  What options do i have outside of the known which would be to use Linux Software RAID setup.

I see there may be options but my knowledge about linux is nothing to most of you out there so any help would be appreciated.

---

### Post by DinoSaw on 2007-03-14
RockstarChampion, did you get anywhere with this? I am having the exact same problem on a supermicro H8SSL that uses the HT1000 disk controller.

I had the same results as yourself re finding a driver, however I did speak to Supermicro who told me that they can supply the source code if I wanted to build the driver myself. Unfortunately I dont have any real idea how to do this, any one out there who knows how or wants to have a go, I can try to get the source to you

As far as I know only Suse and Redhat (not even FC) support the HT1000, and I have not seen any real interest from Tyan or Broadcom to develope drivers for other distros.

Still looking will post any good news!

---

