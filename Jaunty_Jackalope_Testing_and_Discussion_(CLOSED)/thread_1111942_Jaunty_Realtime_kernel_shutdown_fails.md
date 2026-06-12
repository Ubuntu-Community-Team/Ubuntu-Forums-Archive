---
title: "Jaunty Realtime kernel shutdown fails"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by seanlano on 2009-03-31
I have recently installed the Jaunty Beta amd64 version onto my R61i Thinkpad. Everything works OK with the generic kernel, but I am having problems with the realtime kernel (2.6.28-3-rt). Whenever I restart or shutdown, the laptop hangs with a blinking cursor after the usplash goes away. By pressing Ctrl+Alt+F4 (or F5, I don't remember) and changing to another tty, the last thing listed is "System will now restart/shutdown", but it doesn't. I have to do a hard power-off, but even after this the LED on the Ethernet port is still on, which doesn't normally happen. I have re-installed the rt kernel via synaptic a few times, and while this made it more stable, it still will not shutdown. 

Any ideas?
Should I just file a bug report?

P.S. Also, when using JACK to play with audio programs, I cannot start the service with the "realtime" option enable, even though I am using the realtime kernel. ???

---

