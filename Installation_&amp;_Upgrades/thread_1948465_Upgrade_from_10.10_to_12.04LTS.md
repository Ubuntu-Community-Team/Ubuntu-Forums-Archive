---
title: "Upgrade from 10.10 to 12.04LTS"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2012-03-28
I will be upgrading from !0.10 after 12.04LTS when it is final.  
My question is:  
   [LIST=1]Will I be able to upgrade directly to 12.04LTS from my current 10.10?
2. Will I have to upgrade to 11.04 then to 11.10, then to 12.04LTS.
3. OR will I have to do a clean install?
[/LIST]

---

### Post by raja.genupula on 2012-03-28
> 1. Will I be able to upgrade directly to 12.04LTS from my current 10.10?

No not possible , We can make either LTS Upgrades or 11.10 to 12.04 Upgrades . 

> 2. Will I have to upgrade to 11.04 then to 11.10, then to 12.04LTS.


yeah its a possible way but large process .

```
3. OR will I have to do a clean install?
```

This is the better option if you're ok with Fresh installation .

Note: dont forget taking IMP data as backup before Upgrade/Fresh installation . 

Hope that helps.

---

### Post by oldfred on 2012-03-28
with a 640GB drive you should be able to create a 10 or 20GB / partition and install 12.04 to test before you either upgrade or do a clean install. I normally do clean installs but to a new partition, so if I did not backup some configuration, I can go back and get it. But I have all data in other partitions than / (root), so I can keep / small.

You will need to know about nomodeset if you have not had to use it with 10.10 ( I think you did). To boot liveCD or on first boot you will need the nomodeset parameter until the nVidia driver is installed for your desktop.

I have 12.04 in a 8GB partition on a 16GB flash drive so I can test on my laptop. It does not have enough room for another partition so I add one via the flash drive.

---

### Post by jlh68 on 2012-03-28
**oldfred**  Thanks, but I am looking at my laptop that is on 10.10.  I have set it up with many partitions. See the attached image.
Are you saying to divide the root partition and install 12.04LTS, so that I have two OSs installed at the same time? Or should I shrink e /home partition some to free space for a new partition?  Maybe now is the time to use the win PQSERVICE partition as it is 13-GB, all it is, is the restore program which I have on DVD's somewhere. Of course I seldom use windows, and only when I have a win application that will not run on WINE.

I don't think the nomodset will be applicable to the Intel graphics on the laptop.

I think my BIOS is screwed up on my desktop computer.  I cannot even get the BIOS to go through all its routines to start up.  I now cannot even boot up the System Rescue CD. I am strongly thinking about a new M/B, an AMD APU processor and DDR3 RAM.  The APU is a CPU + GPU.  Then I will just install 12.04LTS on it and be done with current problems.

**raja.genupula** Also thanks, I think I knew the answers before asking the question, just wanted to be sure.

---

### Post by oldfred on 2012-03-28
No you should not need the nomodeset on your laptop. Some systems do require it or other settings depending on video card/chip. 

You may want to check on your possible new system with the apu. Often very new hardware is not fully supported immediately.

It looks like you have room after your /home for another 10 or 20GB partition to use as test. I would not reuse /home as some software may update settings that then would not be compatible with your working system. You can reuse /home when you fully install or upgrade will use it of course. You can copy some of the hidden settings if you want into your test install just to see what happens. Actual settings are very small, most of /home is your data or .wine.

---

### Post by alenn on 2012-04-03
When I put my Ubuntu CD in tray, system recognise it as software source, so is it possible that I upgrade my system while my 10.10 version is running.

---

