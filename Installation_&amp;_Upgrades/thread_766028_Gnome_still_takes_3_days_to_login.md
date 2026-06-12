---
title: "Gnome still takes 3 days to login"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by blackvd on 2008-04-24
I was pretty ecstatic for this update, as many I was hoping it to solve my one big bug. System boots fine and fast up to gdm but once I login it takes a good 20 to 30 seconds to load my desktop. Not sure where to start looking with this problem, I know there used to be a really long post regarding this issue since it started with Gutsy. If anyone has any clue on how to solve this or know what information I need to post in order to get this solved I would be very grateful. Thanks.

---

### Post by blackvd on 2008-04-28
Am I really the only one with this problem? Or is there a post I'm not finding regarding this issue?

---

### Post by robsic on 2008-04-29
I'm having a similar problem I think, see my earlier post here: [http://ubuntuforums.org/showthread.php?t=772002](http://ubuntuforums.org/showthread.php?t=772002)
Yet to find a solution though, and now I'm considering to move to Debian Etch instead...

---

### Post by Dale61 on 2008-04-30
If we are to believe the heading, then yes, you probably are the only person with this problem.

Misleading titles will get you nowhere here, so next time, please be more truthful when starting a thread.

---

### Post by olejorgen on 2008-04-30
Uh.. isn't that just gnome loading? 20-30 seconds is maybe a little long, but then again.. it's gnome. Try something else. xfce, ion, wmii, .. if you want something faster. Try to dig in some logs to see if something is hanging

---

### Post by IamAcoconut on 2008-04-30
> **olejorgen said:**
> Uh.. isn't that just gnome loading? 20-30 seconds is maybe a little long, but then again.. it's gnome. Try something else. xfce, ion, wmii, .. if you want something faster. Try to dig in some logs to see if something is hanging
That's rather not what he meant. I dunno about Hardy, but with Gutsy LiveCD it takes shorter time. Yet after the system is installed it's hanging there 20-30secs just doing nothing. After that desktop, and panels _start_ to load.

---

### Post by blackvd on 2008-05-02
OK fine I won't exaggerate in the title didn't know it was such a big deal. Anyways there was a problem with gnome taking 20 to 30 seconds for a lot of people to login. However I haven't been able to locate that thread anymore and just thought I might start a new one. So the delay is from gdm to actually complete load up of gnome desktop. I would love to provide more information so I can attempt to solve this but I'm just not sure where to start. So any suggestions would be great or a link to an appropriate thread thats already been started if it exist. Thanks.

---

### Post by NightwishFan on 2008-05-02
Is the system still fast after it all loads? Or just generically slow? Try disabling some system services perhaps. Also perhaps give kde a try its great.

May the force be with you.

---

### Post by Pumalite on 2008-05-02
Remove 'quiet splash' from menu.lst and take a look where is taking his time,

---

### Post by blackvd on 2008-05-02
System runs great after it finally loads. I was thinking it was a compiz issue but i disable it and reboot and still had the problem. I'll mess with services and see if that helps.


update: Nothing unusual running in services.
        Any other ideas?

---

### Post by Pumalite on 2008-05-02
Good luck.

---

### Post by NightwishFan on 2008-05-02
Also, post the results of these commands here:
```
free -m
```
```
top
```
```
uptime
```
For top I only want the multitude of stuff at the top of it, and the first process on the list of them. Press q once while in top to stop it from moving so you can copy. use the code /code tags (they need to be surrounded by brackets). It should look like this:
```
free -m
             total       used       free     shared    buffers     cached
Mem:           883        864         19          0         27        544
-/+ buffers/cache:        291        592
Swap:         2588          0       2588
```
```
Tasks: 124 total,   2 running, 122 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.3%us,  1.9%sy,  0.0%ni, 86.5%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    904276k total,   886748k used,    17528k free,    28688k buffers
Swap:  2650684k total,        0k used,  2650684k free,   559260k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8997 virgil    20   0  120m  39m  19m S    8  4.5   1:01.53 ktorrent
```
```
uptime
 19:56:52 up  1:23,  1 user,  load average: 0.09, 0.21, 0.21
```

---

### Post by blackvd on 2008-05-02
```
             total       used       free     shared    buffers     cached
Mem:          1009        995         14          0          8        400
-/+ buffers/cache:        586        423
Swap:            0          0          0

```

```
 6786 blackvd   20   0  342m 166m  27m S   19 16.5  19:32.20 firefox                 
 5820 root      20   0 93372  55m  11m S    4  5.5  25:41.45 Xorg                    
 6680 blackvd   20   0  173m  63m  18m S    2  6.3   4:42.99 exaile                  
 6452 blackvd   20   0 75132  36m  11m S    2  3.7  20:12.87 compiz.real 
```

```
17:31:44 up  6:12,  2 users,  load average: 1.22, 1.07, 0.90
```

---

### Post by NightwishFan on 2008-05-02
You load seems a lot higher than mine but overall everything is normal I do not understand why it would take so long to log in. Perhaps do give kubuntu hardy a try. It is somewhat lighter on ram than gnome (despite popular belief), and make sure you do not use the kde4 remix if you decide to give it a try.

If you like gnome, perhaps give xfce a shot. Also you can try to disable some unneeded services and startup programs, that may increase boot time.

At the worst check your install cd for errors, and see if perhaps thats the reason for the slowdowns. (happened to me once)

---

### Post by blackvd on 2008-05-02
Thanks for the help. Perhaps when I feel up to backing everything up I might just do a fresh install.

---

