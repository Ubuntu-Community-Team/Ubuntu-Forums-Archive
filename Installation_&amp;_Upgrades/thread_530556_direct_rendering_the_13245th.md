---
title: "direct rendering the 13245th"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by XDigital on 2007-08-20
Hi,
I know there is loads of information and threads about this topic and I tried most of the suggestions - but fail.
System: Ubuntu Feisty Fawn 7.04 on AMD 1.8 GHz with NVidia 6600 GT

The problem raised the first time, when I tried to install compiz together with beryl. Because compiz didn't start correctly (and I tried more than 1000 times to get this stuff running) I deinstalled it using synaptic. After this action I tried to compile my OpenGL glut code and recieved this message the first time:
```
freeglut (/home/........): Unable to create direct context rendering for window 'Test'
This may hurt performance.
```
Wandering through the internet I found no solution to solve this. During the weekend the error message mature to the following:
```
XIO:  fatal IO error 14 (Bad address) on X server ":0.0"
      after 13478 requests (13478 known processed) with 0 events remaining.
```
Questionmarks grew... Again wandering through the internet no suggested code snipplet could solve this.
And now for the fun stuff, I found in /var/log/syslog the sweet message:
```
gdm_slave_xioerror_handler
```

I fear all these help cries from my computer have somthing to do with 
```
 glxinfo | grep direct
direct rendering: No
```

Any clues? Any help? Do I have to format c:? 42?
Regards
XDigital

---

