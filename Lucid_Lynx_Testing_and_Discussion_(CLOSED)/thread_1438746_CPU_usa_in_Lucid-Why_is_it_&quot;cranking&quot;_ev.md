---
title: "CPU usa in Lucid-Why is it &quot;cranking&quot; even when Idle - Facts please."
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-25
I know it depends on what you have loaded as apps and what type of machine you have, but I, and a few others have noticed much more CPU use on average when compared to similar configurations in either Lucid or Karmic.

Why would a CPU be anything but maybe a periodic 5% blip every few seconds (for polling) when the PC is not in use - no screen saver, nor system monitor - OK maybe 5% and 25% blips if networked, but still, an average 80% and most times about 100%???

(Please don't use tell me it has anything to do with Plymouth!)

---

### Post by 23meg on 2010-03-25
[QUOTE=emarkay]Why would a CPU be anything but maybe a periodic 5% blip every few seconds (for polling) when the PC is not in use - no screen saver, nor system monitor - OK maybe 5% and 25% blips if networked, but still, an average 80% and most times about 100%???[/QUOTE]

You're in a better position to tell that than anyone else, since it's happening on your computer. Start a terminal, run *top*, and see which process is hogging the CPU.

---

### Post by Kenny_Larsen on 2010-03-25
Are you running connected(or have tried to connect to) any Samba shares, it's caused me some issues!

Kenny

---

### Post by philinux on 2010-03-25
> **emarkay said:**
> I know it depends on what you have loaded as apps and what type of machine you have, but I, and a few others have noticed much more CPU use on average when compared to similar configurations in either Lucid or Karmic.

Why would a CPU be anything but maybe a periodic 5% blip every few seconds (for polling) when the PC is not in use - no screen saver, nor system monitor - OK maybe 5% and 25% blips if networked, but still, an average 80% and most times about 100%???

(Please don't use tell me it has anything to do with Plymouth!)

Ok I rebooted lucid, waited for bootchart to finish and then fired up firefox. Here is top. It's idling away in low values nicely. I did have a java glitch earlier that maxed out the cpu. Restarting FF fixed that.

---

### Post by cariboo on 2010-03-25
I just checked with system monitor, some of what your are seeing is the resources that system monitor uses itself, if you click the processes tab and scroll down to gnome-system-monitor, it shows that on my system the process uses 4% of the cpu and 5.2 Mib of ram.

---

### Post by psyke83 on 2010-03-25
> **cariboo907 said:**
> I just checked with system monitor, some of what your are seeing is the resources that system monitor uses itself, if you click the processes tab and scroll down to gnome-system-monitor, it shows that on my system the process uses 4% of the cpu and 5.2 Mib of ram.

Yes... GNOME System Monitor renders a lot of graphics with cairo, which can cause high GPU/CPU usage. I consider it more of a graphics driver performance tester rather than a real system monitor.

---

### Post by emarkay on 2010-03-25
Well I found that BOINC does not close when you close it's window, but I ended its process, and still have about 50% use.

While that looks like a lot for idle I guess it's "OK" being that System Monitor" and Firefox are up.

"X" seems to be the biggest culprit, and when the FGLRX (ATI) driver is finished, I guess that will take up a bit more...

Any other comments?

Thanks!

---

### Post by NightwishFan on 2010-03-25
On my machine system monitor does not use much CPU like it did in the hardy days.

---

### Post by joske on 2010-03-25
idle lucid system: system-monitor shows up on top when sorting on CPU. It's still the same, total waste of time.

---

### Post by Longinus00 on 2010-03-26
> **emarkay said:**
> Well I found that BOINC does not close when you close it's window, but I ended its process, and still have about 50% use.

While that looks like a lot for idle I guess it's "OK" being that System Monitor" and Firefox are up.

"X" seems to be the biggest culprit, and when the FGLRX (ATI) driver is finished, I guess that will take up a bit more...

Any other comments?

Thanks!

Why don't you close system monitor?

---

### Post by umberstark on 2010-03-26
I don't see any CPU spikes, but what I do see is my CPU (Amilo  LI1718 laptop) idling at 58 degrees Celsius, when in windows it's way less, and even more so when I undervolt it using RMClock. Before I installed Lucid, Windows was idling happily at 44 degrees Celsius.

That's  quite a significant difference, and for me an unacceptable one. :-(

---

### Post by Abandon on 2010-03-26
> **emarkay said:**
> I know it depends on what you have loaded as apps and what type of machine you have, but I, and a few others have noticed much more CPU use on average when compared to similar configurations in either Lucid or Karmic.


I use conky and whatch the top 5 processes 'on the fly' and the big issue here is gwibber:

gwibber-service (more than one sometimes)
beam.smp

Because it asks a lot of cpu it also makes the core tempature a lot higher.

---

### Post by mikeyphi on 2010-03-26
For me it's a Samba problem. When I try to connect to my other computer (no problems in the past) system monitor shows gvfsd-smb running at 97-100% even after I've cancelled the 'open' request. I have to use 'end process' to get my cpu back!

---

### Post by tekstr1der on 2010-03-26
> **mikeyphi said:**
> For me it's a Samba problem. When I try to connect to my other computer (no problems in the past) system monitor shows gvfsd-smb running at 97-100% even after I've cancelled the 'open' request. I have to use 'end process' to get my cpu back!

Check these:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024)
and
[https://bugs.edge.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764](https://bugs.edge.launchpad.net/ubuntu/lucid/+source/gvfs/+bug/538764)

---

### Post by jim_24601 on 2010-03-26
> **emarkay said:**
> Well I found that BOINC does not close when you close it's window, but I ended its process, and still have about 50% use.

While that looks like a lot for idle I guess it's "OK" being that System Monitor" and Firefox are up.

"X" seems to be the biggest culprit, and when the FGLRX (ATI) driver is finished, I guess that will take up a bit more...

Any other comments?

Thanks!

If you're suffering from Xorg CPU churn with the ati drivers and the new Lucid kernels, try disabling kernel mode setting: see [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

