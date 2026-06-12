---
title: "Screen freezing all the time"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by AmpersUK on 2013-11-19
I have a problem with my screen freezing all the time and I have taken a lot of trouble trying to isolate the problem.

Here's what I have done and my surmising from the effort.

1. I loaded Windows 7 as a dual boot. 

[COLOR=#ff0000]Result:[/COLOR] Everything worked fine. I installed about ten programs, everything went without freezing and I could use the computer immediately after boot up.

[COLOR=#ff0000]Conclusion:[/COLOR] The hardware, although may not be compatible with Ubuntu, was certainly in full working order using Windows.

2. Loaded Ubuntu 12.04.

[COLOR=#ff0000]Result[/COLOR]: Immediately after bootup the machine refused to work for a few minutes. Then it froze for a few minutes every few minutes so a job that might take ten minutes would take 20-25 minutes.

[COLOR=#ff0000]Conclusion[/COLOR]: There may be a hardware problem between my computer and Ubuntu 12.04

3. Loaded Ubuntu 13.10.

[COLOR=#FF0000]Result[/COLOR]: Immediately after bootup the machine refused to work for a few minutes. Then it froze for a few minutes every few minutes so a job that might take ten minutes would take 20-25 minutes.

[COLOR=#FF0000]Conclusion[/COLOR]: There may be a hardware problem between my computer and Ubuntu 13.10

4. The same disk of 13.10 was loaded onto my wife's desktop as a new clean installation.

[COLOR=#ff0000]Result:[/COLOR] Immediately after bootup her machine worked perfectly without any problems.

[COLOR=#ff0000]Conclusion:[/COLOR] The disk with 13.10 on was not damaged.

The computer I am having a problem with is my Notebook which I use instead of a desktop. [COLOR=#696969]It is a 17" Samsung RF711 with 8GB RAM, 2 x 1GB hard drive.[/COLOR]

I have used Ubuntu on this machine for over a year now without problems. The above only reared its ugly head a month ago.

---

### Post by jellybaby on 2013-11-19
Did you try booting in recovery mode? There's a menu entry in the boot menu, just under "Ubuntu"; it is called "advanced options" or "extended options". If you select that, you can choose to boot in recovery mode. Maybe the option "repair broken packages" might help. Good luck!

---

### Post by VMC on 2013-11-20
It appears you have[COLOR=#4D4D4D][FONT=helvetica] "NVIDIA GeForce GT 540M w/ NVIDIA Optimus", for your video. Are you using [/FONT][/COLOR]*nouveau*[COLOR=#4D4D4D][FONT=helvetica] or nvidia drivers?
If unsure, from a terminal type '[/FONT][/COLOR]lsmod|grep nouveau'

---

