---
title: "Anyone in the Chicago Area wanna help me with Ubuntu?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by Dreadsen on 2010-01-13
Hello I have an Alienware Sentia 3450 and i want to do a clean brand new install on a new hard drive.  
I need the 64 bit version of Ubuntu installed but have been running into problems doing it. One the copies which i have burned on this 11 year old dell Latitude after i click what English for language and then click install it pretty much freezes there. 

I suspect the type of burner on my old Dell isn't burning the disk properly and this is why it's having problems. 
So if someone in the area can help me out i would gladly appreciate it. Or if someone wants to sell me a verified bootable copy of 9.10 amd 64 version. 

Thanks everyone!

---

### Post by presence1960 on 2010-01-13
what are your specs exactly? I looked up your model and there can be quite a bit of variance in specs.

---

### Post by Dreadsen on 2010-01-13
Intel Core Duo T7200 

2 gigs of ram

it had a seagate 100 gig but now has a seagate 250 gig hard drive. 

Is that enough for the specs or do you need more?

---

### Post by presence1960 on 2010-01-13
> **Dreadsen said:**
> Intel Core Duo T7200 

2 gigs of ram

it had a seagate 100 gig but now has a seagate 250 gig hard drive. 

Is that enough for the specs or do you need more?

That is plenty as far as specs go!

Back to the beginning now:

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning as an image to CD/USB? The hashes must match exactly- one character difference & the iso is no good.

Burn the iso as an image to CD at 4x-8x speed? Fast speeds are ok for burning data but not a bootable image.

Boot the Live CD and choose "check disk for defects" from the menu.

Here are some other things to take a look at: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If all else fails try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

Also don't rule out a faulty/dirty optical drive. Sometimes they may read data disks but have difficulty with a bootable image disk.

---

### Post by Dreadsen on 2010-01-13
Hey thanks man. i might hit you on Aim if it gets really tough. 

No i didn't do the MD5sum  i'll look into that now. 

But i also suspect that the drive i have on this dell doesn't support the type of burn that is needed. A few times i got an error suggesting that.

---

### Post by Dreadsen on 2010-01-13
man i just found out the checksums are different.

---

### Post by Dreadsen on 2010-01-13
So since the checksums are different does this mean that there must have been an error in the download and i must download it again?

---

### Post by presence1960 on 2010-01-13
> **Dreadsen said:**
> So since the checksums are different does this mean that there must have been an error in the download and i must download it again?

yes, since the iso is no good. If you can try using a torrent. But either way delete that iso since it is no good and try again.

---

### Post by Dreadsen on 2010-01-13
is a torrent better than the one on ubuntu's download page?

---

### Post by presence1960 on 2010-01-13
> **Dreadsen said:**
> is a torrent better than the one on ubuntu's download page?

a torrent is better because it downloads from a number of peers and it checks the hashes for you as it downloads.

---

### Post by Dreadsen on 2010-01-14
Okay i've verified the CD works. I even got an external CD Player and it does the same thing. no matter what selection i pick from the menu screen ( after i select English) it freezes. The CD drive is blinking but it will do that for over an hour. 

BUT if i try to pop the cd out it right away gives me the warning "Can't read boot CD click here to reboot".

---

