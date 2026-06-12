---
title: "telnet access?"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by praxis22 on 2009-10-27
I had telnet access working under jaunty but under karmic it's no go. Anyone got a quick guide?

Note, I know telnet is insecure, and all about the Elysium that is ssh, etc. but I'm not interested. I want to get telnet working nothing else.

xubuntu, karmic

EDIT: work now, you need a keyboard, mouse and screen to be connected to get a telnet prompt. I presume this is something to do with power management in the hald replacement. So it goes :)

---

### Post by nukie77 on 2009-10-27
Why not just add it with the "sudo apt-get install telnetd" command?

---

### Post by praxis22 on 2009-10-27
I had it working via the openBSD inetd daemon, (I think) so I did already have telnet installed, then I upgraded...

But thanks for your answer I shall again drag the box out from under my desk, (where it runs headless) and try again. Ah the joys up upgrading :)

---

### Post by praxis22 on 2009-10-27
Actually it does appear to be working when plugged into a screen and keyboard besides me, but not when it's headless underneath the desk. More interestingly it appears that when running headless the power button doesn't work, (it's an old IBM thinkcenter) so it could be that hald/dbus is not coming up properly. I'll have to have a fiddle. Annoying.](*,)

---

### Post by praxis22 on 2009-10-27
Actually it looks like it's something to do with the hald replacement, if I leave a keyboard and mouse connected, it still doesn't work, if I pull one of the cables off my twin head desktop and then reboot, it all comes up, and I can telnet in as before. 

Odd.

---

