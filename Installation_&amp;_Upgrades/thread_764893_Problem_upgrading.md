---
title: "Problem upgrading"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by abba567 on 2008-04-24
I decided to upgrade to the new version today, it failed half way through, when i rebooted it came up with lots of things to fix which i did. I've now tried to log in and it accepts user name and password but after that i just get a blank start up screen. Still fairly new to ubuntu so sorry for the rubbish details

Thanks

Tony

---

### Post by PmDematagoda on 2008-04-24
Did you try starting up the GNOME session(I'm assuming that you're using Ubuntu) in Fail Safe mode? You can do that by clicking Sessions on the GDM login screen and selecting Gnome Fail Safe.

---

### Post by abba567 on 2008-04-24
Thanks have managed to get into fail safe now what can i do?

---

### Post by abba567 on 2008-04-24
Ok that wasnt very well worded, Im now in fail safe mode, how can i fix it so i can use the normal mode?

Thanks for all your help

---

### Post by ibutho on 2008-04-24
Can you describe a bit more about what you mean by "blank start up screen". When you see this screen and do CTRL-ALT-F1, do you see a terminal?

---

### Post by PmDematagoda on 2008-04-24
Can you try making a new user and then try logging in using that account, to see if the problem is related to user configurations or something in the system itself.

---

### Post by abba567 on 2008-04-24
Well the blank sceen is a screen that is just that yellow/cream colour with nothing else on it!

---

### Post by abba567 on 2008-04-24
Have tried a new user and i get the same problems.

If i do Ctrl + Alt + Del on the blank screen nothing happens

---

### Post by abba567 on 2008-04-24
Ctrl + Alt + F1 Does bring up the terminal

---

### Post by jmar71n on 2008-04-24
I having exactly the same problem. 

The login screen comes up -->  login  -->  Blank orange/brown screen with a mouse curser

Ctrl+Alt+F1-F6 works and runs as it should.

Also i was using the release candidate which worked perfectly until i did a upgrade 3 days ago, so the problem is some where in the upgrades from the release candidate to the final release. 

I now have a fresh install of 8.04 from the final release CD and getting the same problems.


I have been using Ubuntu exclusively for the last 3 years, so fairly experienced.

---

### Post by abba567 on 2008-04-24
Bump, please help its driving me mad!

---

### Post by PmDematagoda on 2008-04-25
> **abba567 said:**
> Well the blank sceen is a screen that is just that yellow/cream colour with nothing else on it!

I got that too, just start GNOME in Fail Safe and then open Nautilus and show hidden files, then delete the .gnome folders, then log out and try the normal GNOME session again.

---

