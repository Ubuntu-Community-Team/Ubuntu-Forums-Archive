---
title: "USB drive tries to install on itself"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by JacKeown on 2010-06-07
Sooooo....My brother's computer that just randomly stopped booting into Linux Mint is now when trying to boot says something along the lines of "no bootable medium" or something and when I try to use a USB drive to install Ubuntu it tries to install onto itself instead of to the internal harddrive.

I don't have any Idea why it's doing this but if you could maybe tell me what you think is wrong or how to fix it I would appreciate it greatly....thanks

---

### Post by darkod on 2010-06-07
Boot ubuntu in live mode first and in terminal check if it can see the hdd at all with:

sudo fdisk -l (small L)

---

### Post by C.S.Cameron on 2010-06-07
You should be able to select where you want to install to during the install process.

---

### Post by JacKeown on 2010-06-08
Also when I type sudo fdisk -l in terminal it only shows dev/sda and dev/sda1.  I think that those are 2 partitions on my Flash drive and not my hard drive if I'm correct......???....if it helps I'm using unetbootin to put ubuntu on the flash drive

---

### Post by Bucky Ball on 2010-06-08
If it's a desktop might pay to check the hard drive cables. If you've done any work in the box you might have bumped one.

Choose 'Manual Install' and stick the OS where you want. Booting from Ubuntu, System->Administration->Partition Editor. That will show you everything that's there.

---

### Post by JacKeown on 2010-06-08
Something weird just happened......I went into the "Install Ubuntu 10.04" thing to install it and for the first time it showed the harddrive......I rebooted to see if I could get linux mint to work off of the internal harddrive and it started booting but stopped halfway and when I booted back into the ubuntu live disk flashdrive it no longer showed the harddrive.....what could this mean?

---

### Post by pricetech on 2010-06-08
> **JacKeown said:**
> .what could this mean?

That the hard drive is failing.  It wouldn't hurt to open the box up and check cables, as well as cleaning the dust out, but I suspect your drive is dying.

If you have any data on it you can't afford to lose, try putting it in a sealed plastic bag and putting in the freezer, then hook it up and hope for the best.

If you don't have data, just replace the drive.

Good luck with it.

---

### Post by JacKeown on 2010-07-08
Ok thanks! it was a failing drive and I sold it on craigslist....sketchy...

---

### Post by Bucky Ball on 2010-07-09
You sold a failing drive?

---

