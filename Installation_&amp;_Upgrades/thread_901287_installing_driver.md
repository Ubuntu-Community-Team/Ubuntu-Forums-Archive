---
title: "installing driver"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Achilles124 on 2008-08-26
I am having difficulty installing a driver manually in Ubuntu.

This is what the README has to say about it:
" > Introduction
============

  odvr is a user-space driver for Olympus digital voice recorders that do not
support USB Mass Storage. There is no GUI at this time, and functionality is
limited, but basic download and listing capabilities are implemented.

Building
========

  There is no configure script at this time. You'll need libusb and libsndfile,
and their associated development headers. To build, run:

$ make odvr

  A static x86 linux binary is included as odvr.x86.

  odvr will require access to the user-space USB interface. It is recommended
to place "41-odvr.rules" into "/etc/udev/rules.d" or setup your own udev rules
rather than running odvr as root. After changing udev rules, don't forget to
run "udevcontrol reload_rules" and to replugin your DVR.

So, I type $ make odvr in the terminal according to the instructions and then I get the following error message:
"make: *** No rule to make target `odvr'.  Stop." 

What to do now?

---

### Post by Punkoff on 2008-08-26
You need unpack driver package and cd into it's directory and only then, use make odvr

---

### Post by Achilles124 on 2008-08-26
What directory do I have to place it in?

---

### Post by Achilles124 on 2008-08-26
Ah, I read it wrongly. I have done what you said and it worked. thank you.

Greetz,

---

### Post by Achilles124 on 2008-08-26
Nope, it didn't work as planned. it gave an error. How do I undo what was done?

---

