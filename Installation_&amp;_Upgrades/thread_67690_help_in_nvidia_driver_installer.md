---
title: "help in nvidia driver installer"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by rollercoaster on 2005-09-21
its says im running an X server and need to close it

what does it mean?

---

### Post by GOwin on 2005-09-21
you need to stop the gui first, log in to a terminal

sudo /etc/init.d/gdm stop
<do whatever you have to do here>
sudo /etc/init.d/gdm start

---

### Post by rollercoaster on 2005-09-21
whoa!!

its started installing but it says it cant find GCC or cc something (cant remember)

also it says that it needs to compile a kernel or DL one

their ftp sites dead

what should i do?

---

### Post by MrCheese on 2005-09-21
You should be able to install the Ubuntu nvidia package via Synaptic/apt rather than the NVidia nvidia package (if you see what I mean) which works just fine with Hoary, can't say for Breezy though.

---

### Post by rollercoaster on 2005-09-21
[QUOTE=MrCheese]You should be able to install the Ubuntu nvidia package via Synaptic/apt rather than the NVidia nvidia package (if you see what I mean) which works just fine with Hoary, can't say for Breezy though.[/QUOTE]
 hmm thanks anyway got it working now ^__^

---

### Post by persis on 2005-09-21
How do you install the nvidia drivers from the command line using apt/synaptic?

Thanks -

---

