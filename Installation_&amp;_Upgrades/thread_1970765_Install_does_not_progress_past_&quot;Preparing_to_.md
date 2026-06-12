---
title: "Install does not progress past &quot;Preparing to Install&quot; screen"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Donalb on 2012-05-01
I checked the MD5 hash of the iso prior to burning and it was ok. 

Regardless of whether or not I choose MP3 or Install Software Updates on the Prepare to Install screen, there is no further progression. The spinning loading cursor will continue spinning and there will be no further access of the DVD.

If I boot into disk Live environment I'll first get an HP Driver notification for the printer, and immediately afterwards I'd get a Software Package problem with /usr/lib/i386-linux-gnu/colord/colord and ask me if I want to report.

Do this mean I possibly have a problem with the DVD (which I verified on burning)? Or any other ideas?

---

### Post by MonkeyPaw on 2012-05-01
Have you tried installing from a USB thumb drive? 

The only time I've had the installer hang is when configuring disk partitions, where I guess I gave it a combo it didn't like.

---

### Post by jadtech on 2012-05-01
first you could down load the ISO again make sure you select the right one for your processor if you have 64bit get the 64bit ISO if you have 32 bit get the 32bit ISO  if your HDD set up is raid get  the alternate ISO ..

you do the checksum after the burn because there is no way to know if they match before  ther is a program that needs to be down loaded and sum of the burn has to match sum of the ISO on the down load site..

burn the dvd at the slowest speed for the best results ..

if you have an older computer with low ram under a gig it might do you justice to get a copy of gparted and  make a small swap partition before booting the live cd  it will ease tight ram issues .. 

you could also  make bootable USB flash  drive

---

### Post by Donalb on 2012-05-02
I have sufficient RAM & space, used the correct ISO, lowest speed, etc. 

I haven't installed from USB so what the advantages of doing that over optical disk?

---

### Post by MonkeyPaw on 2012-05-02
I should be faster, for one. It saves you from having to use a blank CD/DVD. It might also be more reliable since a bad burn might produce mixed results. I guess it's one way to eliminate your optical drive as a problem.

---

### Post by Donalb on 2012-05-03
Tried it but no difference. Also burned a new disk, same result. No progression past Preparing to Install.

---

### Post by lawentzel on 2012-05-03
I am having the exact same issue. I've downloaded another copy "just in case". I've boot & nuked the hard drive to ensure previous version or the way the hard drive was partitioned did not effect the install. I had no problems with that previous LTS version. Just the latest one not installing. Booting from a thumb drive is not an option for me.

Thanks, Lee

---

### Post by MonkeyPaw on 2012-05-03
It makes me suspect that there is some sort of hardware issue going on. Either something is faulty or not compatible. Maybe a BIOS update would help? Seems unlikely that something is wrong with the installer, but you never know.

---

### Post by mips on 2012-05-03
Have you tried using the alternate text based installer from the DVD, I think the DVD offers both.

---

### Post by Donalb on 2012-05-07
Well, I've updated the BIOS to zero effect. haven't ever used the text based installer. What's the advantage of that?

---

### Post by lawentzel on 2012-05-07
Searched other posts along with the internet and found a solution that worked for me. That was downloading the "alternate" install disk. This resolved the install hanging up.

Hope this helps others.

---

### Post by Donalb on 2012-05-08
Indeed the Alternate disk also worked for me, though I used the Update Manager to go to 11.04 first.

---

### Post by mips on 2012-05-08
> **Donalb said:**
> Well, I've updated the BIOS to zero effect. haven't ever used the text based installer. What's the advantage of that?

It usually works where the ubiquity livecd installer fails. I only use alternate images for installation.

---

