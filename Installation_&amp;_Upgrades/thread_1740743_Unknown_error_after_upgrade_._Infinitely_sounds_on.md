---
title: "Unknown error after upgrade . Infinitely sounds one sequence..."
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by slinzex on 2011-04-27
After yesterday's upgrade from 10.04 to 10.10 I've noticed that several times my laptop (Dell Vostro 1720) stills not responding. 
If I was listening music, or speaking at skype, in random moment, it stacks infinitely playing one sequence of last sound. 
For example is now playing one song : "I'm gonna see you after rain..." . So in one moment, the system is playing the last sequence of words " you after , you after  , you after  , you after ....... infinitely. I can't do anything ( ctrl+alt+F3, ctrl+alt+del.. ) .
I have to press ON button for 5sec to hard shutdown . 

This happened more than 8 times after upgrade yesterday night. 


uname -a : 
Linux watt-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux


How can I detect what happens?

---

### Post by dino99 on 2011-04-27
watch the log files: system admin logviewer, and .xsession-errors (/home, ctrl+h to unhide it)

---

### Post by slinzex on 2011-04-27
could you suggest witch ones I have to look ?

for example is this normal?
Apr 27 19:10:30 xxxx-laptop pulseaudio[1830]: ratelimit.c: 21 events suppressed

---

### Post by kostkon on 2011-04-27
> **slinzex said:**
> could you suggest witch ones I have to look ?

for example is this normal?
Apr 27 19:10:30 xxxx-laptop pulseaudio[1830]: ratelimit.c: 21 events suppressed
Yes, that's a warning from pulseaudio; nothing serious.

---

### Post by slinzex on 2011-04-27
I didn't found any solution for this issue . 
I know that it happens randomly. Not depending on what I'm watching, listening, doing... 

How to detect what cause the problem? 
In which log file I have to look?

---

