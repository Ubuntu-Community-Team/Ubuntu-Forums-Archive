---
title: "Can't boot after upgrade"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by howardcheng on 2006-06-14
I just upgraded my desktop system from Badger to Dapper.  Now the booting process hangs when it tries to start PCMCIA services.  I do not have any PCMCIA slots on my desktop, why would it try to do that?

I haven't had time to fix this yet, but when I get time I will boot with a CD and remove the PCMCIA stuff from the startup sequence.

Has anyone else noticed this before?

---

### Post by johnc4510 on 2006-06-14
Mine doesn't hang but it does give me a failure at that point, and always has

---

### Post by deadgobby on 2006-06-14
[QUOTE=johnc4510]Mine doesn't hang but it does give me a failure at that point, and always has[/QUOTE]
 I got it too and it is nothing really if you do not have any PCMCIA cards in the slot. It is just a default setting and if it does bother you. This is how you can cure that.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It really does not take that long to do and it will skip the PCMCIA slot test at boot up. 
Gobby
Thanks for the posting on that i3dmaster.

---

### Post by howardcheng on 2006-06-14
[QUOTE=deadgobby]I got it too and it is nothing really if you do not have any PCMCIA cards in the slot. It is just a default setting and if it does bother you. This is how you can cure that.
[/QUOTE]

It certainly bothers me because the whole machine hangs and the only thing I can do is to do a hard reset.  I managed to get in now (by using a rescue disk and turning off PCMCIA manually) but now lots of things don't work (lots of programs with wrong permissions, things partially installed, etc.).  I have a feeling that something went horribly wrong with the upgrade, so I'll try installing from scratch. :sad:

---

