---
title: "Installation Problem..."
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by chrini on 2007-09-20
Ok, I've seen many threads that address the installation process freezing up, but so far I have not found any that answer my problem.

I have put together a system with some older parts (specs are below) and I want to put Ubuntu 7.04 on it for programming and what not. So I know to use the alternate CD since it is an old system (I know the alternate cd works because I used it on another system about a month ago). So I try it out and everything goes perfectly well (very smooth and snappy) until it gets to 6% of the base installation it just freezes up ( I can't remember what it said it was installing, unfortunately). 

So I try that three or four times (even putting my memory up to 384 MB of SDRAM).... nothing helps, sitll freexes up at the same spot... oh, just so you know I have to put "acpi=off" in the boot option (F6) to bypass the acpi error I get... So I try the original Ubuntu 7.04 and the original Ubuntu 6.04 installers, they both freeze when loading up the live CD. 

Anyone have any idea how to fix this boot issue?

Specs: 
Motherboard: S7-MVP3 (VIA Chipset)
CPU: AMD K6-iii, 450 MHz
RAM: 196MB PC133 SDRAM
Video: Used 3dfx(?) [I got it at a computer shop used with no info]
HDD1: WD400 [model: WD400BB-00JHA0] //this currently isn't working, so look at HDD2
HDD2: Maxtor (80gig?) [sorry, forgot to write it down...let's just look at one for now]

---

### Post by Cre8torX on 2007-09-20
It would be handy to have a spare harddrive my be it's your hard drive try pulling out the internal battery for the clock and reboot

---

### Post by chrini on 2007-09-20
What do you mean by spare hard drive? 

I have two hooked up (although I think I mentioned that I'm not using the western digital, that is because my bios won't read it, even though I know it works)... I also set the Maxtor to limit it to something like 3000 cylinders or something like that, I don't recall exactly, it is some kind of restriction....

---

### Post by dabl on 2007-09-20
Have you confirmed that your installation CD is a good burn?  I've seen multiple posts describing the problem as "it gets xx% done and freezes" -- and they all seem to end with a bad CD.

---

### Post by bliffle on 2007-09-20
> **dabl said:**
> Have you confirmed that your installation CD is a good burn?  I've seen multiple posts describing the problem as "it gets xx% done and freezes" -- and they all seem to end with a bad CD.

That happened to me once, and it cleared up when I re-burned the CD. Now, if I ever have a problem while processing the CD I just throw it out and burn a new one. Sometimes, with DVDs and audio CDs I can clean the surface with a clean kleenex employed radially around the disk, or with one of those $10 disk cleaners.

---

### Post by chrini on 2007-09-20
I'm pretty sure that it is a good CD, I used it about a month ago to install Ubuntu on an Athlon XP  system. And it went smoothly... I guess while it was sitting there it could have collected something on the disc, so I will go ahead and download the alternate again (check it to make sure it was a good download) and then try the installer again. Thanks for the advice, let me know if you have any other ideas as well.

---

### Post by chrini on 2007-09-20
Ok... so I have been having trouble getting my motherboard set up to fully acknowledge my K6-III cpu, and I finally discovered that I need 2.4V core and I had 2.1V, so I changed that... I also downloaded the alternate installer again..... and so far it has made it past 6%, however it scared me there for about 5 minutes just sitting there.... but so far so good... who would of thought that a perfectly good installer (from a month ago) would have gone bad. must have been a scratch or something? 

Well, thanks everyone! I'll let you know if it is a successful install, so if it is not I hope you guys will still be around...

---

### Post by Pumalite on 2007-09-20
I purposely didn't get in this thread. You seem to have made it...ah?

---

### Post by chrini on 2007-09-21
Yea, I think I've got it... however it froze up again, but at least it made it to 36%!?! I'm going to download it again and make another CD to see if it works this time.... maybe it's the brand of CD? (Maxell)

---

### Post by Pumalite on 2007-09-21
Maxell is the worst. Here is for you to read on and learn about blank CD's:

[http://club.cdfreaks.com/showthread.php?t=227635&highlight=cd-r](http://club.cdfreaks.com/showthread.php?t=227635&highlight=cd-r)

I would go for Verbatim

---

### Post by chrini on 2007-09-21
Thanks for the info, I'll take a look at it when I get a chance and I'll let you know how the installation process goes....again.

---

### Post by Pumalite on 2007-09-21
You are welcome.

---

### Post by chrini on 2007-09-23
Ok, if anyone is still posting to this thread, I finally got XUbuntu alternate to install (although I'd really prefer Ubuntu). It runs incredibly slow (I guess it is probably the fact that I'm using an AMD K6-III, 450 MHz cpu, but really it isn't that bad). 

I think what the solution was, was changing from an 80 gig Maxtor HDD to a 4 gig WD HDD, with the Maxtor as the slave. I think I might try the 4 gig HDD with Ubuntu 7.04 and see if I can get it to work. 

Thanks for all of the help, be sure to give me any other tips.

p.s. it took me three Ubuntu 7.04 alternate downloads, and two Xubuntu 7.04 alternate downloads and I finally got it. Again, I think it was mmainly the HDD though.

---

### Post by Pumalite on 2007-09-23
Glad you got it working!

---

