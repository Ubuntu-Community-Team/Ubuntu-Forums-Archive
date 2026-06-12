---
title: "New HDD and New Server Install"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by kentish on 2011-04-20
Hi 

I was wondering if anyone could give me any suggestions or advice on the following. My server's main HDD is about to die according to the SMART information. I will be replacing it with a shiny new 1 TB drive which will hold my home directories and a a directory used ripping DVD's

Is it advisable to partition the drive into sections

10% for / 
60% for /home 
30% for /data - used for DVD ripping and encoding 

or just use the whole lot under / does it make a difference or is it just personal choice.


Just curious :-k


Mark

---

### Post by Hedgehog1 on 2011-04-21
> **kentish said:**
> Hi 

I was wondering if anyone could give me any suggestions or advice on the following. My server's main HDD is about to die according to the SMART information. I will be replacing it with a shiny new 1 TB drive which will hold my home directories and a a directory used ripping DVD's

Is it advisable to partition the drive into sections

10% for / 
60% for /home 
30% for /data - used for DVD ripping and encoding 

or just use the whole lot under / does it make a difference or is it just personal choice.


Just curious :-k


Mark

The main goal is to seperate the os from your data, so future upgrades can be loaded to the '/' partition and leave your personal data alone.

So the data in '/home' on it own partition is isolated during an install (or repair), as would your data in the '/data' partition.

I would lean toward 95% of the drive as '/home', with a /home/data directory for your movies & DVD work area. This allows the /home/data to grow without changing partition sizes if you guess the size wrong.

The other 5% (~48 gigs) for '/' & swap should be OK.

***The Hedge***

:KS

---

### Post by kentish on 2011-04-21
thanks for that advice.  I will partition the drive as you suggest.   cheers
kentish

---

### Post by dino99 on 2011-04-21
your needs:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

