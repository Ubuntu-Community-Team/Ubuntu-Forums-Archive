---
title: "Feisty hangs on install"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by TheSauce on 2007-05-22
I'm trying to install feisty server (or even desktop...they both hang at the same place).  I choose to install to hard disk and I change the boot options that it doesn't install quietly so I can see what's going on.  Both the server and desktop install both stop at the same place.  I have attached a picture of what I am seeing.  I wasn't sure if there is a way to log the whole installation so I had to resort to just taking a picture so all you see is what is on my screen.  If there is a way to log the whole installation to a file, let me know and I can do that if it will provide more info.

From the picture I know that the last item listed is my DVD/CD drive.  I just don't know if that's what it's hanging up on or if it's the next item that it's not listing that it's hanging up on.  Here is a list of the hardware in my computer:

Epox 8K3A+ mobo
Intel Pro/100+ NIC
SB Audigy 2 ZS sound card
GeForce FX 5900XT vid card
AMD Athlon XP 1800+ proc
250GB Maxtor drive
120GB Western Digital drive
200GB Western Digital drive
Samsung SH-S182D DVD/CD drive
1GB of RAM

Let me know if you have any ideas of what to try or need any more info.

Thanks
Sauce

---

### Post by TheSauce on 2007-05-22
OK, I have now ruled out the DVD/CD-ROM by putting in a different one and it stops at the exact same spot.  I also removed my sound card but it still stopped at the same spot.

One thing I didn't mention in my first post is that I also have a PCI Firewire card and PCI USB 2.0 card but I removed both of those and it still hung at the same spot.

Sauce

---

### Post by aztektum on 2007-05-22
bump

i got no clues. i will research

---

### Post by TheSauce on 2007-05-23
One more thing I forgot to mention.  I currently have Windows XP installed on the machine so this will be a dual-boot operation.  I don't think that is causing my problems because I'm not even getting to the installation part, but I figured I would throw that out there.  I have 40GB of unpartitioned space set aside for whenever I can get this working.

My next step is to remove all the hard drives and just leave the DVD/CD drive to see if it will at least get past the part it is getting stuck at.  I know I won't be able to install at that point but it might help narrow things down.  If anyone has any suggestions, please shoot them my way.

Sauce

---

### Post by wpshooter on 2007-05-23
Assuming that this is the DESKTOP (live CD) version, have you tried starting with the safe graphics mode parameter ?

---

### Post by TheSauce on 2007-05-23
I have tried with the live CD, the normal desktop install, and the server install and they all hang at the same spot.  I will try the safe graphics mode when I get home and let you know.

---

### Post by mavila on 2007-06-07
I was having similar hang issues - and it started about the time I added a 500GB SATA drive and a second DVD-ROM, a SH-S182D with firmware 01 on it. I have a SH-S162A installed and wanted to add another writer, so I grabbed one of the 182's without thinking too much about it. At any rate, Ive disconnected the 182 and I haven't had a lockup since (its been at least 5 hours now.... and I push the box pretty hard - lots of high speed document scanning and OCR work - the OCR in a VMWare windoze machine).

Looks like you setup is pretty similar to mine - Feisty, SH-S182D, SH-S162A, Nvidia 7900GS (dual head), beryl, 3GB RAM, 2.5TB disk and the rest of the usual goodies.

Take a peek at what firmware your drive has on it. there are several releases that Samsung has put out in teh last few months. As I havent tried them personally I cant say it will solve the issue - but I can see that NOT having it in my current config seems to have eradicated the issue.

---

