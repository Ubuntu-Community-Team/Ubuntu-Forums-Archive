---
title: "upgrade from 7.10 to 8.04 wifi badly broken"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by clsiburt on 2008-04-25
I did the upgrade today using update manager.  The OS seems like it installed properly, but the wifi is giving me a very strange problem.

When I try to connect to my router, whatever the OS is sending is actually causing the router to reboot.  3 other devices connect/disconnect without incident.  When I boot up to the 7.10 live cd everything is fine.  Right now I'm typing on the affected machine from XP and it is fine.

I tried changing the network name and removing encryption.  Also tried several reboots of the laptop.  Nothing works.  My next step is to try a fresh install, so I'm downloading the cd installer right now.

Anyone have any thoughts on what could cause this one?  It doesn't seem logical that trying to connect to the network should be able to reboot my router.

Chris

---

### Post by forkd on 2008-04-25
weird.  what kind of wifi card/chipset is present?  Is it connecting to the router and then crapping out the router?  Check the router log if enabled or enable logging in the router and see what's happening.  Also, what router are you using.

---

### Post by la3875 on 2008-04-25
Thats a new one for me. What wireless card are you using? There seems to be a bug that breaks wifi between updates from Beta to RC that must have carried over to the latest. I had all working perfectly on beta then broke and I can't get it back. Thinking of reinstalling beta or going with 7.10 for a while till there's a fix.

---

### Post by clsiburt on 2008-04-25
Yep, I can see my network listed in the network manager.  I click on it, and it begins the connection process, but it never actually connects.  I hear a click coming  from my router about 5 seconds later and it begins its reboot process.


It's an older 2wire 802.11B router for my AT&T DSL, no logging option that I can see.  It's always worked great up til now.  The wireless card in the laptop is Intel PRO/Wireless 3945ABG.

Is it possible to roll-back to 7.10 without doing a complete reinstall?  If so I may take that option.

---

### Post by Peter09 on 2008-04-25
Hardy uses as default IPv6. May be your router cannot support that? It is possible to disable it - you will have to do a search to find out how.

-its a thought before having to drop back a version.


PC

---

### Post by delorin on 2008-04-25
I have the same problem.

---

### Post by clsiburt on 2008-04-25
> **Peter09 said:**
> Hardy uses as default IPv6. May be your router cannot support that? It is possible to disable it - you will have to do a search to find out how.

-its a thought before having to drop back a version.


PC

I did a search and found instructions to disable ipv6.  Either the instructions were wrong, or that was not the problem. :|   I reversed that to the original setting and decided to try a wired connection.  It works just fine on the cable.  So my router must support ipv6.

This is looking like something strictly related to the wifi.   I'm going to try the 8.04 live CD as soon as I finish burning it and see if wifi is fine through it.

---

### Post by jimbo99 on 2008-04-25
On two of my laptops that have built in wifi, a compaq r3000 and a HP zv5000 when attempting to use wifi it wants to download restricted drivers.  Once this is done it locks up my computers, both of them.  On the HP zv5000 I used the Live CD.  It locked up. Boom.

Prior to this I could get wifi to work and most certainly, though I had issues, they never hard locked my computer.

Booting into Windows on the R3000 works fine.  No issues.

I had written many many many posts on various sites about how 8.04 notebook support has gone way down hill and tried to alert people to avoid 8.04 with their notebooks.  Due to this degeneration of the state of notebooks I'm at the point that I won't upgrade my desktops either.

Fair warning was given and Canonical knew about the issues and did nothing.  Not counting the fact that compiz worked on my laptops and now it doesn't.

---

### Post by clsiburt on 2008-04-25
I tried the live cd, and came up with the same results.  After reading the last post, I realize that 7.10 was using the restricted driver for the wlan card.  It doesn't appear to be loading any restricted drivers on 8.04.  

This is really dissapointing.  It seems like something is always broken for me.  On 7.10 my audio required a workaround.  It works out of the box on 8.04.   My wlan was always fine on this laptop, now it's busted.  All things considered I could live without sound if I had wifi working.

Is it possible to revert to 7.10 or am I going to have to do a full reinstall?

---

