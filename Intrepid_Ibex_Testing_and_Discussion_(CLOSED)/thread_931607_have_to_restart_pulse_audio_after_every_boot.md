---
title: "have to restart pulse audio after every boot"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-09-27
pulseaudio -k; sleep 4; pulseaudio -vv

kill and restart it then it is ok.

---

### Post by BwackNinja on 2008-09-27
what does ```
ps ax | grep pulseaudio
``` tell you before you restart pulseaudio?

---

### Post by sdowney717 on 2008-09-27
before  killing
scott@scott-desktop:~$ ps ax | grep pulseaudio
 7515 ?        Sl     0:00 /usr/bin/pulseaudio --log-target=syslog
 7524 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 7927 pts/0    S+     0:00 grep pulseaudio

after killing
scott@scott-desktop:~$ ps ax | grep pulseaudio
 7932 pts/0    Sl+    0:00 pulseaudio -vv
 7936 pts/0    S+     0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 7966 pts/1    S+     0:00 grep pulseaudio
scott@scott-desktop:~$

---

### Post by BwackNinja on 2008-09-27
If I'm not mistaken, that would be the pulseaudio running as a per-session daemon called from sessions. Install padevchooser if you haven't already, and see if it has any output devices in pavucontrol before you restart pulseaudio. If it doesn't, that would mean that something was probably using sound through alsa before pulseaudio came into the picture, and with the way pulseaudio does things, it would not be able to connect while alsa is otherwise being used. Depending on the load order, it could possibly be the login sound doing that.

---

### Post by psyke83 on 2008-09-27
> **BwackNinja said:**
> If I'm not mistaken, that would be the pulseaudio running as a per-session daemon called from sessions. Install padevchooser if you haven't already, and see if it has any output devices in pavucontrol before you restart pulseaudio. If it doesn't, that would mean that something was probably using sound through alsa before pulseaudio came into the picture, and with the way pulseaudio does things, it would not be able to connect while alsa is otherwise being used. Depending on the load order, it could possibly be the login sound doing that.

Exactly. One possible culprit is MPD.

---

### Post by sdowney717 on 2008-09-27
Also, I noticed the login sound comes on loud and then towards the end, sound level tapers off in a rather unusual manner.

---

### Post by BwackNinja on 2008-09-28
Try disabling login sound. If that fixes it, then the problem is pretty bad because it would be widespread. If not, more digging :D

Sidenote: Its funny how you find out more about how something works when it doesn't.

---

