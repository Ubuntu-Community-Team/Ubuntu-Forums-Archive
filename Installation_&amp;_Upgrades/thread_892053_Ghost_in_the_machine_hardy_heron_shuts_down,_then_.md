---
title: "Ghost in the machine: hardy heron shuts down, then revives."
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by khentiamentiu on 2008-08-16
Since I installed Hardy Heron, my system won't die, or rather, it appears to power down, then comes back to life. Using the shutdown button from the gdm panel, or running "shutdown -P now" from the command line, produces the normal shutdown sequence, all the way to shutting down the fans. However, a couple of seconds later, the system restarts, as if I had turned it on. 

I thought at first that this was some coincidental failure of the hardware, but then I booted the system from three distros (Fedora 9, Puppy Linux 4 and Knoppix 5.3.1), and all three distros successfully put a stake in my system's heart - once the system powered down, no unwelcome revival followed. 

FYI, I am running a generic Athlon 64-bit 3500+ system, with the 2.6.24-19-generic kernel. 

Can anyone tell me what's going on here?

---

### Post by jualin on 2008-08-16
Give this command a try > sudo shutdown -h now And tells us if it shuts down the computer

---

### Post by khentiamentiu on 2008-08-16
> **jualin said:**
> Give this command a try  And tells us if it shuts down the computer
No, "sudo shutdown -h now" doesn't shut down the machine. I get the same behavior as with "sudo shutdown -P now".

---

### Post by khentiamentiu on 2008-08-16
Okay, I'm calling this an annoyingly intermittent hardware problem. I just disconnected and reconnected the wiring to my power switch, and the problem went away. Looks like a short. Sorry for the misdirection.

---

### Post by jualin on 2008-08-16
Glad to hear that it was a hardware problem, and that everything is fixed now. Greetings from Miami, FL, USA

---

### Post by khentiamentiu on 2008-08-17
> **jualin said:**
> Glad to hear that it was a hardware problem, and that everything is fixed now. Greetings from Miami, FL, USA

Greetings from the San Francisco Bay. And the problem is back. However, I can't rule out hardware at this point, and will refrain from any further postings until I determine the cause. Meanwhile, if anyone sees the same problem - system shuts down to the point of turning off the fans, then restarts - I would like to hear about it.

---

### Post by jualin on 2008-08-17
Can you try a different power supply? They cost about $30 - $40 in the US. And they are pretty easy to install.

---

### Post by khentiamentiu on 2008-08-18
> **jualin said:**
> Can you try a different power supply? They cost about $30 - $40 in the US. And they are pretty easy to install.

Yup. The annoying thing is, I just replaced the damn thing 7 months ago, about 1 month beyond it's warranty. But it's worth a try. Thanks!

---

### Post by jualin on 2008-08-18
Maybe you can get one try it and if that's not the problem return it. Check the return policy on the store first though, :)

---

