---
title: "Can't get live or installation cd to run"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by Otto on 2005-02-23
Hello, newbie speaking, very nice to meet you all. I've been fiddling around with various linux distros for a while now, but I'm still very inexperienced and anything that is not GUI tends to be a huge hurdle. I'd love to give Ubuntu a try, but whenever I pop in a cd (live or installation), Caldera gives me the following options:

/MLX Program is loaded into conventional and XMS memory using DPMS
/BL=16 Lookahead buffer is in conventional memory, size is in KB
/LEND=ON Lend memory to other applications - 66646 KB available
/DELAY=OFF Write delay is disabled, caching is write-through

...after which comes [DR-DOS] A:\> where I presumably need to type one of the above. Whichever I choose, though, I'm told that that command or filename is not recognized. I haven't the foggiest idea what all that means and how I might solve it. Please excuse the terribly stupid question, but could anybody tell me what I should do with this? 

Thank you... I swear I will one day learn enough about the command line to know what I'm doing and no longer embarass myself.

---

### Post by r0b0 on 2005-02-23
[QUOTE=Otto]Hello, newbie speaking, very nice to meet you all. I've been fiddling around with various linux distros for a while now, but I'm still very inexperienced and anything that is not GUI tends to be a huge hurdle. I'd love to give Ubuntu a try, but whenever I pop in a cd (live or installation), Caldera gives me the following options:

/MLX Program is loaded into conventional and XMS memory using DPMS
/BL=16 Lookahead buffer is in conventional memory, size is in KB
/LEND=ON Lend memory to other applications - 66646 KB available
/DELAY=OFF Write delay is disabled, caching is write-through

...after which comes [DR-DOS] A:\> where I presumably need to type one of the above. Whichever I choose, though, I'm told that that command or filename is not recognized. I haven't the foggiest idea what all that means and how I might solve it. Please excuse the terribly stupid question, but could anybody tell me what I should do with this? 

Thank you... I swear I will one day learn enough about the command line to know what I'm doing and no longer embarass myself.[/QUOTE]
 Live CDs are not supposed to be run from a running OS.
Shut down your running OS, reboot your PC, put the Live CD in your CD drive, when your computer boots up, it will start the Ubuntu Live CD.
If your usual OS starts instead, you will have to set up your BIOS settings to boot up from CD first, hard drive second.

---

### Post by Otto on 2005-02-23
[QUOTE=r0b0]Live CDs are not supposed to be run from a running OS.
Shut down your running OS, reboot your PC, put the Live CD in your CD drive, when your computer boots up, it will start the Ubuntu Live CD.[/QUOTE]

Ah, that's exactly what I'm doing, that much I've figured out. Sorry for the misunderstanding.

Forgot to mention -I'm running a very old system, 64ram, 233Mhz. This is very little and I'm actually trying to find a good OS that will run on that without crawling along. I've got another more recent computer so it doesn't matter if the old one goes slowly or breaks down, I'm using it to experiment a lot and learn more about linux and computers in general. I've found the howto for running Ubuntu on a low-memory system and would like to try it, but since the installation cd won't even run, I'm stuck.

---

