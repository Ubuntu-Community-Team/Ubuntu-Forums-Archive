---
title: "Login problem"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by owlfour on 2006-06-24
I've just managed to get an installation to work using the OEM option from the Alternate CD.

During the install it asked me for a password but **did not** ask for a username!  I thought this was strange at the time but I didn't want to stop it - I've lost count of how many times I've tried to get an install to complete.

So, now I've got a system installed but I can't login because I never got the cahnce to enter a username.  Anyone got any ideas what it may have used as a default username?

---

### Post by bscbrit on 2006-06-24
Start the computer and select recovery mode.  You can then create a new user using the 'adduser' command.  Type 'man adduser' on the command line for more information.  Once you have created a user, you can log in using that name and try to find out what happened.  Remember to make your new user name a member of the 'admin' group so that you can use 'sudo' to gain root privileges.

---

### Post by owlfour on 2006-06-24
Thanks for the hint!

In doing what you suggested I used vigr and found that the username 'oem' is a member of the admin group.

So the answer is: the default username of the oem install option is 'oem'!

---

### Post by bscbrit on 2006-06-25
Glad your problem is solved. See you around the forums...

---

