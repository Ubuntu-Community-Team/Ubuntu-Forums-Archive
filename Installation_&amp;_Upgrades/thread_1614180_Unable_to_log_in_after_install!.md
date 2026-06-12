---
title: "Unable to log in after install!"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by kajman on 2010-11-05
Hi!

After installing  (fresh install) xubuntu 10.10 I cannot log in.
Every time I type the password it seems that the X server restarts and i get back to login screen again and again. I was able to login from console (ctrl+alt+f1) without a problem.

I need my system back and running ASAP!

I tried to install xubuntu 10.4 again, but I get the same "error".

Maybe it's worth noting, that everytime I install next version of linux I use the same /home partition as before, same login, and the same password everytime. I just format the / partition and install new system there.

I was hoping to download some updates, but I was unable to connect to internet succesfully from console (enough issues to make another post).

So I'd like to ask for your help, and hope for a solution fast! I need my system sometime around 18 today!

Thanks in advance,
kajman

---

### Post by mörgæs on 2010-11-05
In /home, there are a lot of directories whose name begins with a dot, meaning that they are hidden. They are configuration files.

If you keep /home while installing, best is to move the configuration files to a USB drive before installing.

---

### Post by RamananUbu on 2011-02-02
login from console  to tty1 : ctrl+alt+f1
now do
 sudo apt-get install  ubuntu-desktop

now login, this should solve ur problem



chers :)

---

