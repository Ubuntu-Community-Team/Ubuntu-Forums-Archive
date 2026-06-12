---
title: "Extremely annoying Asus dual-boot NTFS problem"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by Dorian_McILROY on 2014-04-29
Hello there,

I have run up against a really pesky problem with a Windows 8 / Ubuntu 13.10 dual boot.

So, to go back to the beginning of the story, about a month ago, I treated myself to a new Asus S400ca for use at work. After reading the relevant howtos, I installed 13.10 in dual-boot, after re-sizing the D: windows partition to make space for the Ubuntu install. Everything went smoothly at the first attempt (hey - thanks all you Ubuntu developers, you're doing a great job!).

I want to use the D: partition as my main work data storage space, with files accessible from W8 and Ubuntu. A week went by with me working exclusively in Ubuntu before I used W8 again (in fact, it was because I couldn't get a Wacom Bamboo pad to be "seen" in Ubuntu, and I wanted to check that it worked at least in W8). However, when I did this, I noticed that all the files I had modified/created on D: from Ubuntu seemed to have disappeared, and they didn't come back again when I rebooted in Ubuntu. I managed to get everything back using Recuva on Windows, then I tried the fixes that have been proposed to other people with a similar problem.

I disabled fast boot in the W8 control panel, and also ensured that it was disabled in the UEFI menu. This seemed to work the first time I did it (files created on D: from Ubuntu were visible in W8), but after another couple of reboots, the same problem has returned, and I can't seem to fix it.

I realize that this is more of a Windows problem than a Ubuntu issue, but if anyone has any ideas, or can post a link to the solution, that would be great.

Yours,

DMc

---

### Post by Mark Phelps on 2014-04-29
I've heard that some preinstalled Win8 machines automatically reset Fast Startup - which yours may be doing.  If that's the case, you're not going to be able to share filesystems between Ubuntu and Win8.

---

### Post by Dorian_McILROY on 2014-04-29
Thanks for your answer, Mark. If that's true, then I guess I'll just have to use an external hard drive for data accessed by both Windows and Ubuntu. Kind of annoying, though.

---

### Post by Dorian_McILROY on 2014-04-30
A couple of dozen reboots later, and the only solution I found is that I can force complete shutdown of Windows 8 by opening an administrator command line prompt and typing

shutdown /s /t 0

Then when I restart in Ubuntu, save files on D: and reboot in Windows, the changes are visible.

So I guess my problem is solved, but it would be handy to be able to change the shutdown settings somehow.

DMc

---

