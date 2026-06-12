---
title: "Software Center, Update manager and other applications crash before opening."
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by Stusb on 2010-07-25
Hello,

I just installed Ubuntu 9.10 on my X41T IBM ThinkPad Table and ran into a few problems off the bat.

i installed 9.10 using wubi of a 8 gb slim USB, it is dual booting along side win 7 ultimate.

the installation went well (smoother than anticipated with Win 7 already hoarding space)

ok so after the install i start setting up the system the the way i like it but right away i try to hit up the software center and find that it begins to start up then promptly closes/crashes. 

i have tried sudo apt-get update - sudo apt-get upgrade with no luck. i also tried reinstalling all python programs in synaptic as per a forum thread i found earlier today.

i have tried to reinstall software center threw synaptic to no availe.

i would like fix this issue with out going to the hassle of reinstalling the OS.

Thank you all very much. :-)

---

### Post by partloer on 2010-07-25
Hi Stusb,

I would first try and update your system to see if this is a bug that has been fixed.  Try System->Administration->Update Manager and try and install any updates.

Second you could try and install software manually through the terminal and see if that helps you install software that you need now while you try and fix this problem.

Let me know how this goes.

---

### Post by theozzlives on 2010-07-25
Hey! 9.10 has been known for its bugs out of the box. If you can install the updates its fine. I'd recommend 10.04, it's much more stable and it's an LTS version.

---

### Post by Stusb on 2010-07-26
I love 9.10, runs like a champ on my other desktops. 

other thing i have noticed is that the movie player opens for a brief second before closing.

something for sure is tide to them all not working and i would love to figure it out.

i have been using synaptic to reinstall just about everything i can think of but still to no avail. this can not be a normal problem with 9.10 out of box. i have found very few posts on the subjects of software center failing to open.

is there away to put the live CD in and do a general repair???


Edit: i just tried to run in terminal, here is what resulted

:~$ gksudo software-center
Traceback (most recent call last):  File "/usr/bin/software-center", line 28, in <module>
    gobject.threads_init()
AttributeError: 'module' object has no attribute 'threads_init'


Edit #2: just tried to do a remove and re install of software center, the screen shot below shows the results.

---

### Post by Stusb on 2010-07-27
Bump:p

---

