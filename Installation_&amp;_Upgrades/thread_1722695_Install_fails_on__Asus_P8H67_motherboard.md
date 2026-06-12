---
title: "Install fails on  Asus P8H67 motherboard"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by Wildroser on 2011-04-06
Hi,
I just assembled a new computer with Intel Core I3 processor and Asus P8H67 motherboard and 4 MB of memory. It has a 2TB Hitachi Deskstar Hard Drive and Asus DVD. I am trying to load Ubuntu 10.10 directly (without first loading Windows) without success. 
 
I have tried 4 separate downloads of Ubuntu - 64 bit, 32 bit with Desktop and Alternative. I have changed a variety of parameters and various tricks suggested on other threads. The Desktop (32 and 64) versions get me to Busybox shell with message (Initramfs) Unable to find a medium using live file system. The Alternative version hangs with the messages: 
RAMDISK: Couldn't find valid RAM image startgin at 0; 
No filesystem could mount root, tried ext3, ext2, ext4, fuseblk; 
Kernal panic - not syncing VHS; 
Unable to mount root fs on unkown block(1,0). 
 
For parameters I think have tried them all (but not in all combinations). I tried exiting twice from BusyBox as suggested on forums but that just hangs the system. I also turn off the quiet and splash to try and see what is going on....but it is too complex and goes to fast for me to follow. 
 
A final suggestion was that the P8H67 is too new for Ubuntu 10.10 and to try the new version 11 coming out...I am new to Linux and reluctant to try a Beta. 
 
thanks for any help on this....

---

### Post by dazman19 on 2011-04-06
> A final suggestion was that the P8H67 is too new for Ubuntu 10.10 and to try the new version 11 coming out...I am new to Linux and reluctant to try a Beta. 

No. 10.10 should be fine.

I would suggest plugging the hard drive into a different SATA port. There is a problem with some of the new sandy bridge motherboards, and it affects the SATA drive controllers, it may or may not affect your board, but it sounds like the OS cant mount the drive. If you can run the live CD then its probably a problem with the disk more than anything. Can you install anything else onto this disk? It sounds like after trying 4 different distribution images that it is something to do with the disk. 

I have a sandy bridge core i7 on a similar chipset ASUS board but i dont suffer the same problem. 

If indeed you do have a faulty SATA controller the manufacturers are offering replacements. Contact the company which sold you the product.

---

### Post by Wildroser on 2011-04-06
I tried unplugging the hard drive - no change.  To test my hardware I created a Windows boot from my laptop.   Windows loaded and runs on the P8H76.    I re-tried Ubuntu 10.10 after loadiing windows (thinking with a partitioned disk Linux would work) but got same old problem - dumped into (initramfs). 
 
We know
Assembled computer with P8H76 hardware is ok (Windows runs)
CD is ok- I ran it on my laptop and Ubuntu 10.10 live works fine
P8H76 + Ubuntu10.10 is causing grief...
 
I must be still missing something in this mystery... ideas?
 
Thanks in advance ... this one is knotty...

---

### Post by Wildroser on 2011-04-09
I got it working - more by good luck than good thinking.    I think the key to a workaround is described in [Bug # 143958]("https://answers.launchpad.net/bugs/143958")  where one has to figure out a way to mount the CD-ROM or get it  recognized somehow.   I could not use the "(initramfs) mount /dev/scd0   /cdrom"  and then "exit" suggested in the bug fix because although I had /cdrom I did not have  /scd0 in /dev.    I did have sg0, sda, and sda1-3 as described in the bug fix but did not try  mounting them as I was unsure what they were.
 It ended up I had an external cdrom which I hooked into the USB and  everything loaded fine.    Like I said - more by good luck than good  thinking.... but I think an expert on the BusyBox code could have  figured out how to get through it.

---

