---
title: "Help! Live CD hangs at this message:"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by orick99 on 2008-02-29
Can any one tell me what it means when Ubuntu and Xubuntu live CD hangs at this message?

301.932738] EIP: [<c0197457>] create_empty_buffers+0x17/0x90 SS:ESP 0068:ce7bcd0

I am trying to switch my parents computer from Win XP to Ubuntu. I installed Ubuntu on my laptop without any problem. Convinced my parents to switch to make their life easier. Told them it would be an easy and painless switch. Then I can't even run the live CD!

The normal method gets me to a blank screen and a blinking cursor. I turned off quiet and splash. Tried different VGA options and both Ubuntu and Xubuntu live CD hang at this spot.

I did the memtest and scanned the CD. tried it with and without the ATI card, put CDRom drive and hard drive on seperate cable as masters. All without luck. After two evenings, my parents are telling me to just give it up. Help me out please!

CPU: Intel Celeron 1.7 GHz	
MB : Soyo P4VGA
RAM: 500mb
HD: 40Gb WD
GFX: ATI Rage Pro

---

### Post by banewman on 2008-02-29
What brand and model is the comp - a laptop?

---

### Post by dstew on 2008-02-29
Since you have tried the usual kernel parameters, you may have to go with an Alternate Install CD. It uses a text-based installer. Get it by checking the box below the Start Download button on the Download Ubuntu page.

If you want to try more kernel parameters first, try noapic nolapic acpi=off irqpoll separately or in combination. The first two disable the advanced programmable interrupt controller, acpi=off disables advanced power management, irqpoll tells the kernel to wait for certain interrupts rather than going ahead and having the interrupts try to stop it.

---

### Post by orick99 on 2008-02-29
It's not a laptop. I put it together myself a while ago so I know it pretty well. I can install win xp on it in 30 minutes with my eyes closed. Ubuntu on the other hand....

Forgot to say I already tried noapic nolapic acpi=off, will try irqpoll when I get home.

I want to learn about Linux, that's why I really want to figure this out. I googled "create_empty_buffers" and can't find out what it's related to. Is it something to do with harddrive or memory or the CDRom?

I guess I would eventually try the alternate install cd if I really can't figure this one but I would really like to learn this.

Thanks for the replies.

---

### Post by orick99 on 2008-02-29
bump, anyone have any advice?

---

### Post by dstew on 2008-02-29
Try the Alternate Install CD.

---

### Post by orick99 on 2008-03-03
well alternate CD works fine as expected. but I really wish I could find out exactly what the problem was with the live CD. :confused:

---

### Post by Kuoi on 2008-03-08
Had the same thing , but founded out that it helped by clcicking
"CTRL"+"Alt"+"+"
Everytime you do this it changes the resolution , and gives you the live cd screen for installation.
In my case it couldn't find the right resolution , but it worked well.

Hope this helps.

Kuoi

---

