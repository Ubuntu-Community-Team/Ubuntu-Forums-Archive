---
title: "Enable  spca5xx module (how?) for webcam"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by mock_alien on 2006-11-26
Hi Everyone!

A few weeks ago i followed a guide to enable the spca5xx driver for my webcam (phillips sp700nc). I know it worked, but now i can't seem to find it.
I have looked and searched but to no avail.](*,) 

What i can remember is that only a simple command was given to get to a promt where i could enable the module and have it installed.
(as support for  spca5xx is already in the kernel)

I would really appreaciate if someone can remeber the commands[s].
(it was something with modules...)

---

### Post by mock_alien on 2006-11-26
Edgy Eft 6.10

1) System- Administration- Software Sources
check Community maintaned (universe)


2) sudo apt-get install module-assistant
sudo module-assistant
PREPARE
SELECT
select module spca5xx
and
GET
BUILD
INSTALL


found it...

now how do i get to setup the camera? (adjust brightness et.c.?)

---

