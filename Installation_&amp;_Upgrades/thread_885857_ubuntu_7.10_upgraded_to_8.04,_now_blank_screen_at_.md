---
title: "ubuntu 7.10 upgraded to 8.04, now blank screen at login"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by shortridge11 on 2008-08-10
i have a personal file server that i had 7.10 on.  I decided today that 8.04 was probably debugged enough to warrant an upgrade.  I upgraded, and now when i log in there's just a green screen.  It's the same color as the login screen, but nothing happens.  I can ssh into it, but i can't get the gui up and running.  I don't know if it makes a difference, but i was using ubuntu studios when i upgraded.

---

### Post by shortridge11 on 2008-08-10
when i type

sudo dpkg --configure -a

it says too many errors, and nothing really happens.  Now, instead of the recovery kernels being 7.10 kernels, they're 8.04, and there are 3 instead of 2.  I want to get to the login screen, but each kernel just gets me a blank screen.

---

### Post by shortridge11 on 2008-08-10
i was messing around with keystrokes at the blank screen, when i pressed ctrl alt F1.  This let me log in in the terminal, and everything worked from there

---

