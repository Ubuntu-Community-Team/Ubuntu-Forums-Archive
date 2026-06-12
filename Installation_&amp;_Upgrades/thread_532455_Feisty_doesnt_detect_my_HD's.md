---
title: "Feisty doesnt detect my HD's"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by ragrim on 2007-08-22
HI, well i tried for the 3rd time to install 7.04 feisty on my desktop last night without any luck, my live cd works (eventually after some errors) and the install starts but when it gets to partitioning it doesnt detect and drives, i have 7 SATA hard drives no IDE. ive done a bit of research and seems my board may be an issue but i cant find anyone else with the same mobo having the exact same issue.

My system is..

Abit AB9 Pro (BIOS 1.16 i think)
E6300
2x 1gb G.Skill 
7950GT 512mb
7x SATA HD's (mix of seagate and WD's)
Pioneer 107D IDE DVD

Now... ive tried running my HD's in IDE mode and RAID mode and tried all 3 controllers on my board (my board has 3 differant SATA controllers it seems) but still Ubuntu never detects any HD's..

I dont have an IDE HDD nor do i ever want to use one again but im dying to start using Ubuntu on my home PC as ive been using it on my work laptop for some months now and im loving it. is there a solution for my problem or is the AB9 Pro simply not supported?

has anyone had this problem and gotten around it without using an IDE drive?

Thanks in advance.

---

### Post by Pumalite on 2007-08-22
Try a different Linux and see if it recognizes your hard drives. Then you'll know if it's a hardware problem, a problem with Linux or a problem with Ubuntu only.

---

### Post by ragrim on 2007-08-22
I tried the latest mandrive live cd but i remember i had some problem with that, i just got a fedora disc yesterday so ill give that a try tonight.

im confident my hardware is 100% working cause ive never had any problem with windows (well, other than the usual windows problems)

from what i read though Ubuntu has alot of issues with 965 boards... shame, id love to see how well ubuntu would run on my system.

---

### Post by ragrim on 2007-08-23
Well i finally got ubuntu to install on my PC finally! i installed it onto my USB Hard Drive after a bit of messing around...

wierd thing is, after it was installed to the usb hard drive and i booted into ubuntu it detected all my hard drives no problems..

next problem i had was my network doesnt work, ubuntu detects the network cards (onboard) but they dont seem to work, i did a bit of googling and had not much luck, found one post saying that windows turns off the cards when it restarts and you need to disable that feature in windows, so i did that and then when restarted and ubuntu hangs on loading now :confused::confused::confused:

Is there a vew of ubuntu that works with AB9 Pro motherboard? or is there a newer version comming any time soon that works with it?

oh and also i tried to activate the restricted driver for my 7950GT video card but when i click ok on the apply screen nothing happens, it doesnt activate it, is 7950GT not supported?

---

### Post by Pumalite on 2007-08-23
Glad you got it working. With regards to your card I can advise you to check here:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Pumalite on 2007-08-23
Take a look at this and see if it helps you:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
If you need help installing proprietary driver, let me know.

---

### Post by ragrim on 2007-08-24
heh, my video card isnt listed in the hardware section, i have a 7950GT not a GX2, seems everyone forgets about the 7950GT, even Nvidia, when i bought it the drivers it came with didnt work, i had to use beta drivers for 3 months till proper supported drivers were released, now even ubuntu has forgotten about me :(

and my motherboard isnt listed either lol.

from what i can tell im up the creek without a paddle till my board is fully supported or i get a new board :(

just downloaded the 64bit version of fiesty so ill try that tonight, ive read a few people had more success with the 64bit version over the 32bit version for the AB9 Pro.

---

### Post by ragrim on 2007-08-24
Update!

64 bit fiesty gave me more problems than the 32bit version! i gave up on that and discovered Ubuntu 7.10 Gutsy..

downloaded Gutsy Tribe 4 64 bit alternate (non live cd) had an error about something at the start and added irqpoll to the boot options and after that installed perfectly, im running ubuntu flawlessly, sound video network the lot!

WOOHOOO!

---

### Post by Pumalite on 2007-08-24
Good to know.We'll keep it in mind. I'll bookmark it.

---

