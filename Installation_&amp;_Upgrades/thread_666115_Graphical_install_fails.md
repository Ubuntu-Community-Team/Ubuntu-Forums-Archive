---
title: "Graphical install fails"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by macm10 on 2008-01-13
hello i downloaded Ubuntu 7.10 and when i boot from the disk the Ubuntu logo with orange bar comes up. then after that a series of messages in text come up all of them saying ok. however when the graphical interface starts up it keeps crashing and after a certain amount of times it gives me a message saying to try again in two minutes, and after two minutes the same thing happens. this never used to happen with previous versions of Ubuntu in the past. i am on an alien ware area 51m laptop with an ati radon x1800

---

### Post by nexus2xl on 2008-01-13
When it fails:

1. Ctrl+Alt+F2 (to get to the terminal)
2. sudo killall gdm (to stop gdm from starting in again)
3. sudo dpkg-reconfigure xserver-xorg (enter in all the information correctly and use graphics driver "ati")
4. sudo startx (to see if it works). 
5. If it did then Ctrl+Alt+Backspace then... sudo gdm

post the xserver error if it fails

---

### Post by macm10 on 2008-01-13
Fatal server error:
no screens found 
XIO:     fatal IO error 104 (Connection reset by peer) on X server ":0.0"
            after 0 requests (0 known processed) with 0 events remaining.



any ideas?

---

### Post by macm10 on 2008-01-14
bump...anyone?

---

### Post by macm10 on 2008-01-16
bump again....:-|

---

### Post by sowelie on 2008-01-16
I am searching around for you, but at the moment it's not looking good:

[http://ubuntuforums.org/showthread.php?t=298257]("http://ubuntuforums.org/showthread.php?t=298257")

EDIT: Did you try booting into "safe graphical mode"?  Also, I can't remember which F key it is, but there's one where you can force a resolution.  Try forcing something like 800x600.  I'm sure once it's installed you can get the right drivers installed and you should be good to go.

---

### Post by macm10 on 2008-01-16
thanks, i will try that

---

### Post by Partyboi2 on 2008-01-16
F4 at the main menu, will give you the option to choose resolutions :)

---

