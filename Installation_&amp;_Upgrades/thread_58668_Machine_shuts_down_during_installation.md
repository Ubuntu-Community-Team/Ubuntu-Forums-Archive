---
title: "Machine shuts down during installation"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by nkessler2000 on 2005-08-21
I've been trying to install Ubuntu on my machine, but I'm running into a problem. My computer shuts itself down during the installation. I have tried to install three times and each time the machine shuts itself down before the installation can complete. 

The first time I tried to install, it shut itself down while the installer was reading packages from the CD. Every subsequent time, it shuts itself down well into the installation, after the machine has rebooted, the packages have been installed, and it is at the point of "setting up" the packages. The last time it happened, it was doing something with the "font cache". 

I've never had stability problems with my machine, so I'm not sure what's going on here. I get no errors, just a sudden shutdown and power off. If anyone could give me some ideas as to what might be causing it, I would greatly appreaciate it. 

A few details about my macine

CPU: AMD Athlon XP 2400+
Motherboard: Asus A7N8X
Memory: 512 MB DDR 2100

If you need any more information let me know. Thanks in advance

---

### Post by adwait on 2005-08-21
Maybe an increase in temperature is causing the system to shut down?

---

### Post by nkessler2000 on 2005-08-21
[QUOTE=adwait]Maybe an increase in temperature is causing the system to shut down?[/QUOTE]

Maybe, but I can't imagine. Windows runs a-ok. Never a problem. The BIOS says my CPU temp is about 80 C which seems high, but according to some info I've found on the web, thats normal for an Athlon XP 2400+.

---

### Post by heimo on 2005-08-21
[QUOTE=nkessler2000]Maybe, but I can't imagine. Windows runs a-ok. Never a problem. The BIOS says my CPU temp is about 80 C which seems high, but according to some info I've found on the web, thats normal for an Athlon XP 2400+.[/QUOTE]

That seems high. I believe 85C is the max for that processor and if you get 80C without any particular load, you will be on the edge under load.

---

### Post by nkessler2000 on 2005-08-21
[QUOTE=heimo]That seems high. I believe 85C is the max for that processor and if you get 80C without any particular load, you will be on the edge under load.[/QUOTE]

I got my info here:
[http://www.heatsink-guide.com/content.php?content=maxtemp.shtml](http://www.heatsink-guide.com/content.php?content=maxtemp.shtml)
and here:
[http://users.erols.com/chare/elec.htm](http://users.erols.com/chare/elec.htm)

And like I said, Windows never crashes, never shuts down, never nothing, even under the heaviest of loads. 

Whatever the case may be, I don't think I'm overheating. And even if I was, why would the machine shut itself down only when I try to install Ubuntu and never any other time?

EDIT:
Okay, so I'm using this program called SpeedFan to monitor my CPU temp. It says that with no load (other than Windows) I'm at 65. If I give it a moderate load (consistant 60% CPU usage) it goes up to about 75, and if I give it near 100% it goes up to about 85. Hmmmm....

---

### Post by heimo on 2005-08-21
From the sources you linked:
 > 
Keep in mind that the onboard measurement facilities are often inaccurate and may report temperatures that are too low. This is especially the case with motherboards that use a thermal sensor below the CPU to "guess" the CPU temperature. The temperature values displayed by the BIOS have usually a correction value added, to compensate for this problem - but in some cases this correction value may be too low, or the sensor might not be in good contact with the CPU. [i]

This means: [/i]If the maximum allowed temperature for your CPU is 95°C, and your motherboard reports a CPU temperature of 90°C, then you are *not* on the safe side. 

And:
 ```
Athlon XP-2400+
(6-8-1 2.0GHz Thoroughbred)1.6V
(?V~?V)2.0V----40.8A59.3W65.3W85° C
``` 

I just rebooted. My desktop is 2600+ (Barton) and on 24/7 - under no particular load. Via based Epox motherboard, BIOS reports 47C for CPU and 36C for motherboard. 80C is high.


 >  EDIT:
Okay, so I'm using this program called SpeedFan to monitor my CPU temp. It says that with no load (other than Windows) I'm at 65. If I give it a moderate load (consistant 60% CPU usage) it goes up to about 75, but my system is still stable as ever. Hmmmm.... 

Those are much better and seem safe.

---

### Post by nkessler2000 on 2005-08-21
[QUOTE=heimo]From the sources you linked:
  

And:
 ```
Athlon XP-2400+
(6-8-1 2.0GHz Thoroughbred)1.6V
(?V~?V)2.0V----40.8A59.3W65.3W85° C
``` 

I just rebooted. My desktop is 2600+ (Barton) and on 24/7 - under no particular load. Via based Epox motherboard, BIOS reports 47C for CPU and 36C for motherboard. 80C is high.


  

Those are much better and seem safe.[/QUOTE]

I'm starting to think that CPU temp is the problem. I just wonder why I've never encountered any difficulty before. My CPU has a huge fan on it and everything, so I dunno whats wrong. I guess I'll look into how to bring that temperature down a notch or two. 

Thanks for your input

---

### Post by heimo on 2005-08-21
Could be. It's a bit on the high side - however I'm not 100% convinced. But that's our best bet so far. Better cooling can never hurt, so you'll win anyway and get longer life for your CPU.

I guess you could try - as a temporary workaround and to debug this problem - underclock your system (just for now) to see if this is really the reason. I would do that. Of course that's not too acceptable long term solution.

---

