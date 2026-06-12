---
title: "Ram utilization"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by bgvianyc on 2010-03-21
I noticed upon a fresh install of ubuntu 9.10 ram utilization was 250 MB when in gnome on startup, now upon startup its 450MB, how can I see what new processes are being launched upon startup and how can I disable them?

---

### Post by _h_ on 2010-03-21
You can add/modify/remove/disable startup applications from this section:

System -> Preferences -> Startup Applications

As a reminder, be careful on what you do in there, since disabling/removing specific applications could/will break things.

---

### Post by luttermann on 2010-03-21
From the menu you can choose:
*System > Administration > System Monitor*
in the Processes tab you can se what processes are running and how much ram they are using.
In *System > Preferences > Startup Applications* you can add/remove commands to be run at login.

WARNING: Some of these are crucial for the UI to work.

---

### Post by PPPilot on 2010-03-21
Open a terminal: Type: ```
top
```This will give you all you need to know about what is using what resources. The problem with System Monitor is that it uses resources itself and these are most often at or near the top of the list depending on how you sort. Top in terminal gives more and better information.

---

### Post by bgvianyc on 2010-03-21
How much ram does Ubuntu 9.10 w/ Gnome usually use upon startup? What is normal ram utilization range?

---

### Post by luttermann on 2010-03-22
my "clean" ubuntu 9.10 outputs this if i open a terminal and type in "free -m -t" right after login:
```

             total       used       free     shared    buffers     cached
Mem:           536        241        294          0         33        105
-/+ buffers/cache:        102        433
Swap:          368          0        368
Total:         904        241        662

```
and if I start it with only 94MB RAM it looks like this:
```

             total       used       free     shared    buffers     cached
Mem:            94         93          1          0          4         22
-/+ buffers/cache:         66         27
Swap:          368         56        312
Total:         463        149        314

```

But why so interested in mem usage?

---

