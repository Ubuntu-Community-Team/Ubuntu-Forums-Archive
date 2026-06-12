---
title: "GRUB error 21 Linux Newbie"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by dm2497 on 2008-06-20
Hi there,

I'm a sophomore aspiring Computer Science major. I'm a really big fan of linux and think opensource is awesome, but I can't bear to part with Windows just yet. So I've been trying to get my laptop to dual boot Vista Home Premium and Ubuntu 8.04. In the past I had Vista Home Premium and Ubuntu 7.10 in dual boot and it was great. However when 8.04 came out I deleted my 7.10 partition using a Vista Repair CD so I could do a fresh install of 8.04. I got rid of the 7.10 partition but the GRUB wasn't functioning properly because it couldn't find the linux partition. Because the GRUB wasn't working I couldn't access my Vista partition either. To fix this once again I used the Vista repair CD and I typed FIXMBR in the Command Prompt and I was able to restore my Vista partition. I then downloaded 8.04, and attempted to install it but the installer gave me problems so I gave up on trying to install 8.04. I've been running Vista since.

Two days ago, I got the sudden urge to try again. I booted from my 8.10 live CD and proceeded to install it. I was able to install it after fooling around with the paritions using Gparted on the liveCD. After installation I rebooted my computer. The proper grub showed up. I booted Ubuntu 8.04, got to the login screen was able to type in my username and password, got to the pink-like loadup screen but that was as far as I got before it froze. So I rebooted the system and tried to boot Ubuntu again. Upon rebooting my computer I got an error loading the GRUB, it displayed 'GRUB error 21'. I restarted my laptop and proceeded to boot from the liveCD. Out of curiosity, I decided to run Gparted again to see what was going on, only to discover that my recently installed linux partition was not showing up. :confused:

I pride myself in being able to fix things reading online forums and blog posts with solutions to my problems but I don't know where to start. I would really appreciate some help with my problem. Thanks. [-o<

---

### Post by Pumalite on 2008-06-20
If you use Vista; you have to use the Vista partitioner to allocate space for Ubuntu first, You cannot partition with the Ubuntu CD. (Thanks Microsoft)

---

### Post by upchucky on 2008-06-20
Knoppix is the god when fixing broken windows and tweaking linux installs.

Also google search for super grub, it is very useful for fixing grub problems

---

