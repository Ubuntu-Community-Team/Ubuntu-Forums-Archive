---
title: "Error on disc Cd checking or install"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by punkydog on 2007-08-15
I am trying to install using a burnt CD from the downloaded ISO.
after I boot from it on a athlon 1900 system, if I select check the disc or install or nothing I eventually get an error message.

/bin//sh: can't access tty; job control turned off
(initramfs)

I have been unable to see any mention of this on the forums.

---

### Post by Waves77 on 2007-08-15
Answers:
[http://ubuntuforums.org/showthread.php?p=3155966]("http://ubuntuforums.org/showthread.php?p=3155966")
[http://ubuntuforums.org/showthread.php?t=415041]("http://ubuntuforums.org/showthread.php?t=415041&highlight=tty&page=3")

For me what worked is:

1)  Before choosing install from cd, press F6 (more options) and add **break=top** to the kernel line.

2)  After boot you'll get the same error. Do:
$ modprobe piix
$ exit

It'll boot fine now (at least it did for me). For some reason before loading the desktop environment, it got stuck but continued to load after moving/click the mouse and pressing enter. (could be my dual monitor setup screwing up something).

HTH

---

### Post by Waves77 on 2007-08-15
For some weird reason this worked for me only once ](*,)

Downloading 6.10 right now...

---

