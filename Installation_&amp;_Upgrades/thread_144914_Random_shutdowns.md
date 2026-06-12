---
title: "Random shutdowns"
date: 2006-03-15
forum: Installation &amp; Upgrades
---

### Post by slightly72 on 2006-03-15
Hi,

I've just installed 5.10 on a Sharp Actius UM32W (Pentium 3, 1GHz, 512Mb RAM -- shared with the video card). The installation worked great, all components recognized, including wireless cards (both built-in and external -- the internal one has limited range, so at work I need to use the external one). I've also upgraded the computer from repositories.

Anyway, the problem is that the laptop shuts down every 15 minutes or so, it's an unclean shutdown, just crashing. After that, I cannot use the power button, need to do a hard reset (on a small hidden button at the bottom of the laptop). This has repeated several times; could not detect any correlation between what I was doing and the time of the crash (sometimes upgrading packages, sometimes compiling some software to check the development tools).

This might be a bit of a stretch, but was wondering if there's any correlation between these crashes and the power management -- at times, during intensive jobs, the temperature of the processor was reaching 59C(140F) (according to acpi -t -f) -- but most of the time it was hovering around 48C. As I said, this might be a bit of a stretch, since same laptop handled long hours and compilation jobs (Windows+Cygwin) for quite a bit -- and also don't know how correct are acpi readings.

Any ideas/suggestions are really appreciated.

---

### Post by munga_bill on 2006-03-15
I don't know, but thanks for the acpi -t -c command, I didn't know that one before.
Have you got a 'PC health check' function in your BIOS that you could sit and watch for fifteen minutes or so? You might see what's wrong by watching that maybe. I think most BIOS's have a 'PC Health Check in them somewhere.
Another thing to try is a 'memtest86+', available by selecting it from your grub menu as you boot your computer. The series of tests takes around fifteen or twenty minutes for eight tests on your RAM. [http://forum.x86-secret.com/viewtopic.php?t=2906]("http://forum.x86-secret.com/viewtopic.php?t=2906")
Other than that I'd say just have your computer serviced (cleaned out), it always helps to have clean cooling fins and fans. Regards, munga_bill.

---

### Post by JohnnyLee on 2006-04-23
Some P3 processors had a maximum operating temperature of 60 or 65 degrees C, so depending on the version you have, that might be the case. If it just turns off suddenly, I would expect it's hardware related. I've had heat shutdowns on my laptop when using it in bed, and it just instantly shuts off.

---

### Post by slightly72 on 2006-04-27
For some jobs, the temperature goes above 60-65, but it does not crash then. Besides, it does the same in Windows, which means it's not something OS specific. After some digging on the internet, it seems that this particular laptop has a tendency to have random shutdowns when getting old -- my solution is to avoid using it for more than 6-7 hours straight, which is not a major problem.

---

