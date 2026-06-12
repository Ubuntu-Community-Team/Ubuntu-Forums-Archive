---
title: "cpuinfo_cur_freq different from cpuinfo"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by aouie on 2006-06-13
Powernowd appears to be working when I check /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq. But /proc/cpuinfo is always reporting the full speed CPU frequency. Before upgrading to Dapper the the varying frequencies was reflected in cpuinfo (and hence on the cpu frequency sensor that I put on my KDE panel). Is cpuinfo not getting the right values? Is cpuinfo_cur_freq not getting applied in reality?
Is there any other program that I can use to check the actual operating frequency of my Athlon?
In gnome I believe the scaling CPU freq applet shows the scaling_cur_freq and not the info in /prco/cpuinfo. If cpuinfo is not getting updated properly, then is there a way to display cpuinfo_cur_freq or scaling_cur_freq in the cpu_freq sensor?
Sincerely,
Aouie

---

### Post by weekend warrior on 2006-07-08
Any resolution on this apparent conflict? I'm experiencing the same issue on a Thinkpad T23 with a PIII M that scales at 1132MHz and 732MHz. 

Gkrellm and the Gnome cpu freq scaling applet show Powernowd working on demand. Gkrellm shows the cpu consistently under 732 unless doing something intensive when it pops up to 1132 then back down again, just as it should. 

However Kinfo and /proc/cpuinfo show the cpu maxed out at 1132. I only noticed this after upgrading to some Dapper upgrade and security packages a few days ago (though perhaps I've just missed it up to now). 

I've also noticed that services in Kcontrol shows Powernowd as not running whereas Bootup Manager shows it as active.I don't get any Powernowd errors on startup or shutdown. 

I still have Breezy on this laptop too and there are no conflicting values for Powernowd which eliminates any possible hardware/bios issues. 

So same question, is the /proc/cpuinfo in Dapper incorrect? Is the info reported in KDE services also incorrect?

---

### Post by ltmon on 2006-07-15
I have the same problem with a fresh install of Kubuntu 6.06 on a Intel Core Duo laptop.

The CPU's seem to be scaling properly according to /sys/devices, but /proc/cpuinfo always reports the maximum frequency, so it's hard to monitor what's actually going on.

L.

---

### Post by Curious_Squid on 2006-07-29
I have the same problem on my Duo Samsung Q35, and my battery life would suggest that cpuinfo is giving an accurate reading...

---

