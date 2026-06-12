---
title: "X11VNC black screen"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by maxxer on 2012-06-15
Hi.
I've a setup with two xen VM running both ubuntu 10.04LTS.
The have gdm+xfce installed, and using xen's VNC capabilities I can connect the the physical machine and see the login screen.
I also use x11vnc, for personal needs, on the same server. I used to connect without problems, but since yesterday and apparently no change, when I connect to the x11vnc port I just get the login cursor (the black X) and a black screen with a white bar on top! 
if I try to connect back to the xen vnc I correctly see the xfce screen.

What can it be?
I tried several x11vnc commands with the same result! 
attaching here the vnc log of
```
/usr/bin/x11vnc  -noxrecord -noxfixes -noxdamage -forever -loop -bg -display :0  -v -o /tmp/vnc.log -ncache 10
```

thanks

---

### Post by krunge on 2012-09-08
Which VNC viewer are you using?

Try it without the -ncache 10 and see if it works.

---

### Post by maxxer on 2012-09-11
thanks, works partially. if I issue the command manually it works, if I put it at the bottom of /etc/gdm/Init/Default I still get a black screen

---

### Post by maxxer on 2012-09-21
I've probably found the error: adding a & to the command!
Being gdm init, the process will never reach "exit 0" since x11vnc wasn't returning the control back...

---

### Post by krunge on 2012-09-22
I see. You have "-bg" which should put it in the background (i.e. without need for '&'), but your -loop usage precludes it going into the background (the -bg is ignored.)

I don't think /etc/gdm/Init/Default usage needs the -loop feature (since you have -forever), what do you think?

---

### Post by maxxer on 2012-09-25
> **krunge said:**
> I see. You have "-bg" which should put it in the background (i.e. without need for '&'), but your -loop usage precludes it going into the background (the -bg is ignored.)

I don't think /etc/gdm/Init/Default usage needs the -loop feature (since you have -forever), what do you think?

Yeah, your arguments are correct, since I was getting mad I made a mess with options :)
Since I need it "forever", -bg is irrelevant and -loop as well.

---

