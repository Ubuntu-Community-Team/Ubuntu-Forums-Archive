---
title: "Server x not found?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by miketowninc on 2007-06-06
I installed ubuntustudio and after restarting it says something with server x problems. i Think it says it could not be found, it asks if you run the debuging mode. but thats all. once i say no it goes to the terminal (sudo) but i cant get any further! do i need to explain the problem more?

---

### Post by miketowninc on 2007-06-06
Failed to start the X server. It is likely that it is not setup correctly.


is the correct message

---

### Post by NeoLithium on 2007-06-06
Shouldn't be too bad.  Once you get to the terminal window, type
```

sudo dpkg-reconfigure xserver-xorg

```

Answer all the questions that you know the answer to, the rest, leave as defaults and you should be able to get it up and running.  Since the first run of Xorg didn't work, I think it's pretty pointless to back up the xorg.conf....

---

### Post by miketowninc on 2007-06-06
after i do every question it just goes back to ubuntu@ubuntu.... what else should i do

---

### Post by NeoLithium on 2007-06-06
try running the command

startx

Hopefully it will load your XServer and you'll be back in a gui! :)

---

### Post by miketowninc on 2007-06-06
Fatal error no screens found XIO: Fatal IO error 104(connection reset by peer)on x server"o.o" 
after 0 requesto( 0 known processed with 0 events remaining


weird
can you still help?

---

### Post by miketowninc on 2007-06-07
any other idea?

---

