---
title: "Wubi and Windows XP 32-bit install problems"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by DrivenMink on 2010-09-09
I'm an experienced Ubuntu user and thus far avoided the need to ask too many questions, but this one's a bit of an odd one..

I want to run 10.04 on my XP pro SP2 box at work so I thought perhaps I could run it via Windows by using Wubi - usually I dual-boot or run independently. However due to several factors this isn't possible in this instance, so rather than intall VMWare and all that palava, I figured Wubi would do the trick. Not used it before tho :)

The installer starts ok, but once it starts to download the install files it interferes with my network connection to the point where all my connections suddenly drop, and the install fails. 

I don't know wtf it's actually doing at this stage, because my SSH sessions to other machines seem to persist but I can no longer browse the web, IM loses connection (both MSN and Skype) - which could indicate it's interfering with my DNS? Even after closing the installer I just can't do anything without having to reboot the machine.

I just grabbed the latest installer from the site and ran the install. I'm pretty sure I didn't do anything wrong - but for some reason this clearly does not work on this machine.

Am I missing something before I give up and try another tactic? 

It's turning into an awful lot of effort just to use one piggin' app... :icon_frown:

---

### Post by DrivenMink on 2010-09-09
ah. Having just re-read the documentation I can see that Wubi does not support proxies. Which would explain why it all went up the spout.

Downloaded the ISO and re-ran, and so far so good.. :-p

---

### Post by diosak on 2010-09-12
hey DrivenMink

i just downloaded Wubi and i want to do the same thing.
do i need to download the ubuntu iso first?
i suppose it is like a dualboot, but everything is installed over windows right?
what i need is a dualboot of ubuntu and win xp sp2. will this do the trick?
also, my xp is 32bit. however my cpu supports 64bit software. what should i do? download a 64bit ubuntu version? does wubi check your system out and downloads the appropriate os?

thanks in advance!

---

