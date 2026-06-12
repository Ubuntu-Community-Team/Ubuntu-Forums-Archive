---
title: "Frozen Desktop after upgrades"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by FunkyBluffMan on 2008-01-11
Hi,

I've just installed 7.10 and setup the package manager to find updates. It came back saying there was 187 updates to do. So it left it to download and install all the updates. I then rebooted the machine and when it loads up it gives me the login screen I then enter in username/password. It logs me in but all I get is my desktop with its icons the task panel at the top with the standard 3 icons "Apps",System etc. which if I click does nothing. the only thinng I have in the top left hand corner is the shutdown button. I dont have clocks or anything and it does not allow me to click on that to restart either.

how can I revert back to my previouos settings or how can I check to see whats causing the problem.

---

### Post by peabody on 2008-01-11
The last batch of updates seem to have some bad mojo for random people including me and others.  [This thread](http://ubuntuforums.org/showthread.php?t=662423) has some interesting, if completely useless speculation.

My recommendation is to try and Ctrl+Alt+f1 to a virtual console, login and add a user with "sudo adduser new_name".  See if you can login with that user.

---

### Post by FunkyBluffMan on 2008-01-11
I see I'm not alone. Are the Ubuntu team aware of it? Is so why cant they just remove the update from their system so that other new user dont get the update message.

I did try add a new user and log in as that user and it still did the same thing.

---

