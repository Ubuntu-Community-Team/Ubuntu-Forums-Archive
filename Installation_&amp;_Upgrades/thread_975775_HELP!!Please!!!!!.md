---
title: "HELP!!Please!!!!!"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by bookworm69 on 2008-11-08
I am having problems every time i try to download anything on my laptop, i keep trying to update my computer but it never lets me. It keeps saying this....**An Error has occurred**
THE FOLLOWING DETAILS ARE PROVIDED:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I am no computer wiz and so i have no idea what that means...:(
Also every time i try to add new applications to my computer it says that and im really confused! if you could help me that would be great!
Thanks!

---

### Post by Patrick793 on 2008-11-08
Open a terminal and do this:
```
sudo dpkg --configure -a
```

---

### Post by jobix on 2008-11-08
What is means is that the upgrade process was somehow interrupted and the repository information on your computer is probably in a broken state. By doing what Patrick793 suggested above, you will repair the repository information on your machine, which should then let the upgrade process succeed.

---

### Post by bookworm69 on 2008-11-08
I feel so stupid for asking this but how do i open a terminal...

---

### Post by tvtech on 2008-11-08
[COLOR="Blue"]got to Applications>Accessories>terminal[/COLOR]got to Applications>Accessories>terminal

don't feel stupid this place is for asking questions and often the easy ones are overlooked.

---

### Post by bookworm69 on 2008-11-08
Thanks! 
ok still having problems so i put in the command however its asking for my
password and im trying to type it in but nothing is showing up the black curser thing keeps blinking and im trying to type it in but its not letting me...please help...

---

### Post by hansdown on 2008-11-08
Hi bookworm69.

Your password won't show as you type it in.  Just enter it and hit enter.

---

### Post by tvtech on 2008-11-08
Ubuntu is built fairly secure by default so things like passwords never show up visually.  that way the average joe walking by and thinking of steeling your laptop will think twice since you've got a password that they can't see.

---

### Post by bookworm69 on 2008-11-08
Never mind I figured it out THANKS!!!

---

