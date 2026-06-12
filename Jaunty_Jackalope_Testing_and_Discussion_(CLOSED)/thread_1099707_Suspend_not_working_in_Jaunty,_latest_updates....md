---
title: "Suspend not working in Jaunty, latest updates..."
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-03-18
Is anyone else having any issues suspending or hibernating?  Just after the latest rounds of massive updates, it appears my system just returns to a log-in prompt as if the screensaver had been on.  This happens whether I use the Fn keys on my laptop or the menu options for suspend or hibernate.

I have a Lenovo T61...

---

### Post by zerted on 2009-03-18
This has always randomly happened to me.  After resuming from suspend, I'd have to log back in as if I had just restarted the computer (Lenovo X61 Tablet).  All my open programs/windows from when I suspended were gone.  It doesn't happen often, but is annoying when it does.

---

### Post by dBuster on 2009-03-18
I have a compaq cq60 and have no issues with suspend or hibernate.  Actually found out that if I click on the battery icon it gives me a menu to suspend or hibernate also!  In the past I used just the power icon...  

Yeah, but no issues with my laptop after all the recent updates.  Works as it is supposed to.  Might be something limited to the Lenovo models?

---

### Post by scaine on 2009-03-18
All working here too - Toshiba U-400.  I noticed on another thread that there's some suspend/resume issues if you've enabled UXA on Jaunty.

It's a manual process to do so though, so if you don't know what I'm talking about, then this clearly isn't the issue.

---

### Post by Therion on 2009-03-18
I have no Internet connectivity when coming out of suspension and, about half the time, my whole system locks up tight (no response from KB or mouse) forcing a hard-reset.  Ouch.

---

### Post by nystire on 2009-03-19
This problem appears to kill my sound (Toshiba P105-S9337). After suspend, everything else works (haven't ever tried bluetooth or the fingerprint reader though, so I may be wrong about the everything :) )

---

### Post by mariner09 on 2009-03-19
I looked at the pm-suspend.log file and noticed that the shutdown of PulseAudio generated a return code of 1 which seemed to halt the operation.  I tried killing PulseAudio 1st and that resulted in a system log-out as opposed to a suspend.

Something's not proper with ACPI support and the suspend scripts.  Maybe it's PulseAudio at the root.

---

### Post by onyxrev on 2009-03-23
Could you guys experiencing the 'dumping to screensaver' style suspend problem contribute to my bug report?

Thanks!

[https://bugs.launchpad.net/bugs/344989](https://bugs.launchpad.net/bugs/344989)

---

### Post by mariner09 on 2009-03-23
I just added my pm-suspend.log to your bug report.  It shows what I indicated previously that PulseAudio seems to be the root of my issues.

Maybe I can add a line to kill pulseaudio to my suspend script to get around the issue...

---

### Post by mariner09 on 2009-03-23
I did find that if I manually kill pulseaudio, I can suspend and hibernate, however, after resume, my ThinkPad keys for suspend and hibernate no longer work.  Progress at any rate...

---

### Post by Gnuus on 2009-04-01
> **dBuster said:**
> I have a compaq cq60 and have no issues with suspend or hibernate.  Actually found out that if I click on the battery icon it gives me a menu to suspend or hibernate also!  In the past I used just the power icon...  

Yeah, but no issues with my laptop after all the recent updates.  Works as it is supposed to.  Might be something limited to the Lenovo models?

I have a Compaq CQ50 and suspend has never worked for me, actually it's impopssible to resume from suspend. I have to shut down and start up.

---

### Post by Gnuus on 2009-04-16
> **Gnuus said:**
> I have a Compaq CQ50 and suspend has never worked for me, actually it's impopssible to resume from suspend. I have to shut down and start up.

And still suspend does not work.............

---

### Post by -jay- on 2009-04-16
same here i can not suspend at all even logging off & clicking suspend does not do anything im using the 64bit version

---

### Post by snorbens on 2009-04-17
I cannot suspend or hibernate on my Toshiba Satellite L350..

The screen just goes blank and I have to turn off and on again using the power button. 
 
Frustrating, although hibernate is not important, I would like to be able to suspend, as it would save the laptop heating up, and of course save power.

---

### Post by whtvr on 2009-04-20
same thing happens to me, after I wake up my laptop from suspend I'm back to login screen... I'm on Thinkpad X200s

btw. is there a ticket open for this bug on Lunchpad?

---

### Post by studavis on 2009-04-21
I had same problem with Toshiba Portege R200, if I switch off Wireless and remove my Bluetooth SD card, it will suspend/resume almost all of the time.

---

