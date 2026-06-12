---
title: "How to fix Skype startup permanently?"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-11-05
I have Ubuntu 11.10 on an AMD/64 system.

I found the hint how to start Skype, but needs to be started from the command line:

LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu/ /usr/bin/skype

How can I fix that permanently?

bye

Ronald

---

### Post by ELMIT on 2011-11-09
Any ideas?

---

### Post by mastablasta on 2011-11-10
make a short script with this command and make it executable. then make a launcher for it in your unity bar or desktop...
 
someone will drop in and tell you how.
 
but it's really simple you create a file something like this:
 
```

[SIZE=2][FONT=LiberationMono][SIZE=2][FONT=LiberationMono]#!/bin/bash[/FONT][/SIZE]
[SIZE=2][FONT=LiberationMono]LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu/ /usr/bin/skype[/FONT][/SIZE]
[/FONT][/SIZE]
```
 
and then you make that file executable with rightclicking on it.
 
 
edit: ah here are the instructions. just replace the command with your command you use: 
 
[http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux](http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux)

---

