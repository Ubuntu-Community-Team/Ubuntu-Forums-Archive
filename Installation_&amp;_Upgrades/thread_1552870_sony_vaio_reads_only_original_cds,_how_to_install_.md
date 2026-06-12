---
title: "sony vaio reads only original cds, how to install ubuntu and remove xp?"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by AfrikaDietmar on 2010-08-14
hi,

i'm trying to install ubuntu on a sony vaio. Unfortunately i cannot boot from a cd on which i have burnt the .iso file of ubuntu. The only way i managed to install ubuntu was by creating a usb bootable stick, but here also that doesn't work so well. My workaround was to use virtual clone drive which is freeware to simulate a cd rom in windows and get the iso file started. By leaving the bootable usb stick in the computer in this way it worked...

So in the end i have grub and can load ubuntu and win xp, but then by trying to format the harddrive i kind of messed things up and had to reinstall windows. Because the DVD drive only reads original cds. So from there i will attemp to reinstall ubuntu again. But how can i get rid of win xp afterwards ? If that CD Rom would only read burnt cds or if it would habe been possible to boot from usb then i wouldn't have this trouble.

Any ideas ?

---

### Post by mörgæs on 2010-08-14
It sounds strange that the CD drive only wants original CD's. Have you verified that you burned the contents of the .ISO and not the .ISO itself to the CD? 

Does it work on other machines?

---

### Post by AfrikaDietmar on 2010-08-16
Hi,

yep, it only reads original cds. The .iso CD works on other machines. 
For example i can boot/install xp with an original CD, anything else doesn't.
It also doesn't read copies of anything.

What i did is the following. 
1. I formatted my harddrive and reinstalled WinXP.
2. Then i made a bootable USB stick with ubuntu on it, following the steps on ubuntus website at the download section.
3. Then i downloaded the windows file for installing ubuntu in linux.
4. I plug in the USB stick when winXP is active, and start the windows ubuntu loader/installer. It then sends me some error messages and i continually click on continue until it works - oh yes that works! - i mean the follow up steps.
I then choose that i cannot load ubuntu on boot up and it creates me a boot record for ubuntu with grub.
5. I restart the sony vaio and a test version of ubuntu can be loaded, usb stick stilled plugged in. In the test version of ubuntu i then install from the USB stick.
6. This time the partition program of ubuntu loads, so i could have now deleted win XP, but i left it just in case. But i made it into a very small partition.

Problem kind of solved, took around 2 days though :(

Still no idea whats wrong with the vaio cd/dvd rom drive for it to only read original cds ?
(I also inserted cds burnt on other machines.)

---

### Post by aessdana on 2010-08-16
hi,
First of all-how old is your drive?Is it optiarc (brand) product?From my experience i know that,when optical drive starts to behave like that it can mean that lens is worn out, and it will die pretty soon.Do you have that problem with dvd and cd discs?

---

### Post by AfrikaDietmar on 2010-08-17
Hi,

the laptop should be reaching its 4-5 years of use now. I'm going to change its battery, but not the drive, i'm assuming now that ubuntu is on it, its there to stay even with a dying drive, it will only has the purpose of office use.

The drive is a MAT_****_A UJ-840D... i mean a drive with that name c'ant be good for long right ? :lolflag: (i hope u don't mind my sense of humour) Even the forums filter is filtering out that middle word... so it must be really really bad :D (MAT_ S H I T _A UJ-840D)

---

