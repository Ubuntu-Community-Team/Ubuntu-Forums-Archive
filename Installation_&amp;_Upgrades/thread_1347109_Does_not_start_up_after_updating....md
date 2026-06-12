---
title: "Does not start up after updating..."
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Rimdeker on 2009-12-05
I updated my Ubuntu NBR today. Nothing extraordinary just routine, well that is what I thought but it seems I was wrong because after finishing the update I was asked if I wanted to reboot now or later. I clicked now. I still had firefox and another window running but that never made any difference and I don't think it makes any here. 

Anyhow, after rebooting the horror began. I was thrown into some kinda "sh:" command line of GRUB or something, fact is it did not boot into Ubuntu like usually. I restarted several times but nothing changed, is there any solution or do I have to re-install Ubuntu now, which, in all honesty, I will not do... totally not worth it.

A few infos that might be useful to solve this problem:
I'm using an Asus EeePC 1005.
I installed it within Windows 7 that came with the netbook.
The update was done sunday 6th december at around 1:45 AM.

Hope someone can help me out.

---

### Post by SK Linux on 2009-12-05
The same exact thing happened to me--only I am dual booting XP and Karmic

---

### Post by Rimdeker on 2009-12-05
> **SK Linux said:**
> The same exact thing happened to me--only I am dual booting XP and Karmic

Did it occur just now, too?

---

### Post by SK Linux on 2009-12-05
Earlier today

---

### Post by drsawah on 2009-12-05
me too xp and karmic
> **SK Linux said:**
> The same exact thing happened to me--only I am dual booting XP and Karmic

i reinstall ubuntu then when make ubpdate dont select gurb2 and every thing ok aafter restart
untill gurb 2 problem solve

---

### Post by SK Linux on 2009-12-05
I was already using grub2 though-version 1.97

---

### Post by Rimdeker on 2009-12-05
> **drsawah said:**
> me too xp and karmic


i reinstall ubuntu then when make ubpdate dont select gurb2 and every thing ok aafter restart
untill gurb 2 problem solve

I know you mean it well but I am really having a hard time understanding. I did not select anything during the update I just hit OK.

---

### Post by Rimdeker on 2009-12-05
Sounds like anybody who's updated recently might have this weird problem.

And it feels like there is no way around but to re-install Ubuntu NBR and then most likely end-up updating again and that way it would not work, again lol.

---

### Post by wilee-nilee on 2009-12-05
> **Rimdeker said:**
> Sounds like anybody who's updated recently might have this weird problem.

And it feels like there is no way around but to re-install Ubuntu NBR and then most likely end-up updating again and that way it would not work, again lol.

I wouldn't go by one response in your thread as everybody or even what you see in the forums.

---

### Post by Rimdeker on 2009-12-05
> **wilee-nilee said:**
> I wouldn't go by one response in your thread as everybody or even what you see in the forums.

I agree, two of my friends on IRC told me that they, too, have this problem now. Still, I shouldn't have said that but yea, it seems to be some kinda problem that is now spreading to other NBR users. Which ,of course, sucks, especially for people who have installed Ubuntu/Ubuntu NBR recently. Imagine you're trying out a new OS and suddenly it stops working due to it's own update.

Something like that shouldn't happen :/

---

### Post by wilee-nilee on 2009-12-05
> **Rimdeker said:**
> I agree, two of my friends on IRC told me that they, too, have this problem now. Still, I shouldn't have said that but yea, it seems to be some kinda problem that is now spreading to other NBR users. Which ,of course, sucks, especially for people who have installed Ubuntu/Ubuntu NBR recently. Imagine you're trying out a new OS and suddenly it stops working due to it's own update.

Something like that shouldn't happen :/

I have a netbook and found the UNR's in general to be problematic even as a single running OS. I agree that this sort of thing shouldn't happen, but without knowing why I am hesitant to blame the OS. If you like Ubuntu you should dual boot it and use a regular desktop you will probably get the best response and ability to fix any problems that way.

If the MS system goes bad you will have two OS not working.  I dual boot W7 and Ubuntu, I tried out the wubi set up a while back but found it to be a problem when you remove the Ubuntu set up, it was fixable with a removal of all things wubi and a modification of the windows bootloader.

---

### Post by some-what-Gnu-2-networks on 2009-12-05
Possible alternate for Asus users: Eeebuntu

---

### Post by ibuclaw on 2009-12-06
No issues on my netbook - but I have bumped into something minor when experimenting with a fresh install of Ubuntu ontop of BtrFS.

If you boot without splash, what do you get?

I received something along the lines of:
```
udevadm trigger is not permitted while udev is unconfigured
```

The simple remedy is boot into a LiveUSB, mount and chroot in - then reinstall udev.

Regards
Iain

---

### Post by replikanxxl on 2009-12-07
most of updaters have the same problem yes . But reinstalling is not a solution . Why would i install rather than live CD , if im gonna reinstall it this often.. i spent days to set up all the platforms i need to use on linux . Update stuff is not childplay. I donno what people think though .

AH i know this is a thread based on netbook remix. please dont come up to me informing that. im just talking in general opinion

---

### Post by lengjingmao on 2009-12-07
Hi , I met the same problem on my 64 bits ubuntu. after updating , can not start up. 


it just go to BusyBox with a command line console

---

