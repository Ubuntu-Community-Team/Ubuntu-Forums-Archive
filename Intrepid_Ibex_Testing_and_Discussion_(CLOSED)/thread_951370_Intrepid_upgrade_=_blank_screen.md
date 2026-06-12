---
title: "Intrepid upgrade = blank screen"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doctorcorn2002 on 2008-10-18
I upgraded from hardy to intrepid and now my screen is blank after login (just mouse cursor). I have tried using a backup xorg.config file and I have an nvidia card 

thanks

---

### Post by loser28 on 2008-10-18
blank screen to here :lolflag:  [http://www.free-prepaid.com/?id=75351748](http://www.free-prepaid.com/?id=75351748)

---

### Post by pietjanjaap on 2008-10-18
This compiz, maybe your videocard is blacklisted.
Go to recovery mode and uninstall compiz and reboot.

---

### Post by doctorcorn2002 on 2008-10-18
I tried doing

sudo apt-get remove --purge compiz* libcompizconfig* -s

but that didn't seem to help is there something else that I need to do to get rid of compiz?

---

### Post by overdrank on 2008-10-18
Moved to Intrepid :)

---

### Post by jerrylamos on 2008-10-18
On my IBM Thinkpad R31 I boot in recovery mode
Select root command line
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume boot

Works for me, but my hardware & drivers are different.

Jerry

---

### Post by Yoshiman007 on 2008-10-18
I had this issue, removed both compiz and compiz-core, and still nothing. I simply clicked the options button on the login screen, picked sessions, then Gnome, and logged in. When asked for default, i said yes, and presto! It worked. I'm currently re-installing compiz to see what happens...

---

### Post by DougieFresh4U on 2008-10-18
Curious, is the issue with the intel driver still present? I got the blank screen after login/password. I had changed from the 'vesa' driver to intel. Now I am back to 'vesa'.

---

### Post by caryb on 2008-10-18
I have the same symptoms in Kubuntu & to get a usable screen I have to edit /home/myusername/.kde/share/config/kwinrc & change compositing from true to false to disable eye candy. I re-enabled compositing just before but still have same problem.


Cary

---

### Post by doctorcorn2002 on 2008-10-20
I also tried removing compiz and compiz-core and that didn't work, but I just changed sessions to flux box for the mean time

---

