---
title: "Probelm Installing Lubuntu 11.04"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2011-05-24
Hi,

The problem is when I boot from the lubuntu CD & select **Try Lubuntu** or **Install Lubuntu** the computer hangs.

Xubuntu 10.04 was aready installed & I could easily boot to it. I thought may be some partition table error is causing that issue & I deleted all the existing partitions with Parted Magic Cd in Console Mode.

NB: When I tried to boot to the Parted Magic graphical session the PC hanged then too.

I am totally confused. Cant understand what is going wrong here.

I am now left with a broken system. :oops:

Please help.

---

### Post by Quackers on 2011-05-24
Why would you suspect a partition table problem?
What graphics card are you running and how much ram do you have please?

---

### Post by linuxyogi on 2011-05-24
> **Quackers said:**
> Why would you suspect a partition table problem?
What graphics card are you running and how much ram do you have please?

Yes, deleting the partition table was a wrong move. 

This is an old PC 

Celeron 2.13 Ghz

386 MB RAM

40 GB HDD

Graphics : Via IGP 32 MB

Ubuntu 10.04 was running slow so I decided to install Lubuntu.

---

### Post by ivanovnegro on 2011-05-24
Maybe try it with a new CD, maybe your ISO is corrupted, did you check the md5sum?

---

### Post by Quackers on 2011-05-24
From what I've read I think your specs should be ok for lubuntu to run. The graphics card could be a problem, possibly.
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Maybe you don't have it any more (lost it with xubuntu?).

You could also boot from the lubuntu live cd and at the first screen (purple?) press any key, then choose your language then on the next screen select the "check cd for errors" option.
If any errors are found then the disc is no good.

---

### Post by ronparent on 2011-05-24
Older computers often need additional boot options to boot successfully. A number (but not all) are discussed here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Good luck.

---

### Post by linuxyogi on 2011-05-24
> **ivanovnegro said:**
> Maybe try it with a new CD, maybe your ISO is corrupted, did you check the md5sum?

I tried with the following CDs Xubuntu 10.4, Ubuntu 10.04, Parted Magic.

By the way I have tested the Lubuntu CD on my other computer and it boots without any issues.

In desperation I tried all sorts of stuff, like I removed that Bios battery to see if resetting the bios helps but no joy.

Removed my DVD Burner which was connected to my new PC & connected it to the old one but nothing changed.

---

### Post by linuxyogi on 2011-05-24
> **ronparent said:**
> Older computers often need additional boot options to boot successfully. A number (but not all) are discussed here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Good luck.

Thanks for the link but the thing is now this PC wont boot from the Live Cds from which it used to boot without any issues.

Hardware Issue  ?

On the other hand, it was booting to 10.04 which was already installed until I deleted it on purpose.

---

### Post by Quackers on 2011-05-24
Maybe the cd drive has got a bit tired?

---

### Post by linuxyogi on 2011-05-24
> **Quackers said:**
> Maybe the cd drive has got a bit tired?

Removed my DVD Burner which was connected to my new PC & connected it to the old one but nothing changed.

Tried setting the Bios to Optimized Defaults ...but same thing.

---

### Post by ivanovnegro on 2011-05-24
Does not sound good. The CD drive could be really damaged.
I dont know if you could boot from a USB stick?

---

### Post by linuxyogi on 2011-05-25
The DVD Drive  was really in a bad shape.

The DVD Drive which I used next has a SATA interface. Now, although this motherboard has 4 SATA connectors it only supports 1.5 Mbps . I remember I had to set jumper on a SATA HDD to make it work.
But this DVD burner has no such jumpers.

I opened up the old DVD burner ..... cleaned the lens ..& now it at least it doesn't stall.

BUT

Still was not able to install Lubuntu 11.04, it stalls on screen "Preparing to install Lubuntu".

I had a Xubuntu 10.04 cd ...so installed it instead.

At lubuntu.net they say that Lubuntu can run with only 128 MB of Ram ...... I have 386 MB ...I wonder why it didn't work.

I have done the MD5 check on the Lubuntu iso ...it matches.

I have decided to keep Xubuntu 10.04 as long as this computer works. 

Thanks to all for your support.

---

