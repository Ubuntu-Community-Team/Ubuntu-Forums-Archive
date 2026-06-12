---
title: "Unable to install 10.04 on Thinkpad T42 and T40"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by hyggegnuen on 2010-05-21
Hey Ubuntu forum !

First let me tell you that I am new on using Linux, I installed my first distribution for a couple of years ago, but havent used it much, I am working with windows at a daily basis as an technician so this is my normal platform.

I am unable to install the new distribution on my two old laptops  Thinkpad T40 model 2373-4AF eller T42 model 2373-CTO.
I have tried with 2 separate CDs which is working, this I know because I have installed with them on my work laptop Lenovo T500 without having problems at all.

On the 2 old laptops I have tried to installe Ubuntu ver. 9.04 and then upgrade it afterwards to 10.04 online, this ends up with the same errors as when I use the CDs, and now I am in a deadend, and need some experts.

The error is something like this " The installer encountered an unrecoverable error. A desktop session  will now be run so that you may investigate the problem or try  installing again "

I have also tried with an external CD , this is the same issue, so the problem is with the hardware.
I read a thread about BIOS issues and compatibility mode, but are not aware of this being an issue with this old hardware, and there is no raid on the laptop, and the old distribution ver. 904 is running smoothly.

Please be assisting me to get this running on my outdated laptops, its great on my T500, but my boss wouldent appreciate to see my PC running with Linux on instead of Vista :( 

Be looking forward to hear from you.

Kind regards Thomas

---

### Post by mikewhatever on 2010-05-21
You should post more info about the older machines: CPU, RAM, graphics.  Does the desktop session actually start after the error?

---

### Post by OLDMANHOOK on 2010-05-21
I say always do a clean install Why would u want to install 9.04 when you want the new 10.04 If it was me 1st read a few pages of installs on this fourm, check out the hardware list download the iso burn a DVD at the slowest speed you can stand DON'T install run live 1st see what kind of problems you have READ Linux is not Windows, link in above post and if u are new to this OS do ONE Install at a TIME. ASK ASK, Someone will help you I know 10.04 works on the T40 Upgraded one last week only problem the fan seems to run too much and--





 the wireless don't work too good IF you are a windows tech YOU know about Updates breaking Good Systems . Good Luck.

---

### Post by yukonho on 2010-05-27
Just chiming in to say that I have the same problem on my T40. The live desktop session seems to work just fine after the error message, but I'm reluctant to try installing after seeing that message. What log files should I look at posting on here for help?

Details:
Thinkpad T40 (2373 series)
1.5 GHz Pentium M
512 MB ram, 40GB HDD
32MB ATI Radeon video card

---

### Post by eatmysticcyrice on 2010-06-07
So anyone? I want to do this too but don't know if it'll work. So BUMP!

---

### Post by CoreyS on 2010-06-09
Short response: It worked, but some pain.

Long response:
Tried upgrading Jaunty to Lucid through update manager (wubi install). Jaunty to Karmic worked, Lucid hung. Uninstalled through windows (XP Pro legit), then wubi install Lucid.

I had error messages too. Same problem as hyggegnuen, same machine as yukonho by the looks of it:
My machine:
T42 (2373-4YU) built December 2005
Pentium M 1.7 GHz?
? RAM
40Gb HDD
ATI graphics 32Mb? 15" screen (the one that is limited to 1024x768 only - :mad: grr)
ISO -> x86 desktop (32bit I guess) fast burned through DVD-burner on my tower.

Error message:
"The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again"

Then after that one seems to have disappeared:
VESA graphics error, booted in low-graphics mode. Downloaded updates, which seems to have worked. System works, although quite slow. Now that I can access wireless with this machine I think I will be dumping windows on this machine permanently. May speed it up without wubi.

I've found that Linux seems to be somewhat self-repairing. Maybe its the updating?
I've had issues crop up, I research the problem, come back a day later the problem has disappeared and never seen again.

This is my experimental machine. I have a custom tower with Koala installed, very happy with it. Not sure if I'm ready or willing to risk it yet.

--------
Kinda update:
Those errors are gone, but now I can't get the wireless to handshake with the base station, even though I had it working ten minutes ago. My iPhone connects fine, Windows, no problem. Damn this is annoying!:confused:

---

### Post by wyngrn on 2010-07-04
I have 10.04 installed on a T42. Seems to be mostly OK even though I got the message the poster saw. It started a desktop session and I installed from the icon it showed on the desktop.
Only issue I have is that swapping users seems to cause a hang that goes away if I suspend the laptop and then start again.
If anyone knows what causes this then I would be very grateful.

---

### Post by tgalati4 on 2010-07-04
Turn off Kernel Mode Setting (KMS) perhaps?

---

