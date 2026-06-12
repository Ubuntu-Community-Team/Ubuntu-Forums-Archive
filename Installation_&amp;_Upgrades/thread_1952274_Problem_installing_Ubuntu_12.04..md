---
title: "Problem installing Ubuntu 12.04."
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by B3RTLE on 2012-04-04
I used Wubi to install 11.10 but I was having problems getting the network card to work because I have Realtek 8113E ...I tried to fix(because I was told the problem was fixed in 12.04) it with an upgrade to 12.04 but then I had a black screen and nothing would work..

So I used Wubi to uninstall it ...I downloaded 12.04, put it on a CD, then used Wubi again to install 12.04, now I get an error that it cant find the .iso and windows refused to mount? ...I just used that drive to burn it to a disk, it works fine..

[http://i303.photobucket.com/albums/nn134/BES12000/Ubuntuerror.jpg](http://i303.photobucket.com/albums/nn134/BES12000/Ubuntuerror.jpg)

I would do a fresh install but I have Windows 8 64bit, Windows 7 64bit, and Vista 64bit.. 

But 11.10 installed perfectly ...why is 12.04 so messed up?

System specs:
CPU: AMD FX-8150
RAM: 12gigs DDR3 1600 
MB: GA-990FXA-UD5 (F7N Beta Bios)
Drives:
64GB PLEXTOR PX-64M2S SATA3 - SSD
1TB SAMSUNG HD103UJ SATA2 -  HDD
74GB WDC WD74 0GD-00FLA1 SATA1 - HDD
128GB PLEXTOR PX-128M2S SATA3 - SSD
1TB WDC WD10 EARS-00Y5B1 SATA3 - HDD <--- installed Ubuntu on a partition on that drive
120GB OCZ-REVOdrive RAID PCI-E x4 - SSD
TSSTcorp SH-B123L SATA - Blu-ray/DVD/CD ROM/Burner multi-drive

---

### Post by critin on 2012-04-04
[http://i303.photobucket.com/albums/n...buntuerror.jpg](http://i303.photobucket.com/albums/n...buntuerror.jpg)

Did you follow the instructions on the screen and shut Windows down properly, check disk and restart?

> why is 12.04 so messed up?

You do realize that 12.04 is still in Beta testing stage and hasn't officially been released for permanent installations--don't you?

---

### Post by B3RTLE on 2012-04-04
> **critin said:**
> [http://i303.photobucket.com/albums/n...buntuerror.jpg](http://i303.photobucket.com/albums/n...buntuerror.jpg)

Did you follow the instructions on the screen and shut Windows down properly, check disk and restart?

Yes, there is nothing wrong with the computer, scan of the CD and hard drives showed no errors, I never improperly shut down the computer..

The Blu-ray drive works fine..

Im not understanding why its not finding the .ISO ...I can find it plain as day if I explore the disk in windows..
Why is it not mounting a drive that 11.10 had no issues mounting?

> **critin said:**
> You do realize that 12.04 is still in Beta testing stage and hasn't officially been released for permanent installations--don't you?

Actually I assumed it would work fine since its supposed to be a "WORKING" Beta ...and several people claim it works fine with little effort..

---

### Post by zeljkojagust on 2012-04-04
```
But 11.10 installed perfectly ...why is 12.04 so messed up?

```Well, probably because it's still in Beta phase of development, didn't you think of that? And it will be unusable for real work until mid May probably (until some initial patching is done). And since you are using WUBI for installation... well I recommend you stick to last final release, that is 11.10 version.

---

### Post by critin on 2012-04-04
> Yes, there is nothing wrong with the computer, scan of the CD and hard  drives showed no errors, I never improperly shut down the computer..> 
Im not understanding why its not finding the .ISO ...I can find it plain as day if I explore the disk in windows..
Why is it not mounting a drive that 11.10 had no issues mounting?Because Windows was hibernated.  Sleeping.    

Also the last paragraph could apply to not properly ejecting the cd, bad boot because Windows couldn't mount while hibernated..  Several things.  Why not do as it suggests and see if works?

---

### Post by B3RTLE on 2012-04-04
Well I tried to fix it, ended up losing my Windows 7 install ..its completely gone...looks like Ubuntu made its home there instead of the drive I specified ... no its not user error either..

On the plus side 12.04 works perfectly....internet and all...

And Windows 8 runs 50X faster than Windows 7 anyway...

---

