---
title: "Gui Login fails in 10.04 but TTY login works."
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by Eycks on 2010-07-11
I installed 10.04 on my pc. I also have 9.08 and XP installed. Both work. The 10.04 gui login screen displays and asks for the password.  I enter the password. The screen goes blank but after a few seconds the gui login box re appears and again asks for a login.   I rebooted into the TTY, created a new user, checked the new user was in in /etc/passwd and that I could get into the new user's account.  When I rebooted into the gui the new user was there and I entered the password but again I just got back to the gui login window. The pc I am using is at least 5 years old. I have tried startx and I do get the gui background but no controls are displayed.  I am using 32 bit 10.04.  Using the TTY I have uploaded all the current fixes.

---

### Post by alexshr on 2010-07-11
I once had the similar problem, then the problem was due to compiz. The solution that worked me was to remove compiz & ubuntu-desktop from the system and re-install ubuntu-desktop only. 

Hope this helps you.

---

### Post by Eycks on 2010-07-12
I tried what you suggested but it did not work. I used aptitude from the command line "--with-recommends" which I think reinstalled compiz.  I made sure that compiz was removed. The behaviour is the same as before. Any other ideas?

---

### Post by avi007tokade on 2011-02-03
I know this is old thread but I also faced this same problem and I solved that issue with following steps.

1)  Press *Ctrl + alt + F2 *
2)  Login  in termainal with same details
3)   *# sudo /etc/init.d/gdm stop*
4)  There are some corrupt pakages in ubuntu-desktop and giving this issue. 
    * # sudo apt-get install ubuntu-desktop *
     and I found Evolution mail client 3 package corrupted and after that command packages got   reinstalled and I am successfully able to login now.

I hope someone get this info useful. ):P

---

