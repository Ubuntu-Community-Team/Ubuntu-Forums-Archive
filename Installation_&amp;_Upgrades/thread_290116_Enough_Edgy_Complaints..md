---
title: "Enough Edgy Complaints."
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by jgcamp99 on 2006-10-31
OK, the deed is done, upgrade with a clean install from Dapper to Edgy.

I'm having the hardest time reconciling the System Monitor issue I am experiencing. First off, this is an AMD Athlon XP Barton K7 3200+ with 256 MB AGP ATi Radeon 9600XT, 1.5 GB PC3200, 2 hdd's, 52X cdrom and a 16X DVD +/- RW.

Symptoms, I placed the applet for System Monitor on the bottom panel. The small window indicates a wild fluctuation from 8-100 % cpu utilization at any given moment in time. Activity is web surfing and posting this thread, so I've gotta beleive this isn't an intensive task, especially when it's an on-line word processor like task.

More symptoms, I open the System Monitor and watch the processes during this whole issue of the wildly fluctuating cpu usage. All processes are monitored, so I gotta believe that is accurately being displayed and captured.

I have really only 3 processes that indicate cpu usage. XOrg, gnome system monitor and multi-load applet-2. These indicate cpu % around 2-14% for any given process, with Xorg being predominantly around 2%, and the other two hitting around 7-14% at the same time, so I'm really looking at only around +/- 20%. I think that number is a little high and should be tweaked for a lower cpu usage for the activity I'm putting it thru. Maybe Edgy requires more cpu usage than Dapper ?

Anyone else get this ?, reported it ?, is there a fix on the way ?

I do notice my cpu temps up from 36*C (under Dapper) to closer to 40*C (under Edgy), but this could be the differential between what Dapper idled along ve what Edgy is now idling @ in terms of the cpu usage ? It's noticable, not anything that I would say would damage the computer in terms of increased heat, but being definitely noticable, maybe my power bill goes up a little ? Outside of this little issue, everything about Edgy seems to be quite stable.

---

### Post by skymt on 2006-10-31
The main thing using your CPU in that situation is the two system monitors you're running. Every two seconds, they have to read a bunch of information about each process, process it, and display it, and that's taking up to 14% of your CPU. Close them to free up your CPU.

---

### Post by jgcamp99 on 2006-10-31
So it wouldn't matter if I throttled it back to read at the maximum time interval allowed ? But it still doesn't explain why the poll window when opened shows that these aren't spiking like they do when I mouse over the bottom panel ?

---

### Post by skymt on 2006-10-31
Just ignore the monitors. You're inventing a problem that doesn't exist, and they're helping you. I only recommend using a system monitor to solve problems that are detectable in other ways (sluggish response, etc). I consider an always-on system monitor in the panel a huge waste of resources, and (as you noticed) they are often inaccurate.

Bottom line: there is no problem, so don't worry. :)

---

### Post by jgcamp99 on 2006-10-31
> **skymt said:**
> Just ignore the monitors. You're inventing a problem that doesn't exist, and they're helping you. I only recommend using a system monitor to solve problems that are detectable in other ways (sluggish response, etc). I consider an always-on system monitor in the panel a huge waste of resources, and (as you noticed) they are often inaccurate.

Bottom line: there is no problem, so don't worry. :)

I've always found those system monitors to be very indicative of problems. In Windows, when this system idles, even with system monitoring tools, it's not uncommon to see as low as 4 % cpu usage. At best Edgy indicates 11 % and predominantly upper teens to upper 20 % range ? Surges and spikes to 30-50, even as much as 100 % ? That's ridiculously high for idle for a stable OS and it's processes by anyone's standards. Right now Firefox.bin is @ 0 % cpu usage, so the browser is virtually asleep.

---

### Post by skymt on 2006-11-01
You said yourself that the monitors are the ones using the CPU. Close them, and you get an idle usage between 2-5%.

By the way, don't trust the panel CPU monitor. I've found the most generally reliable system monitor is the "top" command.

---

### Post by jgcamp99 on 2006-11-01
> **skymt said:**
> You said yourself that the monitors are the ones using the CPU. Close them, and you get an idle usage between 2-5%.

By the way, don't trust the panel CPU monitor. I've found the most generally reliable system monitor is the "top" command.

I'm starting to come around on this, maybe the system monitor that I'm using isn't the most efficient application.

Anyway, Edgy is almost back to where I had Dapper. Outside of the slightly higher activity and temp increase, Edgy is pretty darned good. I'm pleased with it. Dapper, good, Edgy, just as good with extra's !

Maybe I didn't get all of the softwares in the repository for Dapper, even checked for new ones, but Edgy repositories seem to have a few more titles ?

---

### Post by McLoud on 2006-11-02
I don't think it should use that much cpu, I have mine enabled all the time and it isn't usual to see it on 2% CPU on a Athlon FX 2.6. Maybe your video drivers are without acceleration and drawing the thing on screen is eating your cpu?

---

