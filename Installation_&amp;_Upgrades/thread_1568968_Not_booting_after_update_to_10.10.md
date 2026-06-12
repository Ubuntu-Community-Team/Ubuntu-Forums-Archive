---
title: "Not booting after update to 10.10"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by cloaknite on 2010-09-06
Hi there, I had Ubuntu 10.04 installed on my machine and I updated to 10.10. When the pc rebooted the following appears:
Ubuntu Maverick (Developer Branch) "computer name here" tty1

And it asks me for my username and password, after that is justs stays there, I've tried the startx command but with no luck :(
Can someone help me please?
Thanks!

---

### Post by davosem on 2010-09-06
Hi:
I also have exactly the same problem. I did the same as you did. I am also hoping that an expert can tell us how to solve it.

---

### Post by garvinrick4 on 2010-09-06
Does the terminal say anything when you type in startx?

---

### Post by cloaknite on 2010-09-06
Yes, it says something like "can't start xserver", I can only say for shure when I return home :D

---

### Post by garvinrick4 on 2010-09-06
does it say cannot start because already running?
Seems like quite a few had this problem today, is fixable.
Let me know when you get home to computer.

[INDENT]Fatal server error:
Server is already active for display 0...[/INDENT]

---

### Post by mörgæs on 2010-09-06
Best is to keep these discussions here:

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by davosem on 2010-09-06
I tried also the command startx and it gave the following message in the screen.
 (EE) Failed to load/usr/lib/xorg/extra-modules/nvidia_drv.so
 (EE) Failed to load module "nvidia"(loader failed, 7)
 (EE) no drivers available
Fatal server error

ddxSigGiveUp:flosig log giving up
xinit: No such a file or directory (errno2) unable to conect to x server
xinit no such process (errno 3): server error.

I omit a few other parts of the message.
 How can we move this thread to the site suggested above?
Thanks

---

### Post by cloaknite on 2010-09-06
I've booted the system again and the same error appears...I took some photos of the error :) btw, I remember now that I did the partial upgrade first, in the update manager, rebooted with no problems and then I did the full upgrade...

---

### Post by garvinrick4 on 2010-09-06
Here is thread about your driver problems in 10.10

[http://ubuntuforums.org/showthread.php?t=1549195](http://ubuntuforums.org/showthread.php?t=1549195)

---

