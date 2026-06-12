---
title: "No further progress than first 2 screens of 10.10 usb live disk installer"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by MOB_Figga on 2010-12-03
this is the hardware:

-zotac HD-ID11 barebone  (which has a Intel Atom D510 dual-core CPU and next gen nvidia Ion graphics chip) with:
 1. 4gb RAM
 2. OCZ Vertex 2 60gb SSD



the problem:

I created a USB startup disk with 10.10 64 bits ISO on it (so that's the amd64 10.10 desktop live cd iso). At first I would give me a 'unknown keyword error', but I already fixed that (removing 'ui' in syslinux.cfg file).. 

However, when I get to the live version and choose 'install ubuntu' from the screen that pops up immediately after the startup, I will not get past that first screen that checks whether you have at least 2.6gib free space, internet working and that the pc is plugged in to a power source. If I click 'forward', it will simply start to load (the white ball indicating that there's stuff being loaded) and it will not get to the next screen. I watched my usb stick closely and the led light on it did not blink (thus no actual loading was done).. 


my plans (that failed ;( ) :
- I removed the 64 bit iso and put the 32 bit iso on the usb, result was the same as above
- I removed the 32 bit iso and put the 10.04.1 32 bit iso on the usb, but then it hung during the 'keyboard configuration' screen..(after clicking on 'forward')

my guess is that something might be wrong with my ssd?? maybe it's not connected that well (even though it's visible in BIOS)


the thing is, I REALLY need a working ubuntu installation on the zotac for my study.. I've been at this for almost 7 hours now... 

anyone who might know what is wrong here?

PS: I also own a Shuttle XS35GT which has the same SSD in it and the installation (via external DVD-writer) of 32 bit 10.10 went flawlessly... :S

---

### Post by MOB_Figga on 2010-12-04
I know I am not the only one in the world asking for some info, but is there anyone who knows what to do..?

btw, I've now tried the alternative cd  (put on a usb flashdrive) from 10.04.. now it hangs at scanning disks when starting up the partitioner... 


please note that the ocz ssd has nothing on it; it came straight out of the box and was put in the zotac barebone.. so there are no partitions/installations on it..

---

### Post by coehorn on 2010-12-04
Have you tried 32 bit and 64 bit images from other distros?  You're lucky your machine sees the OCZ SSD.  Mine would not even recognize it......

---

### Post by MOB_Figga on 2010-12-04
not yet no.. because I want to have ubuntu.. which one should I choose (looks most like ubuntu)?

---

### Post by Quackers on 2010-12-04
Did you check the md5 checksum of the downloaded .iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

