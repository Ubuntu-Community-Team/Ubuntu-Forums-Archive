---
title: "After upgrading to unity 8 the desktop is unusable how to revert it ?"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2014-09-26
I have intall unity 8 since that my desktop is on classic mode.
So on the top bar there is only applications and Places fane.
And on the top right corner I se the user what login in to ubunutu but when I click on it 
open it , retart, shutdown ,none of the things there work.
I can I get back to my hold desktop ?
The only way to put off the computer is to plug of the electricity.
I am using ubunut 14.04.
I don't know if it has something to do with the user.
I can not launch ubuntu sotware center, but when I login as guest I can.
I have tried setsid rest-icons .. nothing worked

---

### Post by deadflowr on 2014-09-26
You have gnome-classic already?
Try retstarting X
```
sudo restart lightdm
```
this should bring you back to the login screen.
At the login screen, where the name and paasowrd box is, is an icon in the top right corner.Click on it and it should list all the available desktop sessions.
If you do indeed have another session, like gnome-fallback( or flashback), it will be listed. Try selecting one, and then login. See what happens then

Also how did you install the unity8 packages?
Currently, unity8 is a seperate desktop session on Ubuntu 14.04, and so you should still have normal unity (version 7.2 for me on 14.04)

---

### Post by hoboy on 2014-09-27
when I run sudo restart lightdm
I get the following error
restart: Unknown instance:

---

