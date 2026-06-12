---
title: "vnc problem"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by superbob666 on 2007-01-06
hi guys

i have installed vncserver on edgy, i can connect with vncviewer localhost:1...but i don't see any desktop just a black screen..i even have tried connecting with another pc on the lan, but same results..

so if some one can help or point me in the rite direction


thanks

---

### Post by superbob666 on 2007-01-07
i have tried tightvncserver and it works with it, just wondering y it is not working with realvnc, if anybody knows ??

---

### Post by superbob666 on 2007-01-07
looks like realvnc is running /etc/X11/Xsession and when i change /etc/vnc.conf to point to ~/.vnc/xstartup it works fine :confused:

---

### Post by Asos_Illusionist on 2007-01-16
> looks like realvnc is running /etc/X11/Xsession and when i change /etc/vnc.conf to point to ~/.vnc/xstartup it works fine
That worked for me but a bit difficult..

I needed to install vnc4server, run it once then kill it (vnc4server -kill :1), remove it (apt-get remove vnc4server) and then install vncserver (apt-get install vncserver), run it once then kill it (vncserver -kill :1) then nanoed the vnc.conf and "add" the ~/.vnc/xstartup script.. but..
there is always a but..
it starts twm to me.. (damn) and i need to start another session of my kde enviroment.. any help..??

p.s. sorry'bout my lagy english.. greece here!

---

