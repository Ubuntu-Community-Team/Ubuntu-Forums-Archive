---
title: "Remote control issue"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Gillingham on 2008-11-09
Hi

After upgrading to ibex I have found that in the 2.6.27-7-generic kernel I cannot use the remote control that came with my hauppauge hvr-1100 TV card.  The card it self works fine when controlled by the keyboard.

The remote does not however appear as an entry in /proc/bus/input/devices

However, I also have the 2.6.24.21-generic kernel available.  The remote does work using that.

Is there a way of getting the remote enabled in the 2.6.27 kernel?

---

### Post by Gillingham on 2008-11-17
Turns out I was missing a kernel module ir-kbd-i2c

---

### Post by olliraa on 2008-11-18
How did you solve the problem exactly (the missing module)? I have the same "not recognized at all" -problem with Nova-t 500, so I'm curious :)

---

### Post by Gillingham on 2008-11-18
To load the module I had to do:

sudo modprobe ir-kbd-i2c hauppauge=1

and to make sure it is loaded each time the computer is booted up.
I created a file called hauppauge-remote in /etc/modprobe.d/ which contains the line

options ir-kbd-i2c hauppauge=1

Hope this helps

---

