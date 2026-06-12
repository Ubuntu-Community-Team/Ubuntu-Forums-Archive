---
title: "Problem in updates"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 013raptor on 2009-10-18
Today, when I was verificating the updates, a windows appeard and now i cant select some updates. How can i fix that?

[[IMG]http://i.imagehost.org/t/0922/Captura_de_tela-Gerenciador_de_atualiza_es.jpg[/IMG]]("http://i.imagehost.org/view/0922/Captura_de_tela-Gerenciador_de_atualiza_es") [[IMG]http://i.imagehost.org/t/0202/Captura_de_tela-update-manager.jpg[/IMG]]("http://i.imagehost.org/view/0202/Captura_de_tela-update-manager")

---

### Post by ELD on 2009-10-18
I really shouldn't of had to post this, there are important topics stuck to the top of the forum for a very good reason, try looking.

[http://ubuntuforums.org/showthread.php?t=1286309](http://ubuntuforums.org/showthread.php?t=1286309)

---

### Post by froggyswamp on 2009-10-18
In my experience it usually means not all packages have been updated in the repos so you just have to wait a few hours, maybe a day.

---

### Post by kansasnoob on 2009-10-18
Perhaps most problematic in this specific instance is the fact that this partial wants to remove rtkit. So I looked at the description of rtkit:

> RealtimeKit is a D-Bus system service that changes the
scheduling policy of user processes/threads to SCHED_RR
(i.e. realtime scheduling mode) on request. It is intended to
be used as a secure mechanism to allow real-time scheduling to
be used by normal user processes.

So, me thinks 'tis a good time to wait!

---

### Post by 013raptor on 2009-10-22
Fous days and the problem stills.

---

