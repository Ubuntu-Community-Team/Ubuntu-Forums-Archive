---
title: "Live CD will boot, but screen goes black..."
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by TheElite1x721987 on 2006-11-23
I've succesfully installed Ubuntu 6.10 on my old Pentium 3 compaq tower with not a single problem (no real problems anyway ;) )

I wanted to run Ubuntu on my main tower I got however, as it is much, much faster. I want to dual boot. I can handle the making it dual boot part. But I ran into a unforseen snag...

I tried with 6.10 Edgy and 6.06 Dapper. Both had the same end result. The Live CD works fine it seems. It loads up, I see the Ubuntu loading splash screen. After thats done, I see  a black screen with a blinking line in the top right of the screen. It seems like it about to go to the desktop (like it did on my compaq when i first put in a live disc). But it doesnt. After 5 seconds of that blinking line, the monitor kicks off into standby mode. I get no display at all. I tried again several times with Dapper and Edgy in safe graphics mode, thinking that was the problem. That didnt solve my issues either :( I'm hoping someone can help me out here, as I would really like to Dual boot on my much faster main tower.

Here are my system specs that I am trying to run it on ( and install after it runs)

Athlon XP 3000 w333mhz FSB
Biostar M7NCG nForce 2 Mobo (Disabled the integrated graphics)
GeForce FX 5200 Ultra
Sound Blaster Live 24bit
1gig DDR 333 ram

---

### Post by renzokuken on 2006-11-23
sounds to me like a grafix problem, specifically with your xorg.

do you know which video driver it is using? may have to use the Vesa driver so you can get in and then install the nVidia driver

have you tried the "alternate" install CD?

---

### Post by TheElite1x721987 on 2006-11-23
No, I have not yet tried the alternate install CD. If I try that, is the install process just as easy as the GUI based live disc? I just don't wanna accidently choose the wrong HD letter and wipe out my windows install and all my data (that would be catastrophic...:( ) I was kinda expecting a graphics problem, and had a hunch I needed to drop into a command line to fix it. But then my question is. Which steps do I need to go thru to DL and install the nvidia driver? I'm a fairly new Linux user, ive had experience with its command line, but im by far not a pro at it. Do you think I should try that first or the alternative install disc?

---

### Post by wagoatzuki on 2007-01-03
Well I had the same problem but I found out it was cause by using the DVI cable on my vid card instead of the VGA cable. My monitor was in stand by after the splash screen, I plugged in the vga cable and found it sitting at the desktop ready to be installed and waiting on me for the next step. Now I am having the same exact problem with my laptop but I don't know what to do with this problem?? I tried the CRT output hoping that I could get through the install but that don't work either.

---

### Post by Omeil on 2007-02-23
Have you tried using a different monitor?. some people's monitors went on standby because they couldn't handle the refresh rate. its a possible issue.

---

