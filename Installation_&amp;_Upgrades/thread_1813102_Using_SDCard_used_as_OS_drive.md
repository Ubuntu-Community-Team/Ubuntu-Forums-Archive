---
title: "Using SDCard used as OS drive?"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by Saidear on 2011-07-27
It's more a thought experiment at this moment than anything else.

[http://www.dealextreme.com/p/sdhc-sd-card-to-sata-solid-state-hard-drive-22597](http://www.dealextreme.com/p/sdhc-sd-card-to-sata-solid-state-hard-drive-22597)

Coupled with a Class 10 8GB SDHC card.

The goal is to run the computer (which is a headless server so there won't be much writing to the card after installation) from the SDCard, freeing up the remaining drives to function as just storage devices:
2x500GB in RAID 1 for Time Machine backups of my MBA.
1x1TB for movies
1x1TB for TvShows
1x500GB for Music

I know the sustained *write* speed of a C10 SDHC card is 10MB/s, which is slower than the 3GB/s SATA interface it will be on.  I can't get any figures on read speed, tho some averages for various manufacturers is up to 200x, which would be 2GB/s.. so not too bad.

Either way, is this possible/advisable for a server?  Or would I be better off just partitioning the Music drive into a 400GB / 100GB and using the smaller portion for Ubuntu? 

(As a side note, is an Intel Core 2 Duo@2Ghz enough oomph to handle RAID 1?  Or I am better off scrapping the whole idea and shelling out for a hardware RAID controller?)

---

### Post by oldfred on 2011-07-29
You can install Ubuntu to 8GB as I have a full install in a USB flash drive of 16GB with 8 for the install and 8 for data. Not speedy but functional.

Does your BIOS let you directly boot a SD card? If not it becomes a major work around to get it to work. Then I would just create 25GB system partition for booting on your hard drive. 

Some useful comments on large drives:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by C.S.Cameron on 2011-07-29
This SDHC to SATA card sounds slower than SDCC to USB.
I find running Ubuntu off USB a little slow but acceptable for what I use it for.
Puppy runs in RAM and might be better and faster for your purpose.
The only time I have heard of anyone burning out a flash drive booting Ubuntu was a fellow using (a cheap)one for a server.

---

