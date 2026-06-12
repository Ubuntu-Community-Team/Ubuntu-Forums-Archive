---
title: "Package system issue"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by nick2k11 on 2011-10-25
When I try to update, I get this error. I am completely lost on what to do.

Screenshot:
imgur [dot] com/8aLUL

---

### Post by Frogs Hair on 2011-10-25
The screen-shot link doesn't work . ;)

---

### Post by nick2k11 on 2011-10-25
Here you go: [http://imgur.com/8aLUL](http://imgur.com/8aLUL)

---

### Post by Utew on 2011-10-25
Have you tried running *apt-get install -f     *  in a terminal window? or [I]sudo apt-get install -f

[/I]to try to fix the broken packages?

---

### Post by nick2k11 on 2011-10-25
Yep. It gave me this:

```
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by critin on 2011-10-25
Is Software Center running by any chance?

---

### Post by moorhead98 on 2011-10-25
I'm having similar problems as well. What I ran was sudo dpkg --configure -a
But do not do that right away, it could be wrong (I was prompted by the system to use it after a reboot)

---

### Post by Utew on 2011-10-25
Yeah, make sure you don't have a package manager (Update Manager, Software Center, Synaptic) open while you are running that command in the Terminal....

---

### Post by nick2k11 on 2011-10-25
Got it to work. I ran the command Utew suggested as root and did what it needed to do.

---

