---
title: "Karmic vs. Lucid - System Monitor Screencaps..."
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-03-22
Just for reference - similar configs and apps loaded. 
 Curious, though, why does Lucid seem to be using a bit more RAM, and what's this 100% CPU all the time?

---

### Post by ElSlunko on 2010-03-22
What is your processor because it seems very busy in both installs if you're in an idle state.

Ooops just saw it in your sig. Is this idle?

---

### Post by alexmurray on 2010-03-22
Open the Processes tab and see which process is hogging all the CPU

---

### Post by emarkay on 2010-03-22
> **ElSlunko said:**
> What is your processor because it seems very busy in both installs if you're in an idle state.
Ooops just saw it in your sig. Is this idle?

Yea, this is the:
*[COLOR=Purple]2.8 G/2G RAM/ATI HD2600,512VRAM/SIS AC97 OB  Audio [/COLOR]*
You can see the blip, where I did the screen capture (after a 2 second delay), and I closed BOINC/SETI, but basically in idle state - recent reboot on both.

Right now, in this state (used for a bit), in Lucid, there are 50 processes running, the Processor is constantly at 100% when Idle, (Even after I closed BOINC) and I have 379Mb of RAM used. Nothing shows in the "%CPU" column except "Gnome System Monitor" at about "22" or so, so what else is using my CPU?  Even Conky says "92%".

Well, it's still Beta...  :)

---

### Post by Longinus00 on 2010-03-23
> **emarkay said:**
> Yea, this is the:
*[COLOR=Purple]2.8 G/2G RAM/ATI HD2600,512VRAM/SIS AC97 OB  Audio [/COLOR]*
You can see the blip, where I did the screen capture (after a 2 second delay), and I closed BOINC/SETI, but basically in idle state - recent reboot on both.

Right now, in this state (used for a bit), in Lucid, there are 50 processes running, the Processor is constantly at 100% when Idle, (Even after I closed BOINC) and I have 379Mb of RAM used. Nothing shows in the "%CPU" column except "Gnome System Monitor" at about "22" or so, so what else is using my CPU?  Even Conky says "92%".

Well, it's still Beta...  :)

System monitor only displays your own processes by default. This has been true since forever.

---

### Post by emarkay on 2010-03-23
Sow, FWIW, how does one see all of what are using the CPU resources?

---

### Post by RomeReactor on 2010-03-23
> **emarkay said:**
> Sow, FWIW, how does one see all of what are using the CPU resources?

In the 'View' menu, change it to "All Processes".

---

### Post by ricsi-pontaz on 2010-03-23
My notebook's (with only 512 MB) memory usage with Karmic is about 180-200 MB with the same applications where Lucid's usage is about 280-300 MB.

---

### Post by emarkay on 2010-03-25
Moving CPU use issue to this thread:
[http://ubuntuforums.org/showthread.php?t=1438746](http://ubuntuforums.org/showthread.php?t=1438746)

---

### Post by lavinog on 2010-03-27
The higher memory usage could be the ureadahead bug where trace memory isn't released after a profile.
A profile occurs during boot, after certain packages are updated.  Since lucid is getting package updates very frequently...it is possible that this is the case.

one way to tell is to look at /sys/kernel/debug/tracing/buffer_size_kb
it has been reporting 128000 when a trace is active, so you should see a 128M increase in memory usage.

---

### Post by lavinog on 2010-03-27
btw: system-monitor is not a good app to use when looking at cpu resources.
It is terribly inefficient at drawing graphs because it focuses on making pretty graphs and not usable ones.
The problem stems from using beizer curves to draw each point on each graph.  This doesn't make sense to do for the memory graph, because memory usage doesn't change rapid enough to need interpolation or graph smoothing.  Also using this for network usage is faulty because it is not an accurate representation of network usage.

---

### Post by zengeos on 2010-03-27
After first installation of 10.04b1 my CPU was almost always at full load.  After one of the updates a few days ago though, CPU usage has dropped dramatically, with around 10-20% usage on each core on average.

Interestingly enough, system monitor shows a higher memory usage now, though....even with that I only seem to use about 1/2 my available RAM.

---

