---
title: "Fresh Install"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by nicketynick on 2007-05-25
I have an existing Dapper install (single-boot), that suddenly quit booting (Grub error 18 ), I suspect I may have a bad sector on my hard-drive.  If I try running a fresh install from the LiveCD, will it basically reformat the drive, and re-install, while avoiding writing to those bad sectors? What do I need to do?

Thanks.

---

### Post by coffeecat on 2007-05-25
I can't really answer your question with confidence. I don't fully understand these things, but it's odd that you are suddenly getting a Grub error 18.

From the Grub manual:

> 
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).Do you have a reason for saying that you suspect a bad sector? Did you know what error 18 meant?

I would have thought you would only get error 18 with a legacy BIOS and a newer hard drive. How old is your BIOS and how large is the hard drive?

I was under the impression that newer HDs dealt with any bad sectors, unlike in the days of MSDOS when you had to do something about it yourself.

---

### Post by nicketynick on 2007-05-25
> **coffeecat said:**
> I can't really answer your question with confidence. I don't fully understand these things, but it's odd that you are suddenly getting a Grub error 18.

From the Grub manual:

Do you have a reason for saying that you suspect a bad sector? Did you know what error 18 meant?

I would have thought you would only get error 18 with a legacy BIOS and a newer hard drive. How old is your BIOS and how large is the hard drive?

I was under the impression that newer HDs dealt with any bad sectors, unlike in the days of MSDOS when you had to do something about it yourself.

Yes, my first approach was to try to fix the Grub Error directly - the system was working fine, so its not exactly what it says, I think. The HD makes a repeated search sound (chk, chk, chk) when trying to boot. I tried re-installing Grub, wouldn't do it, just got the same noise.  Even will start making that noise while I'm running off a Live CD, although I am still able to access all the data on the drive via a terminal. I'm not sure how to troubleshoot the HD to see if its salvagable, so I thought I would just try a clean install and see what happens, but I don't want to write the boot to the same area again!
The BIOS is 2003, the HD 30GB, but as I said, it had been working, so I don't think that's the problem!
Things that work I can figure out, things that are broken......

---

### Post by nicketynick on 2007-05-25
Here is fdisk for the HD in the machine:
Disk /dev/hda: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 3495 28073556 83 Linux
/dev/hda2 3496 3647 1220940 5 Extended
/dev/hda5 3496 3647 1220908+ 82 Linux swap

Exactly the same as prior to the Grub Error 18 starting to show up. Not sure if this helps any......

---

### Post by coffeecat on 2007-05-25
Yes, I can see your line of thought. I'm sorry, but I don't have anything more constructive to offer. Let's hope someone else has. To be honest, if I was in your position, I would replace the drive. I don't know whether your budget stretches to this but in my case my time, my data and my stretched patience :wink: is more valuable than the cost of a new drive. HDs do fail. You haven't said how old this one is but a 30Gb one, if you'll forgive me for saying so, won't be a spring chicken. The fact that you get those seek noises with a live CD also sounds ominous to me.

---

### Post by nicketynick on 2007-05-25
Well, the good thing is I have no data on the drive - its an old IBM machine that I got just for playing around with Ubuntu!  I hear you on the time & patience issue! Trying a fresh install will be less painful than installing a new drive - I don't even want to think about BIOS and mobo limitations.... if the fresh install doesn't work, then a new drive it is.....

---

### Post by coffeecat on 2007-05-25
Best of luck.... :)

---

### Post by nicketynick on 2007-05-25
Anybody else care to comment?

---

