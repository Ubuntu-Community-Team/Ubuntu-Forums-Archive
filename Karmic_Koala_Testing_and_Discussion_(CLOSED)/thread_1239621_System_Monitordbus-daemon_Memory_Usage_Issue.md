---
title: "System Monitor/dbus-daemon Memory Usage Issue"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by namd3r on 2009-08-13
Every time I open System Monitor, I always find at least one (of 2) CPUs at or near 100%.  Originally I thought it was a problem with my BOINC client, but I still saw the CPUs running higher than I thought they should be, even with no other programs running.  On top of that, the only way I can close the System Monitor is by doing a manual force quit from the button I keep on my panel.

I started running top in terminal to monitor the usage, and it seems every time gnome-system-monitor is started, the CPU% jumps significantly.  Also, the two top memory consumers become gnome-system-monitor and dbus-daemon.  As soon as I force quit system monitor, the two disappear and CPU usage goes back to normal.

Anyone else experiencing this problem or know what the problem is?

EDIT: Just realised I mis-named the post.  I'm not experiencing a memory usage issue, but a CPU usage issue.

---

### Post by psyke83 on 2009-08-13
Gnome System Monitor uses a lot of resources to render the various graphs (which is kind of silly, since it makes it useless for measuring CPU usage reliably). The bottleneck on your system may be your graphics card drivers.

---

### Post by namd3r on 2009-08-13
I wouldn't have thought it would take 100% of a CPU to render the graphs, though.  It also happens regardless of if the Resources tab is active.

---

### Post by wayne_cat on 2009-08-13
> **namd3r said:**
> I wouldn't have thought it would take 100% of a CPU to render the graphs, though.  It also happens regardless of if the Resources tab is active.

Still 100% if you set the Graph "Update interval in second" to 100?

---

### Post by psyke83 on 2009-08-13
While monitoring CPU usage, open a terminal and run:

```
$ pkill metacity
```

Does CPU usage return to normal? If so, you're suffering from [bug #389686]("https://bugs.launchpad.net/bugs/389686").

---

### Post by namd3r on 2009-08-13
pkill metacity doesn't seem to do anything.  Running killall metacity gives me a "no process found" response.

CPU usage remained the same after changing the graph update frequency.

It seems after updating my system, though, I am able to close system monitor without a force quit, which is nice.  So it's at least a mild improvement.  Obviously I'm not going to be running System Monitor 100% of the time, but using a laptop that frequently overheats when it is working too hard (Sony Vaio + summer weather - air conditioning), I do find myself using it to see what is using up my cycles.

---

### Post by wayne_cat on 2009-08-13
> **namd3r said:**
> pkill metacity doesn't seem to do anything.  Running killall metacity gives me a "no process found" response.

CPU usage remained the same after changing the graph update frequency.

It seems after updating my system, though, I am able to close system monitor without a force quit, which is nice.  So it's at least a mild improvement.  Obviously I'm not going to be running System Monitor 100% of the time, but using a laptop that frequently overheats when it is working too hard (Sony Vaio + summer weather - air conditioning), I do find myself using it to see what is using up my cycles.

did you restart Gnome/rebooted  after the updates?

---

### Post by namd3r on 2009-08-13
A restart didn't do anything related to this issue, besides not allowing me to close without force quitting (or killing from within system monitor), like before.

---

### Post by wayne_cat on 2009-08-13
> **namd3r said:**
> A restart didn't do anything related to this issue, besides not allowing me to close without force quitting (or killing from within system monitor), like before.

maybe you should file a bug report

---

