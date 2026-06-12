---
title: "System Freezes During Install of Dapper"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by skorpi0wn on 2006-09-25
I've been running Ubuntu as a file server in my home for a long time. This weekend, I decided to wipe everything out and install Dapper from scratch.  Unfortunately, I've been having problems with the install locking up the PC.

System Specs:
AMD Thunderbird 800mhz Processor on Asus Motherboard
300 watt P/S
1 x 512MB PC133
2 x 256MB PC133
1 x 40 GB Maxtor HD for O/S
2 x 300 GB Seagate HDs for file storage

I've never had a problem in the past so I guessed that some hardware might be failing.  

I first checked the hard drives.  I ran each manufacturer's HD check utilities which resulted in no problems.  I also used Drive Fitness Test (DFT) and had the same results.

I then checked the memory.  I used MemTest86 and Windows Memory Diagnostics. Both returned no errors.

I tried running PC Check on the MB/Processor but that program has never agreed with my system.

I started pulling out memory chips one by one and trying the install and the system still freezes.

I burned the latest Ubuntu Server CD on 3 different brand discs with various speeds.  All the same results.

The computer locks up at random times during install.  Sometimes when installing the files, sometimes when searching for hard drives, sometimes when trying to set the clock.

I do a LAMP install everytime (since I want a LAMP server).  I have tried with and without the ide=nodma

Any other ideas I can try/check?

Thanks in advance for any help.  It's most appreciated.

---

### Post by wpshooter on 2006-09-25
Are you running the integrity check on the Ubuntu install CD from the initial boot screen menu ?

If so and if it is passing the integrity check, my suggestion would be (assuming you don't have anything on your Maxtor drive that you need to keep) to download the Killdisk program from this site and WIPE that drive clean and then retry your installation.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by skorpi0wn on 2006-09-25
Thanks wpshooter.  I will test the CD's and try a clean wipe tonight when I get home from work.  I will post an update in here when finished.

---

### Post by The_Apprentice on 2006-09-25
I had the same problem when installing onto an AMD Athlon 1800.

The second time I tried it it worked no probs.

---

### Post by skorpi0wn on 2006-09-25
I checked the install CD and everything was fine.  I then used DBan (since I already had it burned to a CD) and wiped the drive clean. The install worked great!

I then did a dist-upgrade and started getting Kernel Panic problems!!

Well, I started over and tried one more time.  So far so good...

---

