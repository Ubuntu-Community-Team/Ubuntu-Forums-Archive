---
title: "Never Promted for Login"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by Gir_^ on 2006-07-25
When i install the 6.06 i am never prompted with a choice of a "login" it simply asks for a "password" for the "new user"....

Then when i load up the desktop, it asks for user name and password... well since i don't have a user name... it goes nowhere. I try using "root" but it always says "you can't login as root, NOOB"... needless to say i am frustrated to the point of mental exhaustion.

I watched a video of someone else installing 6.06 and it went straight to letting them choose a login name... why am i never prompted with mine... why is the installer broken...

Answers anyone?

---

### Post by philippe_carlo on 2006-07-25
Weird things sometimes happen. Don't worry, this is fixable.

(1) boot into recovery mode
(2) type 'adduser' at the command
(3) give up real name, login, password and if desired some more info
(4) reboot and log in as the new user

Before doing this, you may want to check wether the user does not already exist by typing 'users', giving a list of all users on the system.

---

