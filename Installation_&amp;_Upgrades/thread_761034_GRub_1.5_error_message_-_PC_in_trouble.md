---
title: "GRub 1.5 error message - PC in trouble"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Stingraynut on 2008-04-20
Hi, my PC refuses to boot and I get an error message "‘GRUB loading stage 1.5’
 
‘GRUB Loading, please wait’ 

- and no activity - nothing happens, I've waited up to 2 hours. 
 
Now if there's a CD in, I get the error message Primary IDE change no 80 conductor cable
If I put the boot disc in I get a floppy drive error message
 
If no discs, it goes v quickly to the GRUB message, as in the short vid - [http://www.robhealey.com.au/Vids/PC1.wmv]("http://www.robhealey.com.au/Vids/PC1.wmv")

There is no key I can press to interrupt the boot and get to DOS or anywhere.

Here's the sequence of events that lead me to this dilemma - I hope someone can give me some clues as to what to do next. Needless to say I have checked and rechecked all connections. I am convinced the hardware is OK and that it's a software glitch.

PC is a -
IBM Netvista  2194/18A 733mgh, 8 Years Old, Windows ME.
 
The PC began to run badly with symptoms of low memory. It would lock up and need re-booting, a  common thing after a period of use.

I suspected a virus and decided to use the recovery disc, which I've uses many times before and restores the PC to out of the box, with Windows ME. I don’t keep any data on the PC, it’s a 2nd PC that I use occasionally to check webpages I’ve built and to download software etc to check for virus’s before copying to my main PC.
 
The recovery disc installed windows in what looked like safe mode or reduced graphics mode, so I made a copy of the CD, to prove it was readable. The copy installed to the reduced graphics mode also. I then ran a surface scan of the HD and found a faulty sector. I removed the original HD and used a newer HD as the the single HD.

At this stage I thought perhaps there was a problem with the recovery disc so decided to try a linux OS, which I’ve always wanted to do. I got a copy of ubuntu which would run from a CD. I ran ubuntu from the disc, noticed the graphics res was normal, proving no problem with my sis graphics. In fact the program appeared to work perfectly but was very slow because it was running from the CD and not from the hard drive.
 
I tried to install ubuntu to the HD and it locked up at 15%. I switched off, switched back on and started the installation again - it stalled at 100%. I switched off, then back on - ubuntu didn't run - I forget what sort of screen I got, probably just black.

I gave up for the day. The next day I decided to give up on ubuntu and go back to the recovery disk because it was a known working thing and I know nothing at all about ubuntu.
 
I inserted the recovery disk and got a message that 2 partitions were in error and were being changed – I remember ubuntu re-partitioned the HD.

HERE'S WHERE THE CURRENT PROBLEM IS - from here on the system has got worse and worse. 
 
~~~ The recovery disk install continued after fixing the 2 partitions and got to the 'remove all disc' message. Normally at this point it restarts and all is done.
 
When it restarted I got an error 22 message
 
I restarted with the boot disc, got Dos and formatted drive C to clear it, intending then to start with the recovery disk again.
 
On restart I got this message
 
‘GRUB loading stage 1.5’
 
‘GRUB Loading, please wait’ - and no activity - nothing happens, I've waited up to 2 hours. 
 
Now if there's a disc in, I get the error message Primary IDE change no 80 conductor cable
If I put the boot disc in I get a floppy drive error message
 
If no discs it goes v quickly to the GRUB message, as in the short vid - [www.robhealey.com.au/Vids/PC1.wmv](www.robhealey.com.au/Vids/PC1.wmv)
 
SO............I think what I need to do is somehow restore the MBR which is where the GRUB thing resides - it's part of the Linux OS*format
 
How do I wipe it enough to be able to flash the bios or restore the basic start up stuff?(MBR)format

I should add that I don't speak any DOS or Linux, but can faithfully copy exactly what others write - which is how I re-formatted the drive.

There is no key I can press to interrupt the boot and get to DOS or anywhere - which makes repair very difficult!!

---

### Post by Pumalite on 2008-04-20
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_Loading_stage1.5_Read_Error](http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_Loading_stage1.5_Read_Error).

---

