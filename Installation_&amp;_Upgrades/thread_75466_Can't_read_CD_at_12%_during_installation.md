---
title: "Can't read CD at 12% during installation"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Pumpino on 2005-10-13
I successfully installed Kubuntu 5.10 on my laptop last night.  No problems at all.  The md5sum was correct and the burnt CD passed Nero's verification check.

However, I've burnt the ISO onto three different types of media and my AMD64 machine will not install the same 32-bit version of Kubuntu.

In the early stages of the installation, it checks hardware, goes through the screen to check packages (/main/g/... or whatever it is), then on the next blue and red screen, it hangs on 12% every time, saying it can't retrieve a particular deb.  This is all well before it gets to the partitioning section.

How is this possible when I've burnt the ISO onto different brands of media, when it installed fine on my laptop?  Hardware failure?!

---

### Post by Storm Rider on 2005-10-13
Might just be that the lens on the cd or dvd reader doesn't like that type of media.

---

### Post by Pumpino on 2005-10-13
I don't think it's the media.  I've tried about 10 CDs now, and even copied it to my laptop using rsync and burnt it on that.  And remember, it installed fine on my laptop using the first CD I burnt!

Each time, it has trouble reading the CD at "Retrieving e2fsprogs-udeb..."

Any ideas... :(

EDIT:  I just tried it with acpi=off at the prompt, and then it had read errors, saying "Cannot retrieve md-modules..."

---

### Post by Pumpino on 2005-10-13
I just booted off my old 5.04 install CD to see what would happen.  It got stuck on "Retrieving e2fsprogs-udeb..." also!

So there's nothing wrong with the 5.10 CD.  What computer hardware or BIOS settings etc could cause CD-ROM read errors on a particular file?

---

### Post by jones_jj on 2005-10-14
I am just curious.  Have you tried downloading the 64 Bit version of Ubuntu and tried to install that on your AMD64 machine?

Also what machine did you use to burn the ISO?  Was it the 64 Bit machine in question or was it another?

---

### Post by Pumpino on 2005-10-14
No, I haven't tried the 64-bit version as there are always issue such as no macromedia flash or w32codecs.

I've burnt the CDs on both the AMD64 and my laptop.  The laptop runs any of the CDs fine, but the AMD64 will not install from any of them.

---

### Post by Pumpino on 2005-10-14
It's the BenQ 1640 DVD drive that's the problem.

I just borrowed an old LiteOn CD-ROM from my Dad, put in one of the CDs I'd burnt (with the BenQ drive) and it's rolling right through the installation now!

Perhaps the Ubuntu installation program is sensitive to newer DVD drives.  Have there been similar posts in these forums?  I thought I saw one earlier today, but can't remember where.  Damn, I've switched every cable in my computer looking for a hardware fault!

---

### Post by BungaMan on 2005-10-14
Well, have you tried flashing the BenQ with the latests firmware?

---

### Post by Pumpino on 2005-10-14
Yes, it was already running the latest firmware.  I even tried an older firmware version to see if that would work.  It didn't, so I flashed it back to the latest.

---

### Post by betty on 2005-10-16
I've got a BENQ 1640.  Same problem.  Does this mean we simply can't install ubuntu with this drive?

Also, I wonder if the problem is just with the installation.  If I switch out the drive with another one just for installation, and then put the benq back in, will I continue to have problems using the drive?  Anyone using the BENQ on an ubuntu installation.

My failure occurred with Ubuntu Breezy.  Also fails on Warty.

Thanks,
betty

---

### Post by BungaMan on 2005-10-27
betty, i think it should work fine to use a different drive and then after the installation is finished to use the same benq again..

it is either a problem that benq has with your type of cd (did you try different brands?) or it could be that somehow the linux driver is broken for it (but i'd doubt that).

pumpino,  since you have different computers i suggest you check out wiki on alternative installation methods without using your benq.

sorry for the late reply, kinda forgot this one :)

---

### Post by skskarda on 2005-10-31
I had a similar problem and enabled dma during expert installation.  

[http://www.ubuntuforums.org/showthread.php?t=82402](http://www.ubuntuforums.org/showthread.php?t=82402)

---

### Post by Panhead Bill on 2006-03-13
I have the same error, e2sprogs-udeb at 12%.  MB is a Asus K7V and the DVD R/W is a plextor.

---

