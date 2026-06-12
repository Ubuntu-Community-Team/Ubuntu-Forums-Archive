---
title: "How to disable PulseAudio?"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-08-31
I am a bit tired of PA and I would like to give ALSA a try. Also, I would like to know if my Microphone not working is caused by ALSA or PA. Anyway, I tried to kill and stop PA but it always comes back:


```

andresmh@karmicx300:~$ sudo /etc/init.d/pulseaudio stop
[sudo] password for andresmh: 
 * PulseAudio configured for per-user sessions
andresmh@karmicx300:~$ sudo /etc/init.d/pulseaudio ^C
andresmh@karmicx300:~$ ps -ef | grep pulseaudio
andresmh  9640     1  0 13:44 ?        00:00:00 /usr/bin/pulseaudio --start
andresmh  9643  9640  0 13:44 ?        00:00:00 /usr/lib/pulseaudio/pulse/gconf-helper
andresmh 13936  9851  0 15:57 pts/0    00:00:00 grep pulseaudio
andresmh@karmicx300:~$
andresmh@karmicx300:~$ killall pulseaudio
andresmh@karmicx300:~$ ps -ef | grep pulseaudio
andresmh 14445  9851  0 16:19 pts/0    00:00:00 grep pulseaudio
andresmh@karmicx300:~$ ps -ef | grep pulseaudio
andresmh 14447  9851  0 16:19 pts/0    00:00:00 grep pulseaudio
andresmh@karmicx300:~$ ps -ef | grep pulseaudio
andresmh 14450  9732  1 16:19 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
andresmh 14452 14450 14 16:19 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
andresmh 14453  9651  0 16:19 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
andresmh 14458  9851  0 16:19 pts/0    00:00:00 grep pulseaudio

```

---

### Post by philcamlin on 2009-08-31
all you need to know is in here :popcorn:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by andresmh on 2009-08-31
Thanks. I should have done a search before posting too. I found this 1-week old discussion: [http://ubuntuforums.org/showthread.php?t=1245531&highlight=disable+pulseaudio](http://ubuntuforums.org/showthread.php?t=1245531&highlight=disable+pulseaudio)

---

### Post by 23meg on 2009-08-31
[http://ubuntuforums.org/showpost.php?p=7844892&postcount=172](http://ubuntuforums.org/showpost.php?p=7844892&postcount=172)

---

