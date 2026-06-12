---
title: "Ubuntu 8.04 install fails to detect any hard drives"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by lcpetroski on 2008-04-24
Hello all:
On a system currently running Ubuntu 7.10, the Hardy Heron 8.04 update fails to detect any hard drives at all. As I am using the affected system to write this, there is no apparent problem with the hard drives. The system is using the PC x86 32 bit desktop distributions in both cases. Gutsy Gibbon correctly identified the two SATA hard drives and installed without problem using the ext3 file system, whereas 8.04 issues a series of 8 consecutive "Buffer I/O error on device FD0, Logical Block 0" messages before proceeding to the install where of course no drives at all are shown. Installation must be abandoned at this point. The system motherboard is an ASUS M2R32-MVP with a 64 bit AMD Athlon X2 processor (have also tried the Hardy Heron 64 bit distro with the very same result). Memory is 4 GB. Since 7.10 hardware detection was perfect, some regression error appears to have crept in with Hardy Heron. Any advice on how to proceed?

---

### Post by animalk on 2008-04-24
Hi, I have the exact same problem.:(

EDIT: I just attempted calculating the checksum of my iso image for desktop i386 version taken from the ubuntu torrents and they came out different. The supposed correct checksum is 7a8269d1801b203f96eefbd68cbcd68056f8cc84	 and i got 88951671794c5d8dedcc312fc62f1f1f.
My download was never interrupted this morning and was going quite fast. The image had no problem burning. 

Is it possible that a bad iso image is out there like others have been suggesting? I used a free program called winMd5Sum to calculate the checksum.

---

### Post by lcpetroski on 2008-04-24
I downloaded my ISO of the distro from the MIT mirror site and the md5 sum checked out perfectly, but still the problem exists. Don't feel too badly about having a corrupt ISO, even a good image won't cure this unfortunately. Thanks for the quick response.

---

### Post by cafe con leche on 2008-04-24
Hey you guys I had the same problem last night at 2AM (I was installing the release candidate cuz it's the same thing). 

After trying a whole lot of things, here's what worked for me:
(I was using the alternate CD of the AMD64 version btw)

I hit f6 at the installation menu, and added the following to the end of the sentence representing the installation menu:

pci=nomsi

if you don't understand what i'm saying please ask me and i'll help you in more detail. Also, you can contact me on AIM with the SN: h4q

After i added that, it was just straight up smooth sailing. 

I think it has something to do with using sata devices. 

cheers.

---

### Post by cafe con leche on 2008-04-24
Oh and lcpetroski: I have the same motherboard, same processor, 4 Gigs of RAM and i got the exact same errors you got. In order to get rid of those initial errors i used the alternate CD, and in order to get it to see all my hardware i had to use pci=nomsi.

my comp is from around christmas time it's a newegg rig, i assume you did similar?

peace

---

### Post by lcpetroski on 2008-04-25
Thank you very much cafe con leche. I added the parm as you indicated and the install completed normally. I see we were both up at around the same time last night! Anyway, Hardy Heron looks great, but it is such a shame that some SATA users out there are going to have a less than favorable first impression. Most especially, it is discouraging that a previously functional and smooth installer (7.10 Gutsy) has given way to these retrograde difficulties. I built my own machine from individually purchased components and a spare chassis I had lying around. I'm retired now and it was a lot cheaper than purchasing a new machine (I hope you never have to worry about such things!). Again, thank you very much for the help and now we can start enjoying this distro. Take care.

---

