---
title: "every version of ubuntu, i install hangs after some minutes"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by dev9226134 on 2011-08-05
i tried to install ubuntu (10.04,11.04) both in 32 and 64 version,both were hanged,i have a desktop with 8 gb ram,i5 3.3 ghz,
radeon 6870 graphics card.i was trying to install dual both means install inside windows.
help me......

---

### Post by Duncan Williams on 2011-08-05
If your pc is hanging after a few minutes it could well be ram related.
Check all bios settings and make sure your 8 gig is allocated correctly.

---

### Post by Blasphemist on 2011-08-05
Is the install from within windows the only install you've tried? I can't tell from how you worded it. That has always seemed kluggy to me but I suppose there is a place for it. It seems to me that you can do a very good test of how you'll like it and how your machine will like it by running from the live cd.

You have plenty of machine to run the 64 bit version very well. I say dump the 32 bit. What are you doing that is common for the times when it hangs? Have you looked at any of the log files via the log file viewer? 

I'd start with trying a lengthy session running from the cd and see if it locks up. See if you can figure out just what situation precedes the lockups. See if the logs help you narrow this down. Do you have what is called switchable graphics? That is a gpu on the motherboard and one added. This is a challenge and is just a guess but could be involved. If you post the model details we can look at the spec details and see if it does if you can't tell. There are commands used to look at hardware details, lspci and lshw. The latter may need installed but it will tell you how if you try an run it.

---

### Post by dev9226134 on 2011-08-06
what configuration of machine you want,i given in my first post.if you want some more thing tell me from where i get this because i am now using windows 7.and i don't know anything about ubuntu,log file etc.i have a graphics card radeon amd 6870,it has two modes vga or hdm and right it is plugged with vga mode.help........











> **Blasphemist said:**
> Is the install from within windows the only install you've tried? I can't tell from how you worded it. That has always seemed kluggy to me but I suppose there is a place for it. It seems to me that you can do a very good test of how you'll like it and how your machine will like it by running from the live cd.

You have plenty of machine to run the 64 bit version very well. I say dump the 32 bit. What are you doing that is common for the times when it hangs? Have you looked at any of the log files via the log file viewer? 

I'd start with trying a lengthy session running from the cd and see if it locks up. See if you can figure out just what situation precedes the lockups. See if the logs help you narrow this down. Do you have what is called switchable graphics? That is a gpu on the motherboard and one added. This is a challenge and is just a guess but could be involved. If you post the model details we can look at the spec details and see if it does if you can't tell. There are commands used to look at hardware details, lspci and lshw. The latter may need installed but it will tell you how if you try an run it.

---

### Post by dev9226134 on 2011-08-06
> **Duncan Williams said:**
> If your pc is hanging after a few minutes it could well be ram related.
Check all bios settings and make sure your 8 gig is allocated correctly.

ya,i checked it is working properly as my computer is running windows 7 and so many its application nicely.....

---

### Post by Duncan Williams on 2011-08-06
I had an issue where my linux partition would not boot correctly.
At the time it was a dual-boot instalation with windows.
The windows partition booted ok.

Turned out after changing a few setttings in bios (switched them back later) relating to > vga aperture, S.M.A.R.T and a couple of other ones.
It all worked ok.

---

