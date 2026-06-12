---
title: "Storage Data Loss on Partitioned Hard Drive"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by ADogg80 on 2008-08-07
I am running a windows-based system with 2 seperate hard drives. One is a 320GB and the other a 250GB. I have the 320gig partitioned for 120gb as the "C" drive and the other 200gb as the "E" drive which I use for storage only. When I was asked where to install ubuntu, I specified it to use my "G" drive (Which is the blank 250gb drive).  Installation went successfully, however when I went back into windows, my "E" drive was gone.

I'm probably not using the correct terminology for this, but does ubuntu un-partion hard drives?

I have yet to run Zero Assumption Recovery on the 320gig hard drive. I'm going to try that later.

Specs (Just in case it matters)
AMD Athlon 64 X2 4600+ Windsor 2.4GHz Socket AM2 89W Dual-Core Processor
NX7900GT-VT2D256E-HD GeForce 7900GT 256MB 256-bit GDDR3

Thanks for any help in advance,

ADogg

---

### Post by tamoneya on 2008-08-07
the correct wording would be repartition and yes it does.  It formats it in ext3 by default which works better in linux and is open source.

As to why it would touch "E" i am not sure.  It should have left that entire disk alone.

---

### Post by ADogg80 on 2008-08-08
Tamoneya ... thank you for the vernacular help :)

However in my noobie-goodness I accidentally used the wrong hard drive as my ubuntu partition. (Thank god I didn't use the other one or my windows would've gone bye-bye)

Since then I've tried to run ZAR 8.0 on the drive (but it hangs ... that's another problem for another website.)

The last thing I've done is gone to disk management in windows and simply deleted the two partitions that I created for ubuntu.  I haven't restarted my computer in fear that ubuntu may cause problems because it now has no partition.

Any suggestions now? :)

ADogg

---

### Post by tamoneya on 2008-08-08
my suggestion is that you use test disc.  It is available on the liveCD for ubuntu.  Please dont use the actual ubuntu install.  Put the liveCD in and run these commands in terminal:```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```

Then tell it to search the physical harddrive that has "E" on it.  Then when you find files transfer them to the physical harddrive that has "G" on it.

---

### Post by ADogg80 on 2008-08-09
Tamoneya ... thank you again for your help, it's greatly appreciated.

What I ended up doing was using the windows setup disk, using the recovery option, and typing "fixmbr" ... or something close to that.  I think that ubuntu is gone for good, once I get my files back from the "E" drive, I'm probably going to format it.

I may try linux again sometime, but it won't be until I have a better knowledge of things...

Thanks again!

ADogg

---

