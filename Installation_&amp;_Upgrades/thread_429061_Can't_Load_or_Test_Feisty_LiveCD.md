---
title: "Can't Load or Test Feisty LiveCD"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by smcnally on 2007-04-30
This is very strange and only happens on the PC I want to load Feisty into...If I put the CD into my normal PC (this one) it loads and tests fine.  My other machine ( a home theater PC) boots to the CD and brings up the main menu.  If I tell it to load Ubuntu or Test CD it hangs.  I thought maybe it was the DVD drive so I swapped it with another and the same thing.  Could it be the motherboard is incompatible?  Could it be because I have so many drives in it right now and the liveCD doesn't like that?  The motherboard is an Intel D865PERL and it has an Intel P4 2.8Ghz processor with 1 Terabyte spread over 5 drives (not a RAID array).  I noticed my bios is outdated but also noticed that the upgrades are for either Window$ or Linux, but not both...could this be my issue?

---

### Post by smcnally on 2007-05-01
I can't seem to find any info on whether my MB could be at fault.  But I was thinking that it could be since I've heard similar issues happening with other models of Intel boards.  Nobody has any ideas on this, huh?

---

### Post by wislon on 2007-05-01
smcnally, I ran into something similar to this some time ago. do a search on the forum for "acpi=force", coz it sounds like you might have some sort of kernel panic during the boot. one or more of the results will tell you better how to debug this, by turning off the splash screen, not using quiet mode during boot, and so on. Good luck with it! :)

---

### Post by Benchrest on 2007-05-01
What graphics card do you have?

---

### Post by smcnally on 2007-05-01
Thanks!  I did a search and it looks like this thread [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688) has a lot of ideas.  I'll give them a shot tonight!

---

### Post by smcnally on 2007-05-01
> **Benchrest said:**
> What graphics card do you have?

I believe it is an ATI 9800 series.  Although ATI generally sucks with Linux, I didn't have issues with the same card on another machine (except getting Beryl to run smoothly).

---

### Post by Topsiho on 2007-05-01
I had the same problem on one of my computers. Seems to be a known bug, I forgot the number, in Launchpad, you could search for it, and be aware that Feisty there is called Fiesty.

I could not install Feisty using the Live CD, but everything went smoothly using the alternate CD.

On this computer I have installed most of the previous Ubuntu's without any problem.

I have tried to put in a new NIC, a new HD, a new CD-Rom player, all without any luck. I have an nvidia TNT2 graphics card in it, which I did not replace, having not a replacement ready.
The MB is a Jetway, with an aladdin5 chipset.

So ...

Using the alternate CD everything went okidoki, as said before.

Topsiho

---

### Post by smcnally on 2007-05-01
By alternate CD, do you mean the server edition?

---

### Post by ryber on 2007-05-01
> **smcnally said:**
> By alternate CD, do you mean the server edition?

When you download the ISO, there's an option to download the Alternate CD.  It doesn't have the graphical front end that the liveCD does.

---

### Post by smcnally on 2007-05-01
> **ryber said:**
> When you download the ISO, there's an option to download the Alternate CD.  It doesn't have the graphical front end that the liveCD does.

Found it, thanks!

---

