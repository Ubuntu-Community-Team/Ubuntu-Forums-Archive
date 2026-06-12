---
title: "Issues resolved/unresolved  installing 8.04 Ubuntu on tyan tiger mp s2460 motherboard"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by prime3end on 2008-11-25
I have a Tyan Tiger ol motherboard with dual cpu's ,, amd brand.  An ati agp rage 128, the motherboard requires ecc pc 2100 registered ddr. An oldie.

I have tried many installs, this is the first one that worked out of 20 on this box.  Its an old box just so you know.  

First issue was ACPI , had to turn it off in the bios as well another power setting below the acpi setting, it was another power control thing. 
This issue caused many problems and failed installs.

2nd issue was the bios battery had died and had to reset bios to ECC for memory,as it uses ECC registered pc 2100 DDR.  had to reset OS type on fist page of bios to "other", and set motherboard spec in bios to 1.1 instead of 1.4.  

I could not get through the install , not once, till I unplugged the network cable and then tried the install.  Till then I had many cd read errors.  When I unplugged the network cable I had no more such cd errors. worked well.  I had a couple hundred update files to do aferwards but that worked out well too. I started the download and went to lunch and it was ready to install when I came back.  Had I unplugged the network cable I would have saved a lot of time and trouble.  But the first trouble was with the bios settings. 

I have 2 network cards, a 3com 3c905x and a wireless card.  The wireless card shows up as unsupported but using proprietary drivers.  So another quirky aspect of my hardware and the video is ATI so I get this: 

last and still current issue is that the ATI rage 128 shows up under the sudo lshw as "UNCLAIMED"
stil not resolved.  I'm hoping this time it won't crash unexpectedly as it did before with many freeze ups.  I can say its working much better now, however I haven't tried the first person shooter games yet to see if it will work for gaming.  Hope this helps someone else and if you know how to resolve my video driver issue please post or email.

Thanks for Ubuntu!!!:)

---

### Post by OM NOM NOM on 2009-05-27
LOL I feel your pain! I just picked up not one, not two, but THREE systems with the S2460 board. Are you still running that system and have you had any issues since you've finally got an install running?

I'd like to use one of them for my home server but I'm worried about reliability as you can imagine. 

Thanks!

---

